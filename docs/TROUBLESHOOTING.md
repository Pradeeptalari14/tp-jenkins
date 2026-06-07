# 🔧 Troubleshooting Guide — Jenkins CI/CD Pipeline

> Common issues, error messages, and their fixes.

---

## Issue 1: Permission denied when running a script

```bash
chmod +x scripts/validate.sh
./scripts/validate.sh
```

---

## Issue 2: File contains Windows line endings (CRLF) and fails on Linux

```bash
# Convert CRLF to LF
dos2unix scripts/validate.sh
# Or with sed:
sed -i "s/\r//" scripts/validate.sh
```

---

## Issue 3: git push fails: "remote: Permission to ... denied"

```bash
# Ensure your GitHub token has repo write access
gh auth status
gh auth login   # re-authenticate if needed
```

---

## Still Stuck?

1. **Read the error carefully** — the fix is usually in the message itself
2. **Check official documentation:**
   - [GitHub Issues for this repo](https://github.com/Pradeeptalari14/tp-jenkins/issues)
   - [Studio FAQ](https://pradeeptalari14.github.io/portfolio/tools/jenkins/)
3. **Open an issue** using the [Bug Report template](.github/ISSUE_TEMPLATE/bug_report.md)

---

*Part of [Talari Pradeep Developer Studio Portfolio](https://pradeeptalari14.github.io/portfolio)*