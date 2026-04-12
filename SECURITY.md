# Security

QuietKeep is regularly scanned using three independent tools to check for security issues in the website, dependencies, and source code.

## Security Scans

**[MDN HTTP Observatory](https://developer.mozilla.org/en-US/observatory/)** tests the website's HTTP headers and TLS configuration against current web security standards. A score of 115/100 with an A+ rating means all recommended security headers are correctly configured.

**[Trivy](https://trivy.dev/)** scans the project's dependency files for known vulnerabilities (CVEs) in third-party packages. Zero findings means no packages with known security issues are in use.

**[Semgrep](https://semgrep.dev/)** runs static analysis on the source code to catch common security bugs and anti-patterns before they ship.

| Tool | Target | Result | Date |
|------|--------|--------|------|
| MDN HTTP Observatory | quietwire.dev | A+ (115/100), 10/10 tests passed | 2026-04-11 |
| Trivy | backend/requirements.txt (pip) | 0 vulnerabilities | 2026-04-12 |
| Trivy | frontend/package-lock.json (npm) | 0 vulnerabilities | 2026-04-12 |
| Semgrep | Codebase | Passed, no findings | 2026-04-12 |
