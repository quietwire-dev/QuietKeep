# Security

QuietKeep is regularly scanned using five independent tools to check for security issues in the website, dependencies, source code, and license compliance.

## Security Scans

**[MDN HTTP Observatory](https://developer.mozilla.org/en-US/observatory/)** tests the website's HTTP headers and TLS configuration against current web security standards. A score of 115/100 with an A+ rating means all recommended security headers are correctly configured.

**[Trivy](https://trivy.dev/)** scans the project's dependency files for known vulnerabilities (CVEs) in third-party packages. Zero findings means no packages with known security issues are in use.

**[Semgrep](https://semgrep.dev/)** runs static analysis on the source code to catch common security bugs and anti-patterns before they ship.

**[ScanCode Toolkit](https://github.com/aboutcode-org/scancode-toolkit)** scans every file in the project for license declarations, copyright notices, and embedded package metadata. This ensures all code is properly licensed and no unexpected third-party copyrights are present.

**[ScanOSS](https://www.scanoss.com/)** checks source code fingerprints against a database of known open source projects to verify code originality and detect any unattributed third-party code.

| Tool | Target | Result | Date |
|------|--------|--------|------|
| MDN HTTP Observatory | quietwire.dev | A+ (115/100), 10/10 tests passed | 2026-04-11 |
| Trivy | backend/requirements.txt (pip) | 0 vulnerabilities | 2026-04-22 |
| Trivy | frontend/package-lock.json (npm) | 0 vulnerabilities | 2026-04-22 |
| Semgrep | Codebase | 0 findings (518 rules, 82 files) | 2026-04-22 |
| ScanCode | 81 project files | AGPL-3.0 consistent, no conflicts | 2026-04-22 |
| ScanCode | 225 frontend dependencies | All AGPL-compatible (MIT, Apache-2.0, ISC, BSD, MPL-2.0) | 2026-04-15 |
| ScanOSS | 45 source files | 41 original, 4 boilerplate/scaffold matches (no concerns) | 2026-04-22 |

*Dates reflect the server-side scan run date in UTC.*
