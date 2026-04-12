# Changelog

All notable changes to QuietKeep will be documented in this file.

---

## [Unreleased] - In Development

### Added
- **Home overview page**. Default landing page with at-a-glance host and Docker status
- **Docker stack management**. Discover, scan, and update Docker Compose stacks across hosts
- **One-click Docker updates**. Pull latest images and recreate containers with full log capture
- **Release notes links**. Auto-generated links to GitHub releases for container images
- **Pre-flight system checks**. First-run wizard verifies Python, SSH keys, OS, and Docker
- **System requirements FAQ**. Server specs, supported OS types, and Docker versioning in Help tab
- **Bug reporting**. Report a Bug link in Help tab for easy issue submission
- **Threat Intel dashboard**. CISA Known Exploited Vulnerabilities (KEV) catalog with vendor, threat actor, and time range filtering. Includes ransomware-linked CVE tracking
- **Light/Dark/System themes**. Full theme support with persistent preference
- **Settings page**. SSH config, scan intervals, auto-scan toggle, host management
- **First-run wizard**. Guided setup for new installations
- **SSH key upload via web UI**. Paste your private key, public key is derived automatically
- **Deploy SSH Key to Hosts**. Push the public key to managed hosts with one click using password auth
- **Host setup script**. Downloadable script to automate SSH key and sudo configuration
- **Docker Compose deployment**. Single compose file, builds from source, no manual config needed
- **Auto-detect server IP**. Self-signed cert generated with correct SAN at startup, no env vars required
- **Multi-OS support**. Debian/Ubuntu (apt), Kali Linux, Arch/CachyOS (pacman), Proxmox VE
- **Patch management**. Scan, patch, track history, detect reboots
- **Dashboard**. Clickable filter cards, progress banners, expandable log viewer
- **30-day auto-cleanup**. Patch history older than 30 days is automatically removed

### Fixed
- Docker scanner now preserves stack IDs across scans (upsert instead of delete/recreate)
- Docker update history persists correctly after re-scans
- Release notes links resolve correctly for monorepo images (Immich, Home Assistant, etc.)
- SSH clipboard copy works on non-HTTPS connections (fallback method)
- Light mode badge contrast improved for update indicators
- SSH key path mismatch between Dockerfile ENV and upload destination
- HomePage not refreshing host data after Scan All completes
