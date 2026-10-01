# SSLNexus Customer Relay 1.0.0

Released 1 October 2026. Available for Linux amd64 and Windows amd64.

Customer Relay enables MSP certificate automation where the customer does not operate SSLNexus and keeps CA credentials and DNS authority within its own infrastructure. Independent MSP channels use outbound TLS/mTLS connections, scoped customer policies and optional approval for every issuance or renewal. Relay returns certificates to the requesting SSLNexus Client for deployment, verification and subsequent renewal.

## Included

Email-based administrator accounts, initial super-admin setup, account security and email settings; themed light/dark management portal with account controls, version footer and certificate activity overview; CA connectors using the Client adapters; durable enrollment identities and lifecycle history; activation, suspension and offboarding per MSP; supported revocation and explicit reconciliation of unknown CA outcomes.

Pairing prompts link directly to Customer Profiles and select the paired MSP. Channels without policy show Configure Policy before activation. Private service logs identify pairing failure stages without recording invitation secrets.

## Requirements

MSP Client Server 1.0.8 and Licence Authority 0.16.50, outbound access to the dedicated MSP federation listener and selected CA, and local DNS/challenge access as required by the CA. Invitations are valid for 24 hours and single-use. Management and ACME HTTP-01 validation have separate inbound requirements.

See USER_GUIDE.md for installation, policy setup, daily operation and backups. Preserve existing Relay state during upgrades. CA availability and validation requirements remain vendor-specific.


## Native Linux packages

Debian: sudo apt install ./sslnexus-authority-relay_1.0.0_amd64.deb. RHEL/AlmaLinux: sudo dnf install ./sslnexus-authority-relay-1.0.0-1.el10.x86_64.rpm (use the exact supplied filename). Then run sudo sslnexus-relay-setup to accept the EULA and configure the management endpoint. Supply SSL_NEXUS_RELAY_DOMAIN and optional local TLS certificate/key environment values as described above. Initial package installation does not start an unconfigured service. Package upgrades restart an already-running Relay while retaining state, configuration and identities. Uninstall stops the service but retains customer state and configuration; remove them separately only when intentionally decommissioning.

Windows distribution includes the executable and a ZIP containing Install.ps1, documentation and checksums. Use the complete ZIP for initial Windows service installation.
