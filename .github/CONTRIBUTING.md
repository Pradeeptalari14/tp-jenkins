# Contributing Guidelines

Thank you for your interest in improving the **Jenkins CI/CD Pipeline** studio resources! 🎉

---

## How to Contribute

### 1. Reporting Issues

Found a bug, incorrect config, or misleading documentation?

1. **Check existing issues** first to avoid duplicates
2. **Open a new issue** using the appropriate template:
   - 🐛 Bug Report — for incorrect generated configs or broken scripts
   - 💡 Feature Request — for new studio options or example variants

### 2. Submitting Improvements

```bash
# 1. Fork this repository
# 2. Clone your fork
git clone https://github.com/YOUR_USERNAME/tp-jenkins.git

# 3. Create a feature branch
git checkout -b feat/improve-docker-multistage-example

# 4. Make your changes
# 5. Test your changes (run scripts, validate YAML, etc.)

# 6. Commit with conventional commit format
git commit -m "feat: add golang multi-stage Dockerfile variant"
git commit -m "fix: correct HPA minReplicas to 2"
git commit -m "docs: add troubleshooting for ImagePullBackOff"

# 7. Push and open a Pull Request
git push origin feat/improve-docker-multistage-example
```

---

## Contribution Standards

### ✅ Config File Requirements
- All YAML files must be **valid** — use `yamllint` or `kubectl --dry-run`
- All shell scripts must pass **shellcheck**
- No hardcoded secrets, IPs, or personal data
- Add a comment header explaining **what** the file does and **when** to use it

### ✅ Documentation Requirements
- Keep examples **realistic and production-relevant**
- Link to official documentation for any tool or flag used
- Include the **why**, not just the **what**

### ✅ Security Requirements
- Run `gitleaks detect` before pushing (see SECURITY.md)
- No credentials, API keys, or passwords in any file
- Mark any sensitive placeholder with `REPLACE_WITH_YOUR_VALUE`

---

## Code of Conduct

Be respectful. Be constructive. Help each other learn.

This project follows the [Contributor Covenant Code of Conduct](https://www.contributor-covenant.org/version/2/1/code_of_conduct/).

---

## Related Studio

Generated configurations come from the **[Jenkins CI/CD Pipeline Studio](https://pradeeptalari14.github.io/portfolio/tools/jenkins/)**.
If you find the studio itself has a bug, please open an issue on the [main portfolio repository](https://github.com/Pradeeptalari14/portfolio).