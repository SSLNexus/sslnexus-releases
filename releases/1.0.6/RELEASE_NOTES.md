# SSLNexus 1.0.6 Release Notes

Release date: 28 September 2026

SSLNexus 1.0.6 is a production update focused on visibility, trust management, security hardening and administrative usability while preserving the established 1.0.x upgrade path.

## Highlights
- Dependency & Impact shows known relationships around certificates, deployment targets, applications and trust stores before operational changes are made.
- Trust Store Management provides organisation-scoped public root/intermediate bundles, discovery, drift visibility and controlled provisioning for supported Linux and Windows targets.
- Certificate issuance-history charts make daily issuance trends easier to understand and link back to detailed audit records.
- Global dashboard search can navigate directly to matching sections.
- The About page now presents release/build information, system details, effective licence and certificate-capacity information in one place.

## Security and privacy
- Vendor Portal private keys are generated locally in the user's browser for CSR creation. SSLNexus receives the CSR, not the private key.
- Team invitations use single-use password-setup links instead of emailing temporary passwords.
- Login protection now includes source-aware throttling and a dedicated repeated-login / possible brute-force event after the alert threshold is reached.
- Access Logs distinguish Client Server administrator activity from Vendor Portal activity.
- Self-hosted GitLab configuration rejects unsafe local, loopback and link-local destinations by default.
- The public Private Key Policy documents the product's key-custody expectations.

## Reporting and usability
- PDF reports have improved SSLNexus branding, layout, wrapping and pagination.
- Dependency & Impact has improved dark-mode contrast.
- Password visibility controls are available for user password fields without exposing API tokens, keys or application secrets.
- Account linking requires the invited account to accept before it joins the organisation; the purchasing account retains ownership and billing authority.

## Compatibility
- Existing CA changes continue to affect future issuance and renewal; an already-valid certificate is not automatically revoked merely because the configured CA changes.
- Existing customer private-key custody remains within customer-controlled infrastructure.
- The normal native package upgrade path from 1.0.5 is retained.

## Release verification
The published DEB and RPM were produced from the qualified SSLNexus 1.0.6 source with Go 1.27.1 and the Go Cryptographic Module v1.0.0 selected for the release build. Both finished packages were verified against their embedded CycloneDX SBOMs before publication.
