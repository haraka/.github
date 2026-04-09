# Security Policy & Incident Response Plan

## Supported Versions

Security fixes are applied to the **latest stable release** of each affected Haraka package. Older major versions receive fixes only for critical (CVSS ≥ 9.0) vulnerabilities.

| Package | Supported |
|---------|-----------|
| haraka (latest stable) | ✅ |
| haraka (previous major) | critical only |
| All other packages (latest stable) | ✅ |

---

## Reporting a Vulnerability

**Do not open a public GitHub issue for security vulnerabilities.**

Report vulnerabilities using one of these private channels:

1. **GitHub private security advisory** (preferred):  
   [https://github.com/haraka/Haraka/security/advisories/new](https://github.com/haraka/Haraka/security/advisories/new)

2. **Email**: haraka.mail@gmail.com
   Encrypt sensitive reports with the maintainers' PGP key (available on request).

Include as much of the following as possible:

- Affected package(s) and version(s)
- A description of the vulnerability and its impact
- Steps to reproduce or a proof-of-concept
- Any suggested mitigations

---

## Response Timeline

| Milestone | Target |
|-----------|--------|
| Acknowledge receipt | 48 hours |
| Triage and severity assessment | 5 business days |
| Patch development begins | 7 business days (critical: immediately) |
| Patch released | 30 days (critical: 7 days) |
| Public disclosure | After patch is released and users have time to upgrade |

We follow [coordinated disclosure](https://en.wikipedia.org/wiki/Coordinated_vulnerability_disclosure). If a reporter has a shorter disclosure deadline, please note it in your report.

---

## Severity Classification

We use [CVSS v3.1](https://www.first.org/cvss/) to score vulnerabilities:

| Severity | CVSS Score | Response |
|----------|------------|----------|
| Critical | 9.0–10.0 | Patch within 7 days, immediate out-of-band release |
| High | 7.0–8.9 | Patch within 14 days |
| Medium | 4.0–6.9 | Patch in next scheduled release (≤30 days) |
| Low | 0.1–3.9 | Patch in next scheduled release |

---

## Incident Response Process

### 1. Detection & Intake

- A report is received via private advisory or email.
- A maintainer acknowledges receipt and creates a **private GitHub security advisory** if one does not already exist.
- The reporter is added as a collaborator on the advisory.

### 2. Triage

- A maintainer reviews the report.
- Assign a CVSS score and severity label.
- Determine affected packages and version ranges.
- Identify whether a workaround exists.

### 3. Remediation

- A **private fork or branch** is created off the affected package's `main` branch.
- A fix is developed and reviewed privately by at least one maintainer who did not write the fix.
- Tests are added covering the vulnerability.
- The fix is validated against all supported Node.js versions using the existing CI matrix.

### 4. Release

- A patched version is published to npm.
- The GitHub security advisory is published, referencing the CVE (requested from GitHub if not already assigned).
- Release notes include a security section describing the vulnerability at a high level without a full exploit guide.
- Affected users are notified via:
  - GitHub security advisory (automatic for users watching the repo)
  - A post in the [Haraka discussion forums / mailing list](https://github.com/haraka/Haraka/discussions) if severity is High or Critical

---

## Scope

The following are considered **in-scope** for security reports:

- Remote code execution, privilege escalation, or authentication bypass in core Haraka or any `haraka-plugin-*` package
- Denial-of-service vulnerabilities exploitable by unauthenticated remote attackers
- Header injection, SMTP smuggling, or email spoofing facilitated by Haraka
- Sensitive data exposure (credentials, email content) due to insecure defaults

The following are **out of scope**:

- Vulnerabilities in dependencies (report to the upstream project; we will update the dependency)
- Issues that require physical access to the server
- Social engineering or phishing attacks
- Findings from automated scanners without a demonstrated impact

---

## Credits

We are grateful to security researchers who responsibly disclose vulnerabilities. With the reporter's permission, we acknowledge contributors in the security advisory and in the package CHANGELOG.

---

## Contact

For questions about this policy, open a [GitHub Discussion](https://github.com/haraka/Haraka/discussions) or email haraka.mail@gmail.com.
