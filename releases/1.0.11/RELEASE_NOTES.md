# SSLNexus Client Server 1.0.11

Adds a versioned certificate store and two distinct actions: **Reissue certificate** restores and deploys retained, valid material without any CA request, issuance rate-limit use or issuance charge; **Request new certificate** retains fresh CA issuance outside the renewal window, with applicable CA limits and charges. Reissue preserves serial, expiry and key and stops if suitable retained material is unavailable. Certificate history downloads, retry of initial issuance and CA changes remain separate.

Nginx deployment now checks configuration and occupied web ports before changing deployed material, reloads active nginx after successful validation, and blocks competing service starts. HTTP-01 cleanup skips reload if its configuration test fails. New HTTPS listeners reuse the shared endpoint protocol flags while preserving existing site configurations.
Adds an optional local artifact keystore to encrypt managed certificate private keys, saved PFX files and pending issuance records. Automatic unlock supports unattended renewal. Migration is an explicit offline operation; protect and back up the local unlock key together with the matching encrypted data.

Strengthens password recovery and session handling. Changing or resetting a password signs out existing sessions. Temporary passwords require a password change before access to administration or vendor operations. Multi-factor changes have an attempt limit.

Improves removal of sensitive values from diagnostics and support bundles. Audit forwarding requires HTTPS or TLS syslog and does not follow HTTP redirects. Existing collectors using HTTP must be reconfigured before upgrading.

Account links use a short-lived sign-in code without exporting the local password verifier. New portal accounts establish their own password through the portal password setup email. Existing portal passwords are unchanged.

Uses Go 1.27.2 and Go Cryptographic Module v1.0.0. The local keystore protects stored artifacts; protect the running server, unlock key and backups separately. Native backup archives and keys deployed to destination systems retain their existing protection requirements.

Reissue now excludes web-server package installation, SSL-module enablement and service startup. Certificate, target and verified nginx/Apache adapter identity must agree. Incorrect adapter selection is rejected before remote automation; Apache setup also checks for occupied web ports before installation or startup.

Discovery groups repeated observations of the same certificate across endpoints and lists those endpoints together. Loopback-only entries and unrelated default certificates from domain probes are excluded. Remove entry is available for discovered, imported and managed inventory records: it stops waiting automation while preserving deployed certificate files, configuration, retained material and issuance history. Removed certificate observations stay removed on subsequent scans; a newly renewed certificate can be discovered again.
