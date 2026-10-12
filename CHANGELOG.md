# SSLNexus Client Server 1.0.11

12 October 2026

- Reissue retained, valid certificates without contacting the certificate authority or consuming issuance limits or charges. Existing keys, serial numbers and expiry dates are preserved. Request new certificate remains a separate action.
- Keep a versioned certificate store for recovery and redeployment. Optional local keystore encryption includes automatic unlock and migration for existing material.
- Preserve the selected nginx or Apache engine and shared-site configuration. Validate configuration before reload; Reissue does not install or start another web server.
- Improve retained-key reuse for Tomcat, PaperCut and Launchpad, and preserve the recorded PaperCut keystore location across year changes.
- Select the intended IIS site and preserve supported existing bindings without a host-wide IIS reset.
- Group discovery observations by certificate fingerprint and exclude loopback-only names and unrelated default certificates. Remove unwanted inventory entries while retaining deployed files and issuance history.
- Strengthen session invalidation, password-change enforcement, multi-factor attempt limits, diagnostic redaction and encrypted audit forwarding.
- Use a short-lived account handoff code without transferring the local password verifier.

Back up configuration, database, certificate artifacts and protected unlock material before upgrading. Existing plaintext material remains unchanged until optional encryption is enabled or migrated. Protect the unlock key and backups together; automatic local unlock does not protect a host under an attacker's full control. Audit collectors using HTTP must be reconfigured for HTTPS or TLS syslog.
