# Changelog

All notable changes to QuietKeep will be documented in this file.

---

## [Unreleased] - In Development

### Added
- **Held-back updates surfacing**. When `apt-get upgrade` defers packages that would require installing new dependencies (typically kernel metapackages on Ubuntu/Debian), the Host Detail page now shows a dedicated card listing what was held back, with an explicit Install Held-Back Updates button that runs `apt-get upgrade --with-new-pkgs`. A Held Back column on the Host Management table shows the count per host so you can spot deferred updates at a glance
- **Faster Docker stack scans**. Docker discovery and update checks across multiple hosts now run in parallel instead of sequentially
- **Automated sudoers probing**. Every host scan now checks whether the `/etc/sudoers.d/quietkeep-<user>` NOPASSWD rule is present. Status is surfaced as an OK / Needs Fix / Unknown / Root badge in both Host Detail and Host Management
- **One-click Fix Sudoers**. New modal installs the sudoers rule on a host using a one-time password, eliminating the need to SSH into each host by hand
- **GPG key-rotation detection**. The patcher recognizes NO_PUBKEY / EXPKEYSIG / expired-key failures on apt and Kali hosts and tags the patch log so the UI can respond
- **Keyring recovery modal**. When a key rotation is detected, the Host Detail view shows a persistent banner and an in-app popup with OS-specific secure recovery commands (HTTPS-fetched archive keyring, sha256 verification, dpkg install). No auto-trust of new signing keys by design
- **`apt-get --fix-broken install` step**. The patcher now completes half-finished dpkg transactions before running the upgrade, fixing a common source of silent patch stalls on Kali rolling releases
- **Shared ConfirmDialog component**. Centered, accessible confirmation modal with danger/warning/primary variants. Replaces native `window.confirm()` dialogs across Patch, Reboot, Docker Update, and Delete All Hosts
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
- Reboot action now reports honest success/failure based on SSH session behavior and sudo exit codes instead of always returning success
- Patch runs that fail because the host is missing a NOPASSWD sudoers rule no longer misreport as success with 0 packages; they now fail loudly and the UI surfaces the sudoers badge
- `setup-host.sh` sudoers rule widened to cover `apt-get` and `pacman` commands (previously only `apt`), fixing silent patch failures on hosts that were set up with the earlier, narrower rule
- Confirmation dialogs for Patch, Reboot, Docker Update, and Delete All Hosts now render in the center of the viewport instead of at the top where they were easy to miss (BUG-003)
- SSH Test indicator in Host Management now reflects the persisted online state after the test completes instead of showing stale data
- Docker scanner now preserves stack IDs across scans (upsert instead of delete/recreate)
- Docker update history persists correctly after re-scans
- Release notes links resolve correctly for monorepo images (Immich, Home Assistant, etc.)
- SSH clipboard copy works on non-HTTPS connections (fallback method)
- Light mode badge contrast improved for update indicators
- SSH key path mismatch between Dockerfile ENV and upload destination
- HomePage not refreshing host data after Scan All completes
