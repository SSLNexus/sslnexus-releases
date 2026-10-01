# Customer Relay 1.0.0 user guide

## Choose the customer connection

Use External MSPs on an existing customer SSLNexus Client Server. Install Customer Relay when the customer does not operate SSLNexus. Both paths preserve customer control of CA/DNS credentials and use outbound connections to the MSP.

## Installation and initial account

Linux: extract the binary package, review EULA.md, then run sudo ./install.sh. Set SSL_NEXUS_RELAY_DOMAIN to the intended management hostname. To supply a trusted management certificate set SSL_NEXUS_RELAY_TLS_CERT and SSL_NEXUS_RELAY_TLS_KEY to existing local files. The default management certificate is self-signed; this is separate from the pinned MSP federation trust.

Windows: extract the Windows binary package, review EULA.md and run Install.ps1 from an administrator PowerShell session. Follow its hostname and EULA prompts. Complete the printed setup link once to create the initial named super admin. Use normal email/password login afterwards. Configure account email settings for invitations and password recovery. Restrict management access to the appropriate network.

## Pair, configure and activate

The MSP enables its MSP feature, selects the customer estate and creates an invitation. Copy the complete invitation and paste it into Vendor Channels > Pair Another MSP. Invitations last 24 hours and are single-use; obtain a fresh one after expiry.

Click Configure Customer Policy in the pairing prompt or Configure Policy on the channel. The selected MSP is carried into Customer Profiles. Configure a local CA connector first if none exists, then select it in the profile. Supply permitted domains, maximum SANs, validity limits and trust chain as appropriate. Approval defaults to required. Configure wildcard and revocation permission explicitly. Save the profile and return to Vendor Channels to Activate. Pairing alone does not grant certificate authority.

## Approvals and lifecycle

Review Approvals and inspect the CSR before approving or rejecting. The Relay processes the original CSR and CA order; certificates return to the MSP Client for deployment and verification. Renewals use the same customer policy and approval rules. Private keys are retained by their original infrastructure owner; CA/DNS credentials remain local to the customer authority.

Suspend pauses one MSP independently. Revoke Channel offboards that MSP and is distinct from certificate revocation. Certificate revocation requires connector support and profile permission. Unknown CA outcomes stop until checked with the CA and reconciled against the original operation; do not create another order to resolve uncertainty.

## Connectivity and errors

The MSP must allow inbound TCP on its advertised federation listener; Relay requires outbound access to that listener and the CA. Use direct TLS or TCP pass-through to preserve the federation identity and mTLS. Management HTTPS and any ACME HTTP-01 challenge endpoint are separate routes. The federation CA in an invitation is pinned; a self-signed warning in an ordinary OpenSSL check is not itself a pairing failure. Review the Relay service journal for pairing stages and the Authority journal for assertion rejection stages. Do not share invitation tokens or credential-bearing requests.

## Backups and upgrades

Linux state: /var/lib/sslnexus-authority-relay. Windows state is the directory selected by the installer. Preserve the entire state directory, including database, encryption key, machine identities, connectors and request history. Back up state with the service stopped for a consistent copy and protect it as sensitive key material. Reinstalling binaries must retain state; do not reset enrollment identities while requests are pending.


## Native Linux packages

Debian: sudo apt install ./sslnexus-authority-relay_1.0.0_amd64.deb. RHEL/AlmaLinux: sudo dnf install ./sslnexus-authority-relay-1.0.0-1.el10.x86_64.rpm (use the exact supplied filename). Then run sudo sslnexus-relay-setup to accept the EULA and configure the management endpoint. Supply SSL_NEXUS_RELAY_DOMAIN and optional local TLS certificate/key environment values as described above. Initial package installation does not start an unconfigured service. Package upgrades restart an already-running Relay while retaining state, configuration and identities. Uninstall stops the service but retains customer state and configuration; remove them separately only when intentionally decommissioning.

Windows distribution includes the executable and a ZIP containing Install.ps1, documentation and checksums. Use the complete ZIP for initial Windows service installation.
