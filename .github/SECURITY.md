# Security Policy

We take the security of this product seriously and if you believe you have found a security vulnerability, please check to ensure the version you're using is still supported and actively being developed and then report it to us as described below.

## Reporting a Vulnerability

**Please do not report security vulnerabilities through public GitHub issues.**

Instead, please report them to the team directly via [email](mailto:security-policy@theholocron.dev).

Please include the requested information listed below (as much as you can provide) to help us better understand the nature and scope of the possible issue:

  * Type of issue (e.g. buffer overflow, SQL injection, cross-site scripting, etc.)
  * Full paths of source file(s) related to the manifestation of the issue
  * The location of the affected source code (tag/branch/commit or direct URL)
  * Any special configuration required to reproduce the issue
  * Step-by-step instructions to reproduce the issue
  * Proof-of-concept or exploit code (if possible)
  * Impact of the issue, including how an attacker might exploit the issue

This information will help us triage your report more quickly.

### Preferred Languages

We prefer all communications to be in English.

## Response Time

We are committed to working with security researchers to resolve issues promptly. Here’s how we typically handle reports:

* **Acknowledgment**: We will acknowledge the receipt of your vulnerability report within 48 hours.
* **Investigation**: We will investigate the reported issue, determine the impact, and develop a fix if necessary.
* **Resolution**: Once a fix is made, we will notify you and, if appropriate, publicly disclose the vulnerability and fix.

You can expect a full response (including a fix and a disclosure plan) within 7 business days of the acknowledgment.

## Supported Versions

Check the repository's README file for a table of which versions are currently being supported with security updates.

The chart will look similar to the following:

| Version  | Supported          |
| -------- | ------------------ |
| 4.x.x    | :white_check_mark: |
| 3.42.x   | :white_check_mark: |
| < 3.42.x | :x:                |
| 2.53.x   | :white_check_mark: |
| < 2.53.5 | :x:                |

## Security Update Process

When a vulnerability is identified and resolved, we will take the following steps:

1. **Patch**: A patch will be developed and tested.
2. **Notification**: All users will be notified of the security update.
3. **Disclosure**: A security advisory will be issued, providing details about the vulnerability, its impact, and the steps to mitigate it.

## General Security Practices

To maintain the security of this project, we adhere to the following practices:

* **Regular Audits**: We conduct internal security audits to identify and resolve potential issues.
* **Dependency Management**: We keep dependencies up-to-date and perform regular checks for vulnerabilities.
* **Access Control**: We follow the principle of least privilege for both codebase access and repository permissions.
* **Code Reviews**: All changes are reviewed to ensure they adhere to best security practices.

## Scope

This policy applies to security issues within the codebase of this repository, including:

* Code flaws such as buffer overflows, injection attacks, etc.
* Sensitive data leaks (e.g., unintended exposure of secrets or credentials).
* Authentication and authorization issues.

This policy **does NOT** cover social engineering attacks, denial of service attacks, or any third-party dependencies that are outside of our control.

We greatly appreciate your contributions to the security of this project!
