# SSLNexus Releases

Official binary releases for the SSLNexus Client Server.

This repository is intentionally **binary-release metadata only**. SSLNexus source code is not published here.

## Current release

SSLNexus 1.0.6 is the current production release in this repository. SSLNexus 1.0.5 is retained for rollback and compatibility purposes. SSLNexus 1.0.7 will be added only after its qualified release gate passes.

## Packages

Each release provides native Linux packages where available:

- Debian/Ubuntu: `.deb` (`amd64`)
- RHEL/AlmaLinux/Rocky Linux: `.rpm` (`x86_64`)

Release assets also include SHA-256 checksums and a CycloneDX SBOM.

## Verification

Always verify a downloaded package before installation:

```bash
sha256sum -c SHA256SUMS
```

Compare the result with the checksum file attached to the same GitHub Release.

## Installation

Debian/Ubuntu:

```bash
sudo apt install ./ssl-nexus_<version>_amd64.deb
```

RHEL/AlmaLinux/Rocky Linux:

```bash
sudo dnf install ./ssl-nexus-<version>-1.el10.x86_64.rpm
```

## Release history

See [CHANGELOG.md](CHANGELOG.md) and the versioned release metadata under [`releases/`](releases/).

## Security and private keys

SSLNexus is designed so certificate private keys remain within customer-controlled infrastructure whenever the selected certificate workflow allows it. Release packages should only be downloaded from official SSLNexus distribution locations and verified before installation.

## Source code

Customer/public distribution is binary-only. This repository does not contain SSLNexus source code.
