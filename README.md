# SSLNexus Client Server

Latest release: **v1.0.11**, released **12 October 2026**.

SSLNexus is a self-hosted certificate management platform for issuing, deploying, renewing, discovering and managing certificates across Linux, Windows and application environments. Certificate keys and CA credentials remain within customer infrastructure.

## Downloads

Download the signed binary package for your Linux server from the [v1.0.11 release](https://github.com/SSLNexus/sslnexus-releases/releases/tag/v1.0.11):

| Server | Package |
| --- | --- |
| Debian / Ubuntu, amd64 | `ssl-nexus_1.0.11_amd64.deb` |
| RHEL / Rocky Linux / AlmaLinux, x86_64 | `ssl-nexus-1.0.11-1.el10.x86_64.rpm` |

The Client Server runs on Linux and manages supported Windows targets remotely. Releases include checksums, OpenPGP signatures and a CycloneDX software bill of materials. Verify the signing-key fingerprint through a trusted SSLNexus channel before trusting a downloaded key.

## Changes in v1.0.11

- Reissue retained, valid certificates without contacting the CA, consuming issuance limits or incurring issuance charges. Request new certificate remains a separate action.
- Keep issued certificates for recovery and redeployment, with optional encryption of stored certificate private keys.
- Preserve the selected web server and other sites during deployment. A failed configuration check prevents reload.
- Group repeated discovery observations and remove unwanted inventory entries while retaining deployed certificates and issuance history.
- Improve application certificate deployment, account sign-in links and account security.

## Install or upgrade

Back up SSLNexus configuration, database and certificate material before upgrading. Include the matching unlock key if local keystore encryption is enabled. Review the release notes before installation.

Debian / Ubuntu:

```bash
sudo apt install ./ssl-nexus_1.0.11_amd64.deb
```

RHEL / Rocky Linux / AlmaLinux:

```bash
sudo dnf install ./ssl-nexus-1.0.11-1.el10.x86_64.rpm
```

Upgrade in place without uninstalling the existing package. Allow a maintenance window: upgrade duration depends on database size and backup time.

After installation or upgrade:

```bash
sudo ssl-nexus-admin preflight
sudo ssl-nexus-admin security verify --json
```

Confirm **1.0.11** in the dashboard. See the [documentation](https://docs.sslnexus.com) and the [SSLNexus website](https://sslnexus.com) for setup and supported integrations. Installation and upgrade guides are also included with the packages.

## Security and licensing

Keystore encryption is optional. Automatic unlock supports unattended renewal; protect the server, unlock key and backups separately. SSLNexus uses the Go Cryptographic Module v1.0.0; this module's validation does not constitute a separate FIPS validation of the entire SSLNexus product.

Features depend on the active licence and configured integrations. This repository distributes binary packages and customer documentation.
