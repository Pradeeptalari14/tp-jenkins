pipeline {
    agent { label "docker" }

    options {
        buildDiscarder(logRotator(numToKeepStr: "10"))
        timeout(time: 30, unit: "MINUTES")
        timestamps()
    }

    environment {
        APP_NAME  = "my-service"
        REGISTRY  = "myregistry.azurecr.io"
        K8S_NS    = "production"
    }

    stages {
        stage("Checkout") {
            steps {
                checkout scm
                script { env.GIT_SHA = sh(returnStdout: true, script: "git rev-parse --short HEAD").trim() }
            }
        }

        stage("Build + Test") {
            steps { sh "mvn clean verify -T4 -q" }
            post { always { junit "target/surefire-reports/*.xml" } }
        }

        stage("Security Scans") {
            parallel {
                stage("SonarQube") {
                    steps {
                        withSonarQubeEnv("sonar") { sh "mvn sonar:sonar" }
                        timeout(time: 5, unit: "MINUTES") { waitForQualityGate abortPipeline: true }
                    }
                }
                stage("OWASP") {
                    steps { sh "mvn org.owasp:dependency-check-maven:check" }
                    post { always { publishHTML([reportName: "OWASP", reportDir: "target", reportFiles: "dependency-check-report.html"]) } }
                }
                stage("Trivy") {
                    steps {
                        sh "DOCKER_BUILDKIT=1 docker build -t ${REGISTRY}/${APP_NAME}:${GIT_SHA} ."
                        sh "trivy image --severity HIGH,CRITICAL --exit-code 1 ${REGISTRY}/${APP_NAME}:${GIT_SHA}"
                    }
                }
            }
        }

        stage("Push Image") {
            steps {
                withCredentials([usernamePassword(credentialsId: "registry-creds", usernameVariable: "USER", passwordVariable: "PASS")]) {
                    sh "docker login -u $USER -p $PASS ${REGISTRY}"
                    sh "docker push ${REGISTRY}/${APP_NAME}:${GIT_SHA}"
                }
            }
        }

        stage("Deploy") {
            when { branch "main" }
            steps {
                withKubeConfig([credentialsId: "k8s-prod"]) {
                    sh "kubectl set image deployment/${APP_NAME} ${APP_NAME}=${REGISTRY}/${APP_NAME}:${GIT_SHA} -n ${K8S_NS}"
                    sh "kubectl rollout status deployment/${APP_NAME} -n ${K8S_NS} --timeout=180s"
                }
            }
        }
    }

    post {
        success { slackSend channel: "#deployments", message: "OK: ${APP_NAME} #${BUILD_NUMBER}" }
        failure { slackSend channel: "#alerts",      message: "FAIL: ${APP_NAME} ${BUILD_URL}" }
        always  { cleanWs() }
    }
}