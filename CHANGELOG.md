# Changelog — Jenkins CI/CD Pipeline

All notable changes to this repository are documented here.
Format follows [Keep a Changelog](https://keepachangelog.com/en/1.0.0/).

## [Unreleased]

## [1.2.0] — 2026-06-07
### Added
- Security policy (SECURITY.md)
- MIT License
- .gitignore with comprehensive secret exclusions
- .env.example with safe placeholder values
- .pre-commit-config.yaml with Gitleaks + ShellCheck + yamllint hooks
- GitHub Actions security scan workflow (Gitleaks, Trivy, ShellCheck, yamllint)
- Dependabot config for GitHub Actions updates
- docs/TROUBLESHOOTING.md with category-specific common issues
- docs/GLOSSARY.md with SRE and studio-specific terminology
- docs/COMPLIANCE.md covering SOC2, ISO27001, GDPR, HIPAA applicability
- .github/CONTRIBUTING.md and PR/Issue templates

## [1.1.0] — 2026-06-07
### Added
- examples/ folder with one working config per studio option variant
- Mermaid architecture flow diagram in README
- scripts/validate.sh

## [1.0.0] — 2026-06-07
### Added
- Initial README with real-world problem → solution → lifecycle flow
- docs/USAGE.md