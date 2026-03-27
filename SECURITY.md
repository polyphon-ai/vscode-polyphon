# Security Policy

## Supported Versions

Only the latest release is actively maintained and receives security fixes.

| Version | Supported |
|---------|-----------|
| 0.1.x   | ✓         |

## Reporting a Vulnerability

**Do not open a public GitHub issue for security vulnerabilities.**

Report vulnerabilities privately via [GitHub's private vulnerability reporting](https://github.com/polyphon-ai/vscode-polyphon/security/advisories/new).
Include a description of the issue, steps to reproduce, and potential impact.
You will receive a response within 7 days.

## Security Considerations

### API token storage

The Polyphon API token is stored in VS Code's user settings (`settings.json`). This file is stored in plain text on disk. Avoid storing the token in workspace settings, which may be committed to source control.

### Data transmission

When code context attachment is enabled, the content of your active file selection and error diagnostics are sent over a localhost TCP connection to the running Polyphon instance. This data is then processed by Polyphon and forwarded to whatever AI providers you have configured (Anthropic, OpenAI, etc.). Do not attach context containing confidential, sensitive, or personally identifiable information.

### Localhost-only connection

The extension connects to Polyphon over TCP on `127.0.0.1` (configurable). The API token is transmitted in plain text over this connection. This is intentional — the connection is designed for local use only. Do not expose the Polyphon API port to the network.

### AI-generated content

This repository contains AI-assisted code. Review all configurations, scripts, and logic before deploying in sensitive or production environments.
