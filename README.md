# Super-11

> A minimal, privacy-respecting Windows 11 IoT image built with [MSMG Toolkit](https://msmgtoolkit.in/). Reduced RAM footprint, smaller ISO, and no telemetry out of the box.

-----

## Overview

This is a custom Windows 11 IoT Enterprise LTSC build stripped of consumer bloat, tracking services, and legacy components that ship with retail Windows but serve no purpose on a clean workstation. The result is a leaner install that boots faster, uses less memory at idle, and doesn’t phone home.

-----

## What Was Removed

### Bloatware & Consumer Apps

|Component                     |Reason                                                 |
|------------------------------|-------------------------------------------------------|
|Cortana                       |Replaced by Start Menu search; telemetry source        |
|Bing News / Weather           |Unused widgets with background data calls              |
|OneDrive                      |Redundant if using a local or third-party sync solution|
|Clipchamp, Power Automate     |Niche tools; installable on demand                     |
|Xbox Overlay & Gaming Services|Unnecessary on non-gaming workstations                 |
|Zune Media / Media Players    |Legacy, superseded                                     |
|Get Help, Feedback Hub        |Telemetry endpoints disguised as support apps          |

### System Telemetry & Tracking

- `UnifiedTelemetryClient` — the primary Windows data collection service
- `WindowsErrorReporting` — crash reports sent to Microsoft
- `CEIP` (Customer Experience Improvement Program) — background usage analytics

### Corporate & Kiosk Components

- **AssignedAccess** — Kiosk Mode lockdown framework
- **MultiPointConnector** — Multi-user shared session service
- **WorkFolders** — Enterprise file sync for managed environments

### Legacy & Niche Utilities

- Fax & Scan services
- XPS Viewer and XPS print driver
- Remote Assistance (distinct from Remote Desktop)
- Windows Mixed Reality framework
- Retail Demo Mode content
- Offline Maps service and local speech recognition data

-----

## Optimizations Applied

**ISO size** — All Windows editions except Pro are stripped from the install image, significantly reducing ISO and install footprint.

**RAM at idle** — Local speech recognition datasets and the offline maps service are removed, eliminating background indexing processes that load into memory on boot.

**Disk space** — Retail Demo content and the Mixed Reality framework are excised before image capture, reclaiming several gigabytes on the final install.

-----

## Installation

**Requirements:** A USB drive of at least 8 GB and a machine with Secure Boot configurable (can be left on or disabled depending on your setup).

1. **Obtain the ISO** — Download the pre-built image, or build it yourself using MSMG Toolkit with the configuration files in this repository.
1. **Flash to USB** — Use [Rufus](https://rufus.ie) with the default GPT + UEFI settings for modern hardware, or MBR for legacy BIOS systems.
1. **Boot and install** — Enter your firmware boot menu, select the USB drive, and proceed through a standard Windows setup.

> **Note:** Because certain default apps and services are absent, the initial OOBE (out-of-box experience) may skip a few setup screens. This is expected behaviour.

-----

## Build It Yourself

All MSMG Toolkit configuration files used to produce this image are included in the `/config` directory. To reproduce the build:

```
1. Install MSMG Toolkit on a Windows host
2. Mount a retail Windows 11 Pro ISO
3. Apply the config files from /config
4. Run the toolkit's removal and integration steps
5. Capture the modified image to a new ISO
```

Refer to the [MSMG Toolkit documentation](https://msmgtoolkit.in/) for full build instructions.

-----

## Disclaimer

This project modifies a Windows installation image for personal use. It is not affiliated with or endorsed by Microsoft. Removing system components may affect compatibility with certain software or Windows Update behaviour. Use at your own discretion.