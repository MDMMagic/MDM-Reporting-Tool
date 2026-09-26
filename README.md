> [!WARNING]
> **Licence purchasing is not available at the moment, but will be in the near future.** In the meantime, every new install includes a 72-hour free trial with all features unlocked.

<div align="center">

# MDM Reporting Tool

**Point it at your MDM, get an audit report.**

A native macOS app that connects to **Jamf Pro**, **Microsoft Intune** and **Iru** over their APIs and
renders a polished, branded, self-contained HTML report — with an optional PDF or DOCX alongside.

[**Download the latest release →**](https://github.com/MDMMagic/MDM-Reporting-Tool/releases/latest) · [Documentation](https://github.com/MDMMagic/MDM-Reporting-Tool/wiki) · [mdmmagic.au](https://mdmmagic.au)

<img src="https://raw.githubusercontent.com/wiki/MDMMagic/MDM-Reporting-Tool/images/01-mdm-selection.png" alt="Choose your MDM" width="760">

</div>

---

Instead of clicking through each console to piece together a configuration snapshot, you pick a
platform, authenticate, choose your sections, and the tool pulls everything over the API and renders
it into a single file you can email, attach to a ticket, or archive.

Every API client is **read-only**. Nothing is ever written back to your MDM.

## Install

1. Download the latest `.pkg` from [**Releases**](https://github.com/MDMMagic/MDM-Reporting-Tool/releases/latest).
2. Double-click it and follow the installer.
3. Launch **MDM Reporting Tool** from `/Applications`.
4. Every feature is unlocked for a **72-hour free trial**. Activate a licence any time to keep full access.

The package is signed with a Developer ID certificate and notarised by Apple, so it installs without
any Gatekeeper warnings. Requires **macOS 15.0 or later**.

<details>
<summary><b>Deploying to a fleet</b></summary>

<br>

It's an ordinary signed installer package — upload it to Jamf Pro, Intune or anything else and deploy
it like any other package, or install it on the command line:

```bash
sudo installer -pkg /path/to/MDMReportingTool.pkg -target /
```

Each machine activates its own licence. See [Getting Started](https://github.com/MDMMagic/MDM-Reporting-Tool/wiki/Getting-Started#deploying-with-mdm).

</details>

## The report

<img src="https://raw.githubusercontent.com/wiki/MDMMagic/MDM-Reporting-Tool/images/16-report-jamf-html.png" alt="The HTML report" width="100%">

One self-contained HTML file — no external assets, no server, no internet needed to open it. Sticky
navigation sidebar, a live filter that searches section names *and* table content, expand/collapse
all, an inventory panel, a light/dark toggle, and a print stylesheet that produces a clean paginated
document. Logo, colour theme, title and footer are yours.

| | |
|---|---|
| **Three MDM platforms** | Jamf Pro (65 sections), Microsoft Intune via Graph (23 sections), Iru (15 sections) |
| **Export formats** | HTML, HTML + PDF, HTML + DOCX |
| **Security compliance** | Fleet-wide FileVault, Gatekeeper, SIP, firewall and other security settings, XProtect definitions compared with Apple's latest releases, and login banner / password hint checks |
| **Security audit** | Jamf Compliance Benchmarks checked against the mSCP baselines your instance actually uses |
| **App version check** | Installed app versions across your Macs compared with the latest on Homebrew, optionally limited to Macs with recent inventory |
| **Scheduled agents** | Unattended runs delivered by email, Slack, Teams, or HTTP upload |
| **Report diffing** | Compare two saved reports and see exactly what changed |
| **Credential safety** | Everything sensitive lives in the macOS Keychain, with saved server profiles for Jamf Pro, Intune and Iru |
| **Read-only and local** | Never writes to your MDM. No vendor backend, no telemetry |
| **Permission preflight** | Verifies all 19 required Jamf read privileges before a run starts |

## How it works

Six steps, with a progress bar across the top and back-navigation at any point:

**1 · MDM** → **2 · Authenticate** → **3 · Options** → **4 · Sections** → **5 · Generate** → **6 · Done**

For Jamf Pro, two optional steps come after Sections: **Check Application Versions** and **Report
Extras** (the security audit).

The connection is tested before anything else happens, so a bad URL or an expired secret surfaces at
step 2 rather than halfway through a run. Every section is opt-in. Reports are timestamped rather
than overwritten, which is what makes diffing two of them useful.

<p align="center">
  <img src="https://raw.githubusercontent.com/wiki/MDMMagic/MDM-Reporting-Tool/images/07-jamf-sections.png" alt="Select report sections" width="49%">
  <img src="https://raw.githubusercontent.com/wiki/MDMMagic/MDM-Reporting-Tool/images/10-report-complete-jamf.png" alt="Report complete" width="49%">
</p>

## What you need to connect

| Platform | Credentials |
|---|---|
| **Jamf Pro** | Server URL plus either a username/password or an API client — [setup](https://github.com/MDMMagic/MDM-Reporting-Tool/wiki/Connecting-to-Jamf-Pro) |
| **Microsoft Intune** | An Entra app registration with read-only Graph permissions — [setup](https://github.com/MDMMagic/MDM-Reporting-Tool/wiki/Connecting-to-Microsoft-Intune) |
| **Iru** | Tenant subdomain and an API token — [setup](https://github.com/MDMMagic/MDM-Reporting-Tool/wiki/Connecting-to-Iru) |

## Documentation

The [**wiki**](https://github.com/MDMMagic/MDM-Reporting-Tool/wiki) covers everything:

| | |
|---|---|
| [Getting Started](https://github.com/MDMMagic/MDM-Reporting-Tool/wiki/Getting-Started) | Install, deploy, and a walkthrough of the six-step workflow |
| [Connecting to Jamf Pro](https://github.com/MDMMagic/MDM-Reporting-Tool/wiki/Connecting-to-Jamf-Pro), [Intune](https://github.com/MDMMagic/MDM-Reporting-Tool/wiki/Connecting-to-Microsoft-Intune), [Iru](https://github.com/MDMMagic/MDM-Reporting-Tool/wiki/Connecting-to-Iru) | Credentials, saved servers and required privileges |
| [Report Sections](https://github.com/MDMMagic/MDM-Reporting-Tool/wiki/Report-Sections) | Everything each platform can report on |
| [The HTML Report](https://github.com/MDMMagic/MDM-Reporting-Tool/wiki/The-HTML-Report) | What the report does, and the other output formats |
| [Security Audit](https://github.com/MDMMagic/MDM-Reporting-Tool/wiki/Security-Audit) | The Jamf Compliance Benchmarks / mSCP pass |
| [Application Version Check](https://github.com/MDMMagic/MDM-Reporting-Tool/wiki/Application-Version-Check) | Installed versions compared with Homebrew |
| [Automated Reports](https://github.com/MDMMagic/MDM-Reporting-Tool/wiki/Automated-Reports) | Scheduled agents and delivery options |
| [Comparing Reports](https://github.com/MDMMagic/MDM-Reporting-Tool/wiki/Comparing-Reports) | Diffing two reports |
| [Preferences](https://github.com/MDMMagic/MDM-Reporting-Tool/wiki/Preferences) | Appearance, branding, save paths |
| [Troubleshooting](https://github.com/MDMMagic/MDM-Reporting-Tool/wiki/Troubleshooting) | Diagnostics, debug mode, common failures |
| [Licensing](https://github.com/MDMMagic/MDM-Reporting-Tool/wiki/Licensing) | The free trial, what works without a licence, activation |
| [Security FAQ](https://github.com/MDMMagic/MDM-Reporting-Tool/wiki/Security-FAQ) | Answers for security teams approving the tool: TLS, storage, access |

## Licence

Every new install gets a **72-hour free trial** with everything unlocked. After that, Jamf Pro
settings reports keep working without a licence. A licence unlocks all three platforms, every report
section, the security audit and app version check, PDF and DOCX export, webhook notifications,
scheduled agents and Keychain credential saving — see
[Licensing](https://github.com/MDMMagic/MDM-Reporting-Tool/wiki/Licensing).

## Support

Found a bug, or want something added? [Open an issue](https://github.com/MDMMagic/MDM-Reporting-Tool/issues)
— attach the run's diagnostics log, and redact instance URLs and any identifying data first.

---

<div align="center">

This repository hosts releases, documentation and issues. The app itself is closed source.

[mdmmagic.au](https://mdmmagic.au)

</div>
