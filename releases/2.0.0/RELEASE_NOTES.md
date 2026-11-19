# SSLNexus Client Server 2.0.0 revision 1

Updated the HTTP server to fix a crash affecting HTTP/1 connections (GO-2026-6859).

## Automate certificate management

Open **API Access** in the Control Centre to create an expiring key for an estate. Choose which targets and operations the key can access. Management API v1 is available on every licence tier and uses the same certificate authorities, deployment targets and permissions as the Control Centre. Use it to list certificates, request issuance or renewal, approve a renewal, deploy a certificate and follow the resulting job. The installed API guide, OpenAPI specification and curl, PowerShell and Ansible examples are in `/usr/share/doc/ssl-nexus/`.

## Issue and renew with DNS-01

Under **Organisations**, select **Configure DNS-01** beside a verified parent domain. Connect Cloudflare, Amazon Route 53, OVHcloud, PowerDNS Authoritative, ClouDNS or Infoblox NIOS. For an Indusface zone, delegate its challenge name by CNAME to a connected zone.

For a public certificate, select **Let’s Encrypt → ACME directory → Production** on the deployment target and choose **DNS-01** on the certificate. SSLNexus publishes the challenge TXT value, waits for authoritative DNS, and removes its value after validation. The same connection supports renewals and wildcard certificates. To replace an existing diagnostic certificate, save the Production directory on its target and choose **Request new certificate**.

## Plan renewals as certificate lifetimes change

In **Certificates → Renewal policy**, choose a fixed number of days or a percentage of the certificate’s lifetime remaining. Percentage-based policies adapt to the lifetime of each newly issued certificate. **Overview → Certificate validity notices** shows announced lifetime changes, affected policies and the projected time available to recover if renewal fails.

## Windows deployment and offline Enterprise licensing

SSLNexus supports certificate deployment to PRTG on Windows. Offline Enterprise licensing is available by quote. Administrators can upload a signed licence file, receive reminders from 30 days before expiry and retain management through seven days of grace. Installed certificates remain in place after licence expiry. High-availability replicas start in standby. Fence the former active server before promoting a replica. See `OFFLINE-ENTERPRISE.md` in the installed documentation for configuration and recovery.
