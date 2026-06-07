# ⚖️ Compliance & Legal Guide — Jenkins CI/CD Pipeline

> This guide covers legal, regulatory, and compliance considerations when using configurations from this studio in real production systems.

---

## 📜 License

This repository is licensed under the **MIT License** — see [LICENSE](../LICENSE) for full text.

**What this means:**
- ✅ You **can** use these configs freely in personal, commercial, or enterprise projects
- ✅ You **can** modify, distribute, and sublicense them
- ✅ You **can** use them without attribution in production configs
- ❌ You **cannot** hold the author liable for damages from using these configs

---

## 🔒 Security Compliance Frameworks

Depending on your industry, your infrastructure may need to comply with:

| Framework | Applies To | Key Requirements for This Studio |
|-----------|-----------|----------------------------------|
| **SOC 2 Type II** | SaaS companies | Audit logs, access controls, encryption at rest/transit |
| **ISO 27001** | Any org | Information security management, risk assessment |
| **PCI-DSS** | Payment processing | Network isolation, no plain-text card data, WAF |
| **HIPAA** | US Healthcare | PHI encryption, access logs, BAA agreements |
| **GDPR** | EU data controllers | Data minimization, right to erasure, DPA agreements |
| **FedRAMP** | US Federal systems | NIST 800-53 controls, continuous monitoring |
| **CIS Benchmarks** | All infra | Hardened OS/container/cloud baselines |

---

## ✅ Pre-Production Security Checklist

Before using any generated config in production, verify:

### Secrets Management
- [ ] No hardcoded credentials in any file
- [ ] Secrets stored in Vault / AWS SSM / GitHub Secrets / Azure Key Vault
- [ ] `.env` files listed in `.gitignore`
- [ ] Secret rotation policy defined

### Access Control
- [ ] Least-privilege principle applied (minimal IAM/RBAC permissions)
- [ ] MFA enabled for all human users
- [ ] Service accounts have no interactive login
- [ ] API keys scoped to minimum required permissions

### Network Security
- [ ] Network policies / security groups restrict traffic to necessary ports only
- [ ] All external endpoints use TLS 1.2+ (no HTTP for production)
- [ ] Internal service communication encrypted (mTLS where possible)
- [ ] Public-facing endpoints behind WAF / DDoS protection

### Audit & Monitoring
- [ ] All admin actions logged and retained for 90+ days
- [ ] Alerts configured for suspicious activity (failed logins, privilege escalation)
- [ ] Log forwarding to SIEM configured

### Patch Management
- [ ] Container base images pinned to specific digest (not `:latest`)
- [ ] Automated vulnerability scanning in CI/CD pipeline
- [ ] Dependency update policy defined (Dependabot / Renovate)

---

## 📋 Third-Party Software Notices

The configurations in this repository reference or use:

| Software | License | Notice |
|----------|---------|--------|
| Prometheus | Apache 2.0 | © The Prometheus Authors |
| Grafana | AGPL-3.0 | © Grafana Labs |
| Kubernetes | Apache 2.0 | © The Kubernetes Authors |
| Terraform | BSL 1.1 | © HashiCorp |
| Ansible | GPL-3.0 | © Red Hat / IBM |
| Docker | Apache 2.0 | © Docker, Inc. |
| Jenkins | MIT | © Jenkins Project |
| Helm | Apache 2.0 | © The Helm Authors |

> Always verify licenses for your use case. Commercial restrictions may apply (e.g., HashiCorp BSL).

---

## ⚠️ Disclaimer

The configurations in this repository are provided **for educational and reference purposes only**.

- They are **starting points**, not final production configurations
- They have **not been audited** by a professional security firm
- Your security and compliance requirements may differ
- **Always engage a qualified security professional** before deploying to systems handling sensitive data

---

*Maintained by [Talari Pradeep](https://pradeeptalari14.github.io/portfolio) — [MIT License](../LICENSE)*