# Super11

A privacy-hardened, telemetry-free Windows 11 IoT Enterprise LTSC installation image built with [MSMG Toolkit](https://msmgtoolkit.in/). Engineered for sustained performance, long-term stability, and a minimal attack surface — without the overhead of consumer telemetry, bundled applications, or forced online account requirements.

-----

## Features

**Zero Telemetry**
Core diagnostic and tracking components (CEIP, UnifiedTelemetryClient, Windows Error Reporting) are removed at the image level — not merely disabled via policy.

**Fully Unattended Installation**
Ships with a pre-configured `autounattend.xml` answer file that automates EULA acceptance, skips all OOBE telemetry prompts, and enforces a local account setup. No network connection required during installation.

**No Pre-installed Applications**
Built on the IoT Enterprise LTSC base, which carries no consumer inbox apps, Xbox services, or retail-tier bloatware.

**Reduced Attack Surface**
Legacy compatibility packages, mixed reality components, and unused enterprise management features have been removed, reducing RAM consumption and on-disk footprint.

**10-Year Security Support**
Aligned with the IoT Enterprise LTSC servicing model — critical security updates through 2034, with no disruptive feature upgrades.

-----

## Requirements

- USB flash drive (8 GB or larger)
- [Rufus](https://rufus.ie/) or equivalent flashing utility
- A system meeting Windows 11 baseline hardware requirements

> **Note:** The IoT Enterprise LTSC foundation has relaxed enforcement of TPM 2.0 and Secure Boot compared to retail Windows 11 editions.

-----

## Installation

1. **Download** the latest `Super11_IoT.iso` from the [Releases](../../releases) page.
1. **Flash to USB** using Rufus. Select the ISO and your target drive, then proceed with default settings.
1. **Optional — Additional Privacy Hardening:** When Rufus prompts with customization options, enable *“Bypass requirement for an online Microsoft account”* and *“Disable data collection”* for redundant enforcement at the Rufus level.
1. **Prepare your machine:** Disconnect your Ethernet cable before booting. This is a precaution; the answer file already handles offline enforcement.
1. **Boot from USB** and allow the unattended installation to complete. When prompted for network connectivity, skip and proceed with a local account.

-----

## Disclaimer

This is an unofficial, community-built Windows image and is not affiliated with or endorsed by Microsoft.

- Provided **as-is**, without warranty of any kind, express or implied.
- A valid Windows 11 IoT Enterprise LTSC digital license or product key is **required** and is not included.
- Back up all critical data before proceeding. Installation will wipe the target drive.

-----

## Acknowledgements

- [MSMG Toolkit](https://msmgtoolkit.in/) — the tooling that makes deep image modification possible.
- Built and maintained by [Your GitHub Username](https://github.com/).