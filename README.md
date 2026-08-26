<div align="center">

# Cerberus XSS

### Advanced Cross-Site Scripting Testing for Authorized Security Assessments

[![Python](https://img.shields.io/badge/Python-3.9%2B-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
[![Platform](https://img.shields.io/badge/Platform-Kali%20Linux-557C94?style=for-the-badge&logo=kalilinux&logoColor=white)](https://www.kali.org/)
[![Interface](https://img.shields.io/badge/Interface-Rich%20Terminal%20UI-8A2BE2?style=for-the-badge)](https://github.com/Textualize/rich)
[![License](https://img.shields.io/badge/License-See%20Repository-333333?style=for-the-badge)](LICENSE)

**Cerberus XSS** is an advanced, terminal-based XSS testing framework created by **[Sudeepa Wanigarathne](https://github.com/CerberusMrXi)** for ethical hackers, penetration testers, security researchers, and bug bounty hunters.

It combines crawling, payload testing, WAF-aware mutation, DOM analysis, blind-XSS callback logging, proxy support, session persistence, and structured reporting in one interactive workflow.

[Features](#features) · [Installation](#installation) · [Usage](#usage) · [Proxy Setup](#proxy-support) · [Security](#ethical-use-and-security) · [Contributing](#contributing)

</div>

> **Important:** Cerberus XSS is intended only for systems that you own or are explicitly authorized to assess. Never scan, inject payloads into, or monitor callbacks from third-party systems without written permission.

![Cerberus XSS terminal interface](https://github.com/user-attachments/assets/2cbe8191-44e6-4773-abbd-9cd052e3a3b3)

## Overview

Cross-site scripting vulnerabilities can occur when untrusted input reaches an unsafe browser execution context. Cerberus XSS helps security professionals identify and validate potential XSS injection points during authorized assessments by automating repetitive discovery and testing tasks.

The tool is designed to support a transparent, researcher-controlled workflow. It does not replace manual verification, responsible disclosure, or a complete application security review.

## Features

| Capability | Description |
| --- | --- |
| **Web crawling** | Discovers pages, forms, parameters, and candidate injection points within an authorized target scope. |
| **Payload injection** | Tests a broad payload corpus, including encoded, obfuscated, and context-aware variants. |
| **WAF-aware mutation** | Applies mutation strategies such as case variation, comment insertion, and nested encoding to support controlled testing of filtering behavior. |
| **DOM-based XSS detection** | Searches client-side application behavior for potentially unsafe source-to-sink flows. |
| **Blind XSS logging** | Supports out-of-band callback workflows for authorized blind-XSS testing and callback observation. |
| **Rich terminal interface** | Provides interactive menus, progress indicators, tables, and readable scan output through [Rich](https://github.com/Textualize/rich). |
| **Session persistence** | Saves scan state so an assessment can be resumed without restarting from the beginning. |
| **Proxy support** | Routes traffic through an HTTP proxy such as Burp Suite for inspection and controlled debugging. |
| **Vulnerability reporting** | Presents discovered findings and relevant testing details in a structured terminal workflow. |

## Requirements

Cerberus XSS is primarily intended for **Kali Linux**. Before installation, ensure that you have:

- Python **3.9 or newer** with `pip` and `venv` support.
- Network access to the authorized assessment environment.
- A legally approved target scope and test window.
- An HTTP proxy, such as Burp Suite, if traffic inspection is required.

Python virtual environments isolate project dependencies from the system interpreter and are recommended for local security tooling.[1]

## Installation

### 1. Update the system and install prerequisites

```bash
sudo apt update
sudo apt install -y python3 python3-pip python3-venv git
```

### 2. Clone the repository

```bash
git clone https://github.com/CerberusMrXi/cerberus_xss.git
cd cerberus_xss
```

### 3. Create and activate a virtual environment

```bash
python3 -m venv venv
source venv/bin/activate
```

On Windows PowerShell, if you are adapting the project for a compatible environment, activation generally uses:

```powershell
.\venv\Scripts\Activate.ps1
```

### 4. Install dependencies

```bash
python -m pip install --upgrade pip
pip install -r requirements.txt
```

### 5. Launch Cerberus XSS

```bash
python cerberus_xss.py
```

When you are finished, leave the virtual environment with:

```bash
deactivate
```

## Usage

Start the interactive interface from the project directory:

```bash
source venv/bin/activate
python cerberus_xss.py
```

Follow the on-screen prompts to define the authorized target, configure crawl and payload options, select proxy settings, and begin the assessment. Always keep the scope as narrow as possible and start with non-destructive validation.

### Recommended assessment workflow

1. Confirm written authorization, target ownership, scope, exclusions, rate limits, and the reporting contact.
2. Configure the smallest practical crawl scope before starting discovery.
3. Review discovered forms and parameters before enabling broader payload testing.
4. Use a proxy during development or testing so requests can be inspected and stopped when necessary.
5. Manually verify suspected findings and remove any test data created during the assessment.
6. Export or preserve the session and document evidence for responsible disclosure.

## Proxy Support

Cerberus XSS can be used with an HTTP interception proxy such as Burp Suite. A typical local proxy listens on `127.0.0.1:8080`, but the exact host and port depend on your proxy configuration.

Before launching a scan:

1. Start your authorized proxy listener.
2. Enter the proxy host and port when prompted by Cerberus XSS.
3. Confirm that traffic is visible in the proxy history.
4. Verify that the target scope and request rate are correct.

Do not route traffic through a proxy or callback collector that you do not control or have permission to use.

## Blind XSS Callback Safety

Blind-XSS testing can generate callbacks from browsers or services that process submitted content later. Use a callback domain or collector that you control, clearly document the callback behavior in the authorization agreement, and avoid collecting unnecessary personal or sensitive information.

Callback logs may contain IP addresses, user agents, URLs, tokens, or other sensitive data. Protect them as assessment evidence, restrict access, and delete them according to your engagement’s retention policy.

## Output and Session Data

Depending on the project configuration, scan sessions and reports may contain target URLs, request data, payloads, callback metadata, and vulnerability evidence. Treat these files as confidential security data.

Before sharing a report, redact credentials, session cookies, API keys, personal information, internal hostnames, and unrelated third-party data.

## Ethical Use and Security

> **Cerberus XSS must not be used for unauthorized scanning, exploitation, persistence, credential theft, data exfiltration, service disruption, or evasion of security controls outside an approved security engagement.**

The authors are not responsible for damage, data loss, legal claims, or other consequences resulting from misuse. You are responsible for complying with applicable laws, contracts, program rules, and responsible-disclosure requirements.

For defensive validation, use a local lab or intentionally vulnerable application such as [OWASP Juice Shop](https://github.com/juice-shop/juice-shop) and follow the lab’s rules.[2]

## Troubleshooting

### `python: command not found`

Try the explicit Python 3 command:

```bash
python3 cerberus_xss.py
```

### `No module named ...`

Confirm that the virtual environment is active and reinstall the requirements:

```bash
source venv/bin/activate
python -m pip install -r requirements.txt
```

### Permission or package installation errors

Avoid installing project dependencies globally. Create a fresh virtual environment and use the environment’s `python` and `pip` commands:

```bash
rm -rf venv
python3 -m venv venv
source venv/bin/activate
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
```

### Proxy traffic is not visible

Check that the proxy listener is running, the configured host and port match the listener, and the target traffic is being generated by the same environment in which Cerberus XSS is running.

## Project Structure

A typical local checkout may contain files similar to the following:

```text
cerberus_xss/
├── cerberus_xss.py       # Main application entry point
├── requirements.txt      # Python dependencies
├── README.md             # Project documentation
├── venv/                 # Local virtual environment; do not commit
└── ...                   # Supporting modules, sessions, and reports
```

The exact structure may change as the project evolves.

## Contributing

Contributions are welcome when they improve reliability, documentation, test coverage, accessibility, or safe security-research workflows. Before opening a pull request, describe the problem being solved, explain the security and privacy implications, and test changes in a controlled lab environment.

Please do not submit payloads, callback data, credentials, private targets, or other sensitive assessment information. If the repository includes contribution guidelines or a code of conduct, follow those documents before submitting changes.

## Responsible Vulnerability Reporting

If you discover a security issue in Cerberus XSS itself, avoid posting exploit details publicly before the maintainer has had a reasonable opportunity to respond. Open a private security report through the repository’s supported contact method, including affected versions, reproduction steps, impact, and a safe proof of concept.

## Author

**Sudeepa Wanigarathne**

- GitHub: [@CerberusMrXi](https://github.com/CerberusMrXi)
- Project: [Cerberus XSS](https://github.com/CerberusMrXi/cerberus_xss)

## License

This project’s license should be documented in the repository’s [`LICENSE`](LICENSE) file. If no license has been selected yet, add one before accepting or distributing contributions.

## References

https://docs.python.org/3/library/venv.html "Python venv documentation"

https://owasp.org/www-project-juice-shop/ "OWASP Juice Shop"

<div align="center">

**Built for authorized security testing and responsible disclosure.**

</div>
