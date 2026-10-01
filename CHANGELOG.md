# SSLNexus Client Server 1.0.8

Released 1 October 2026. Linux Client Server; Debian and RHEL-family binary packages.

## Customer-owned certificate authority

MSPs can complete issuance, deployment, verification, renewal and supported revocation through a customer-owned SSLNexus Client Server or Customer Relay. Customer CA and DNS credentials remain local. Each MSP connection has its own domain scope, approval rules and activation controls. The requester retains its certificate private key.

External MSPs now opens correctly from the sidebar and About page. Administrators can pair an external MSP, configure a profile using an existing local CA configuration, inspect requests and control its channel. MSP invitations have a copy button and remain valid for 24 hours, single-use. Existing invitations retain their original expiry.

## Lifecycle reliability

Pending issuance and renewal preserve the original CSR and job identity through restart and customer approval. Returned certificates rejoin normal deployment, verification and renewal scheduling. Deployment recovery reuses the issued certificate. Unknown CA outcomes require reconciliation of the original operation. CA configurations are encrypted and pinned to the operation.

## Upgrade

Use the existing DEB/RPM upgrade flow. Retain the complete Client state, including /var/lib/ssl-nexus/customer-federation and /var/lib/ssl-nexus/federation. Pairing requires Licence Authority 0.16.50 or a federation-compatible build. Ensure the advertised MSP listener port is allowed through the MSP firewall. Customer connections are outbound.

---

# SSLNexus changelog

## 1.0.7 — 2026-09-29

### Certificate integrations
- Added first-party Apache Tomcat / Java, Microsoft Exchange, Fortinet FortiGate, Citrix ADC / NetScaler and Kubernetes TLS Secret deployment adapters.
- Added HashiCorp Vault PKI as a native CA connector while retaining Vault KV as a certificate destination.
- Added Kemp LoadMaster as a Lab-status adapter pending representative appliance qualification.

### Discovery and administration
- Added a dedicated Discovery page separating verified-domain enumeration from active private-CIDR Network Discovery.
- Added a single managed-domain dropdown workspace with in-place DNS TXT ownership verification.
- Added optional CIDR filtering for verified-domain discovery after enumeration and DNS resolution; the CIDR remains a filter rather than a subnet scan.
- Exposed the existing active private-CIDR TLS scanner as Network Discovery.
- Preserved expanded/collapsed workflow-card state across Discovery and Organisation re-renders.

### Windows onboarding
- Added the complete Windows WinRM preparation PowerShell directly to the target guide.
- Improved automatic SSLNexus source-address selection by preferring the Linux kernel routing decision before interface-enumeration fallback.

### Compatibility
- Preserved the existing certificate deployment engine, target-bound CA model, 1.0.x upgrade path and customer-controlled private-key custody model.
- General-purpose patching and unrelated configuration-management automation remain outside the SSLNexus execution scope.

- Added a dedicated Discovery surface separating verified-domain enumeration from active private-CIDR Network Discovery; verified domains can optionally filter discovered names by a CIDR boundary without scanning that range.
# Changelog

## 1.0.7 packaging correction — 29 September 2026

- Added native package Epoch 1 to DEB/RPM metadata so clean public 1.0.x releases upgrade earlier internal/development package versions rather than being classified as downgrades.
- Corrected 1.0.7 native package revision to 2.
- Product/runtime version remains 1.0.7.
- Fixed parent-domain subdomain discovery against current Subfinder releases by removing the obsolete `-max-results` argument; discovery now records the engines that actually succeeded and surfaces partial-source warnings.

## R15 PostgreSQL Phase 2.3.2 — installer HBA parser hotfix

- Corrects the embedded Python used by `scripts/provision-postgres.sh` to construct the managed loopback SCRAM `pg_hba.conf` block.
- No runtime Go code, schema, licensing, capacity-reconciliation or service behaviour changes.
- Interrupted Phase 2.3.1 installs can rerun the normal installer safely.


## 1.0.5 R15 — PostgreSQL Phase 2.3 / capacity reconciliation hardening

- Discovery-only inventory no longer consumes finite certificate capacity.
- Capacity reconciliation processes the full managed estate and reports per-record issues instead of stopping at the first failure.
- Pending allocations remain pending until certificate material exists; successful licence activation/refresh is no longer turned into an error by a local reconciliation warning.
- Failed never-issued reservation releases are persisted and retried automatically on later Authority checks.


## 1.0.5 R15 — PostgreSQL Phase 2.1 / Authority certificate capacity

- Completed PostgreSQL-canonical persistence for scaling-sensitive client-server control state, including report definitions/history in addition to certificates/jobs/schedules/policies/events, MSP tenancy, vendor/admin state, deployment targets and distribution bindings.
- Removed local no-licence-to-Free fallback. Free is Authority-issued and fail-closed.
- Generalised certificate capacity accounting across every finite Authority licence: Free 5, Starter 25 and Business 200 currently use reserve → commit → pending-only release; Enterprise/current Trial remain unlimited.
- Renewal on any finite certificate ceiling requires a committed Authority allocation; issued-but-uncommitted records cannot be reissued to recycle capacity, and existing estates are reconciled after activation/refresh and tier downgrade.
- MSP Trial/explicit-entitlement behavior and explicit-only Support entitlement behavior are unchanged.

## 1.0.5 R15 MSP activation workflow - 2026-09-22

- Added self-service MSP entitlement request controls to MSP Hub and Product licence settings.
- Kept Licence Authority authoritative; the client never flips MSP locally.
- Preserved explicit Authority MSP grants and client-estate limits during Trial without making MSP implicit.
- Added sanitized compatibility handling for older Licence Authority builds without the entitlement-request endpoint.


## 1.0.5 R15 usability refresh

- Sanitized/retried transient gateway errors in Advanced Alert Routing.
- Added remembered per-target remote backup locations and dropdown-based restore discovery.
- Restored local Vendor Portal launch and themed Vendor/Windows setup guides.
- Exposed the MSP Hub Enterprise add-on in the Trial licence table without granting the entitlement.

# Changelog

## 1.0.5 R15 - MSP multi-tenant hub - 2026-09-21

- Added Enterprise + `msp` entitlement multi-tenant management while retaining the MSP organisation as its own internal certificate estate.
- Added isolated client estates, portfolio health, customer suspension/reactivation and a server-validated estate selector.
- Added explicit per-client staff assignment for Operators, Network Operators and Read-only identities.
- Kept engine-wide licence/settings/notifications/operations/backups/plugins/connectors/Internal PKI controls Hub-only.
- Added estate-scoped certificate artifacts, immutable repository ownership and cross-organisation target-ID collision protection.
- Added safe entitlement-loss recovery that preserves customer data and allows a Return to MSP Hub path.
- Removed the legacy `msp` tier shortcut: MSP is now exclusively an Enterprise feature entitlement.
- Replaced only the right two-thirds login visual with the locked Zero-Trust Vendor Identity Management artwork; existing login form and footer remain unchanged.

## 1.0.5 R14 - Operations UI and email reporting refresh - 2026-09-21

- Simplified Operations & health persistence status, hide unavailable database-pool metrics and moved the manual refresh action into System health.
- Added 12-hour local/UTC health timestamps and coherent installed version/revision/release-date display.
- Changed the no-update operator message to reference the License Server rather than the underlying release-feed implementation.
- Added coloured Overview estate/target-health charts.
- Reworked HTML email into a fixed Master Shell with system logo/environment header, UTC/server/settings footer and server-controlled Action Alert, Summary Digest and Vendor / External Comm archetypes.
- Added coloured digest/report metric bars, top-10 alternating data tables and full-report CTAs.
- Kept subject/body copy editable while preventing raw HTML/CSS or archetype overrides from the notification policy.

## 1.0.5 R14 - Licence Authority 0.16 alignment - 2026-09-20

- Made `/v1/activate` and `/v1/check` authoritative for effective tier, limits, platforms, applications and granular feature flags while retaining the legacy Ed25519 token verifier.
- Added nullable authority-controlled grace, including explicit zero-grace support, and exposed the effective value through licence status.
- Changed the normal authority refresh to 15 minutes and made manual Refresh authority run an immediate effective licence check.
- Added independent feature enforcement for Internal PKI, Vendor Portal, Network Operator, Network appliances, Palo Alto, F5 BIG-IP, VMware vCenter, Deployment Plugins and Source Control.
- Preserved unknown authority feature keys for forward compatibility and stopped tier names from restoring explicitly disabled features.
- Added clear credential-rotation recovery without deleting existing state or retrying every minute.
- Added low-sensitivity feature-use telemetry and `product_revision: R14` to existing activation/check payloads.
- Kept installation-seat acceptance authority-side; the client does not use the legacy token activation-count claim for seat decisions.

## 1.0.5 Internal PKI R14 - 2026-09-20

- Expanded the Enterprise Internal ACME CA into a managed Internal PKI with EAB enrollment policies, account governance, private-certificate inventory, revocation and CRL publication.
- Added general/network PKI scopes and Network Operator object-level restrictions.
- Mirrored Internal PKI certificates into the normal SSLNexus certificate estate and audit/SIEM pipeline.
- Enforced Enterprise entitlement on the ACME protocol and Internal PKI management APIs.
- Added migration visibility for pre-EAB ACME accounts.

## v1.0.5 network appliances R13

- Added the Network Operator staff role with server-side read/write scope limited to network-appliance targets and their managed certificates.
- Added LDAP/Active Directory and OIDC group mapping for Network Operator identities.
- Added explicit **Test connection** management-API health checks for PAN-OS, F5 BIG-IP and VMware vCenter, independent of per-target **Test CA**.
- Added first-party F5 BIG-IP iControl REST target onboarding and certificate/key deployment to an explicitly configured Client SSL profile.
- Added first-party VMware vCenter Machine SSL two-stage CSR/deployment while retaining the private key inside vCenter.
- Added network-appliance administration, F5 BIG-IP and VMware vCenter operator documentation.

## SAP BI Launch Pad adapter R11

- Added first-party SAP BusinessObjects BI Launch Pad two-stage JKS/CSR deployment.
- Added dynamic discovery of `server.xml`, Tomcat service and SAP JVM `keytool.exe`.
- Added rollback-aware Tomcat HTTPS connector activation for both modern and legacy connector syntax.

## 1.0.4 - 2026-09-19

- Added DNS-verified parent-domain discovery with Subfinder preference and Certificate Transparency fallback.
- Added HTTPS certificate observation from verified discovered names and provider-neutral adoption into registered deployment targets.
- Added HashiCorp Vault KV v2, AWS Secrets Manager and Azure Key Vault certificate destinations with per-certificate bindings.
- Added named Entra ID, Okta, Google Workspace and Generic OIDC SSO with signed ID-token/JWKS validation, staff role mapping and isolated Vendor Portal authorization.
- Preserved LDAP/Active Directory authentication and explicitly prevented Vendor SSO from self-provisioning assignments.

## 1.1.13 - 2026-09-18

- Moved certificate authority configuration from global Settings into each Deployment Target.
- Bound managed certificate issuance to the CA configured on its deployment target and reject contradictory CA overrides.
- Added encrypted per-target CA credentials and separate target CA health testing.
- Prevented credentials from one CA adapter being reused when a target changes adapter.
- Updated bulk reissue/migration to derive its CA from each target.
- Retained legacy global provider loading only for backward compatibility with existing issue-only certificates and vendor mappings.

## 1.1.12 - 2026-09-18

- Reordered the control-plane workflow so Deployment targets precede Certificates.
- Made target operating system selection explicit and filter applications by the selected platform instead of silently locking the selector to the default application.
- Enforced the documented full Enterprise-equivalent platform/application profile for active Trial licences.
- Fixed Linux bootstrap Copy with a secure Clipboard API path plus legacy selection/copy fallback.
- Made target connection tests report progress and results in the target row instead of losing feedback during a page re-render.
- Restructured Certificates into a clear managed lifecycle flow: CA request, optional deployment target, renewal automation, then estate/search.
- Replaced the free-text CA field with enabled configured CA adapters and clarified that certificate creation starts issuance/automation rather than importing an existing certificate.

## 1.1.11 - 2026-09-18

- Cache-bust embedded SSLNexus branding assets so browsers cannot retain older green-background logo files after upgrade.
- Reuse the exact public website v49 wordmark/icon assets without modification.

## 1.1.10 - 2026-09-18

- Restored the exact website v49 SSLNexus wordmarks in the client UI.
- Added representative icons to the left navigation.
- Replaced typed footer branding with the header wordmark and version text.

## 1.1.10 - 2026-09-18

- Normalise supplied SSLNexus light/dark branding assets to identical dimensions and remove the dark green backgrounds.
- Make Gmail OAuth redirect URL copying work with a non-Clipboard-API fallback.
- Warn when Gmail OAuth is being configured while the interface is still accessed by IP address and DNS/HTTPS should be configured first.

## 1.1.8 - 2026-09-18

- Makes Trial verification and activation a single authority-confirmed flow; the client no longer submits a second `/v1/activate` request after a verification code succeeds.
- Keeps the Trial token/state only after the authority confirms the Trial activation response.
- Adds the supplied SSLNexus light/dark wordmarks and icon assets to the control panel, favicon and footer.
- Tightens dark-mode contrast around near-black surfaces while retaining the SSLNexus green accent.

## 1.1.7 - 2026-09-18

- Added first-class Gmail OAuth using a Google OAuth Web client, refresh tokens and the Gmail API; no PEM/private key is required for this provider.
- Added the exact Gmail OAuth callback URL and Google Cloud setup guidance to Notifications.
- Kept Google Workspace service-account mail as a separate compatibility provider.
- Replaced the Trial browser prompts with a persistent in-dashboard verification flow that survives navigation in the same browser tab.
- Added end-to-end Trial verification-to-activation coverage so a verified code must result in an active Trial entitlement.

## 1.1.6 - 2026-09-18

- Fixed the Operational overview Reports button so it opens Reports through the main dashboard router.
- Added regression coverage for the Overview Reports navigation path.

## 1.1.4 - 2026-09-18

- Fixed the Reports button so it reliably opens the Reports page through the primary client router.
- Fixed stale licensing-authority connectivity in Settings by refreshing authority reachability when licence status is requested.

## 1.1.3 - 2026-09-18

- Fixed licensing-authority recovery after a temporary outage. SSLNexus now retries a disconnected authority every 60 seconds and returns to connected state automatically without a service restart.

## 1.1.1 — 2026-09-18

- Fixed control-centre navigation overflowing on shorter browser windows, which could hide Notifications and Settings.
- Fixed Linux deployment-target SSH setup commands rendering in an undersized field; setup commands now use the available width and a readable monospace layout.

# SSLNexus changelog

## 1.1.0

- Trials now require a verified customer email and remain tied to that customer across reinstalls, IP changes and authorised migrations.
- A trial still lasts exactly seven days; moving or reinstalling SSLNexus does not restart the clock.
- SSLNexus-managed certificates created under Trial or a paid licence now receive signed managed-state provenance. Copied or altered managed state cannot be silently adopted by another customer.
- Trial expiry now returns the installation directly to the permanent Free tier rather than leaving it read-only.
- Free remains available forever and does not require registration.

## 1.0.0

- Initial public SSLNexus release.
- Permanent Free tier, tier-based parent-domain limits, paid licensing, Vendor Portal, DEB/RPM packaging and the v1 administration experience.

## R12 - Palo Alto Networks PAN-OS

- Added first-party PAN-OS/Panorama certificate management through the HTTPS XML API.
- Added Panorama template and template-stack propagation with asynchronous commit/push verification.
- Added encrypted PAN-OS API credentials, certificate-object persistence and operator documentation.
- Simplified customer-facing built-in integration documentation so internal orchestration mechanics are not disclosed.

## R14 operations and notification hygiene refresh

- Added editable notification templates, event/severity/tag routing, persistent hourly/daily digests and per-channel test diagnostics.
- Added shared output redaction before job/log persistence and support-bundle generation.
- Added sanitized support bundles, configurable retention and automatic purge maintenance.
- Added target blackout windows with IANA timezone and server-side worker enforcement.
- Added Operations health for disk/repository/update state and restricted HTTPS update-manifest checking.
- Added focused regression coverage for the new operational controls.

## R15 MSP tab visibility maintenance

- Fixed MSP Hub sidebar discoverability for Trial and Enterprise administrators.
- Added a locked MSP Hub information view when the explicit MSP entitlement is not active.
- Preserved server-side Enterprise + `msp=true` enforcement for all managed-client operations.

## R15 MSP loader repair

- Fixes an administrator-dashboard boot regression in the MSP discoverability page caused by unescaped single quotes inside the embedded JavaScript HTML template.
- Adds a focused escaping regression assertion for the locked MSP page.
- Release validation now checks the actual embedded dashboard `<script>` blocks rather than a partial extraction.
## R15 maintenance — Licence Authority 0.16.13 MSP compatibility

- MSP refresh now reports the live Authority version and effective MSP entitlement.
- Authorities without `/v1/entitlements/request` fall back to `/v1/check` instead of dead-ending.
- Paid Enterprise MSP grants and client-estate limits are covered by compatibility tests.
- Trial denial from Authority 0.16.13 is surfaced explicitly and is never bypassed locally.
- Added `LICENCE_AUTHORITY_0.16.13_MSP_COMPATIBILITY.md` documenting the Authority follow-up required for explicit Trial MSP grants.

## R15 PostgreSQL Phase 2.3.1 — PostgreSQL loopback authentication

- Fixes source installation on PostgreSQL hosts whose broad loopback HBA policy uses Ident authentication.
- Adds an idempotent, database/role-specific SCRAM rule for the local `ssl_nexus` TCP DSN and preserves the original HBA file.
- Runtime client logic remains identical to Phase 2.3.

## 2026-09-27 — Access-log security visibility
- Activity & audit now records a distinct `security.login_bruteforce` access event on the fifth failed sign-in from the same source within a 15-minute window.
- Access Logs render that event as `Possible brute-force login attempt` while preserving the underlying failed-login rows for investigation.
- Public documentation now reflects browser-local Vendor Portal key generation, single-use team password setup, consent-based Client Area account merge, GitLab private-network restrictions, and the current sign-in protection model.
