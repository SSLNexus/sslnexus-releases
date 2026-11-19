# SSLNexus Client Server

Read the [2.0.0 release notes](https://github.com/SSLNexus/sslnexus-releases/releases/tag/v2.0.0) for version details. The packages include the host maintenance guide in `/usr/share/doc/ssl-nexus/HOST_MAINTENANCE.md`.

SSLNexus is a self-hosted certificate management platform for issuing, deploying, renewing, discovering and managing certificates across Linux, Windows and application environments. Certificate keys and CA credentials remain within customer infrastructure.

## Downloads

Download the package for your Linux server from the [2.0.0 release](https://github.com/SSLNexus/sslnexus-releases/releases/tag/v2.0.0).

| Server | Package |
| --- | --- |
| Debian 13, amd64 | `ssl-nexus_2.0.0-1_amd64.deb` |
| AlmaLinux 10, x86_64 | `ssl-nexus-2.0.0-1.x86_64.rpm` |

The Client Server runs on Linux and manages supported Windows targets remotely. Releases include checksums, OpenPGP signatures and a CycloneDX software bill of materials. Verify the signing-key fingerprint through a trusted SSLNexus channel before trusting a downloaded key.

## Changes in 2.0.0 revision 1

- Automate certificate issuance, renewal, replacement, deployment and supported revocations through Management API v1 on every licence tier. Limit each access key by estate, target, permission and expiry.
- Issue and renew Let’s Encrypt certificates, including wildcards, with DNS-01. Connect Cloudflare, Amazon Route 53, OVHcloud, PowerDNS Authoritative, ClouDNS or Infoblox NIOS. Indusface zones can delegate validation by CNAME to a connected zone.
- Choose when a certificate renews using either the percentage of its lifetime remaining or a fixed number of days before expiry.
- See which renewal policies may be affected by shorter public certificate lifetimes and how much time each policy allows for recovery.
- Deploy certificates to PRTG on Windows and use a signed licence file for eligible offline Enterprise installations.

## Install or upgrade

Back up SSLNexus configuration, database and certificate material before upgrading. Include the matching unlock key if local keystore encryption is enabled. Review the release notes before installation.

Debian 13:

```bash
sudo apt install ./ssl-nexus_2.0.0-1_amd64.deb
```

AlmaLinux 10:

```bash
sudo dnf install ./ssl-nexus-2.0.0-1.x86_64.rpm
```

Upgrade in place without uninstalling the existing package. Allow a maintenance window: upgrade duration depends on database size and backup time.

After installation or upgrade:

```bash
sudo ssl-nexus-admin preflight
sudo ssl-nexus-admin security verify --json
```

Confirm **2.0.0 revision 1** in the dashboard. See the [documentation](https://sslnexus.com/docs/) and the [SSLNexus website](https://sslnexus.com) for setup and supported integrations. Installation and upgrade guides are also included with the packages.

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

## Application package platform scope

The package build targets are Debian 13 amd64 and AlmaLinux 10 x86_64. The published EL10 RPM is not an EL8 or EL9 package. Ubuntu, Debian 12 and other RHEL-compatible systems are outside the supported package platforms. Host-maintenance distribution support is a separate capability and does not imply package availability. Operations upgrades require an explicit match in the signed release manifest. The release manifest lists eligible systems.

Before trusting a new signing key, compare its full fingerprint with an independently trusted copy. Open the official GitHub release repository directly at https://github.com/SSLNexus/sslnexus-releases and check the publisher's signing information. If the fingerprint cannot be independently confirmed there or through an established SSLNexus support contact, stop. Downloading a package, key and matching fingerprint from the same website does not independently authenticate the publisher.
