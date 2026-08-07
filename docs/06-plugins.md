# 06 — Plugins

Plugins installed on this build, and why they're there. OPNsense plugins are installed from the web UI under **System > Firmware > Plugins**.

## CrowdSec

Behavioural detection and collaborative IP blocking. It reads your logs, spots malicious patterns (brute-force, scanning, etc.), and blocks the offending addresses — while also drawing on a shared community blocklist.

### Installation

<!-- TO FILL:
     - the plugin name to install (os-crowdsec)
     - any repository step needed beforehand
     - the version you installed -->

### How it works, in short

CrowdSec has two halves:

- the **agent**, which detects and decides
- the **bouncer**, which enforces the block

On OPNsense the plugin wires both into the firewall. Detected IPs land in the alias CrowdSec maintains, and your firewall rules drop them.

### Configuration

<!-- TO FILL:
     - enrolment key / console signup (mention it exists; do NOT paste your key here)
     - which collections you enabled
     - log sources it watches -->

> ⚠️ Never commit your CrowdSec enrolment key or API credentials to this repo. The `.gitignore` blocks config exports for exactly this reason.

### Checking it runs

<!-- TO FILL:
     - where to see active decisions in the web UI
     - useful console commands (cscli metrics, cscli decisions list)
     - where the logs are -->

### Resource use

<!-- TO FILL: measured CPU/RAM impact. On a Xeon E5-2620 v3 with 24 GB
     it should be negligible, but a real figure is more convincing than
     "it's fine" — note what you actually observed. -->

## Other plugins

<!-- TO FILL as you add them. Common ones on a home/lab firewall:
     - os-wireguard      — WireGuard VPN
     - os-acme-client    — free Let's Encrypt certificates
     - os-ddclient       — dynamic DNS
     - os-theme-*        — web UI themes
     For each: what it does, why you added it, anything F800-specific. -->

---

Next: [Troubleshooting](07-depannage.md)
