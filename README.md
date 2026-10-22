# SSLNexus Client Server

Release: **v1.0.12** — **16 October 2026**. Includes optional scheduled host maintenance. See `RELEASE_NOTES_1.0.12.md` and `HOST_MAINTENANCE.md`.

SSLNexus is a self-hosted certificate management platform for issuing, deploying, renewing, discovering and managing certificates across Linux, Windows and application environments. Certificate keys and CA credentials remain within customer infrastructure.

## Downloads

Download the signed binary package for your Linux server from the [v1.0.12 release](https://github.com/SSLNexus/sslnexus-releases/releases/tag/v1.0.12):

| Server | Package |
| --- | --- |
| Debian / Ubuntu, amd64 | `ssl-nexus_1.0.12_amd64.deb` |
| RHEL / Rocky Linux / AlmaLinux, x86_64 | `ssl-nexus-1.0.12-1.el10.x86_64.rpm` |

The Client Server runs on Linux and manages supported Windows targets remotely. Releases include checksums, OpenPGP signatures and a CycloneDX software bill of materials. Verify the signing-key fingerprint through a trusted SSLNexus channel before trusting a downloaded key.

## Changes in v1.0.12

- Encrypt new recovery archives with a separately held, verified recovery key. See [Backup archive encryption](BACKUP_ENCRYPTION.md).
- Schedule optional host maintenance with reviewed playbooks, advance alerts, verified remote backups and recovery checks on every plan.
- Enable independent recovery monitoring and overdue alerts through the Authority.

- Open relevant documentation directly from administration pages, sections and certificate-provider selection.
- Reverse optional keystore encryption with a supported offline command, with verification and resumable conversion.
- Report missing GoDaddy and The SSL Store certificate statuses explicitly.
- Distinguish observed post-quantum certificate algorithms from hybrid TLS key exchange in SSL Monitoring.
- Use reporting hostnames separately from target connection addresses.
- View support conversations with formatting, supported attachments and reviewed diagnostic reports.
- Show customer-facing staff public usernames and detailed support usage history.
- Receive eligible evaluation extensions through the existing licence refresh.

See `RELEASE_NOTES_1.0.12.md` for upgrade requirements and feature details.


## Install or upgrade

Back up SSLNexus configuration, database and certificate material before upgrading. Include the matching unlock key if local keystore encryption is enabled. Review the release notes before installation.

Debian / Ubuntu:

```bash
sudo apt install ./ssl-nexus_1.0.12_amd64.deb
```

RHEL / Rocky Linux / AlmaLinux:

```bash
sudo dnf install ./ssl-nexus-1.0.12-1.el10.x86_64.rpm
```

Upgrade in place without uninstalling the existing package. Allow a maintenance window: upgrade duration depends on database size and backup time.

After installation or upgrade:

```bash
sudo ssl-nexus-admin preflight
sudo ssl-nexus-admin security verify --json
```

Confirm **1.0.12** in the dashboard. See the [documentation](https://sslnexus.com/docs/) and the [SSLNexus website](https://sslnexus.com) for setup and supported integrations. Installation and upgrade guides are also included with the packages.

## Security and licensing

Keystore encryption is optional. Automatic unlock supports unattended renewal; protect the server, unlock key and backups separately. SSLNexus uses the Go Cryptographic Module v1.0.0; this module's validation does not constitute a separate FIPS validation of the entire SSLNexus product.

Features depend on the active licence and configured integrations. This repository distributes binary packages and customer documentation.

## Evaluation duration

New evaluations last 30 days from verified activation. Organisation owners and licence administrators can request an eligible one-time extension in Client Area under Evaluation options. The extension adds 60 days, giving 90 days in total from the original activation. Existing seven-day evaluations retain their original duration and are not eligible for this extension. Permanent Free and paid-licence grace periods are unchanged.

## Support conversations and attachments

Open a ticket or reply in Support and use the formatting toolbar or type Markdown. Format text, add code blocks, lists, quotes and links, and preview your message before sending. Pasted images are added as attachments. HTML content and externally hosted images are not displayed in messages.

Attach PNG/JPEG images or UTF-8 TXT, LOG, MD and JSON files. Each message supports up to four files, with a limit of 2 MiB per file and 4 MiB in total. Each ticket has a 32 MiB attachment allowance. HTML, SVG, executables, PDFs, archives and private-key PEM files are not accepted. Image metadata is removed. Attachments follow the ticket's access permissions.

Follow replies and ticket status in Support and receive email notifications. Sending messages does not deduct support time. Support usage history shows the recorded work and hours used.

Organisation administrators can select **Add diagnostic report**, review the report and confirm its attachment before sending. The report excludes secret files and certificate material; larger logs are omitted. Operators and read-only users cannot generate it. The separate downloadable ZIP diagnostic bundle remains available.
