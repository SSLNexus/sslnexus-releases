# SSLNexus Client Server 1.0.8

Released 1 October 2026. Linux Client Server; Debian and RHEL-family binary packages.

## Customer-owned certificate authority

MSPs can complete issuance, deployment, verification, renewal and supported revocation through a customer-owned SSLNexus Client Server or Customer Relay. Customer CA and DNS credentials remain local. Each MSP connection has its own domain scope, approval rules and activation controls. The requester retains its certificate private key.

External MSPs now opens correctly from the sidebar and About page. Administrators can pair an external MSP, configure a profile using an existing local CA configuration, inspect requests and control its channel. MSP invitations have a copy button and remain valid for 24 hours, single-use. Existing invitations retain their original expiry.

## Lifecycle reliability

Pending issuance and renewal preserve the original CSR and job identity through restart and customer approval. Returned certificates rejoin normal deployment, verification and renewal scheduling. Deployment recovery reuses the issued certificate. Unknown CA outcomes require reconciliation of the original operation. CA configurations are encrypted and pinned to the operation.

## Upgrade

Use the existing DEB/RPM upgrade flow. Retain the complete Client state, including /var/lib/ssl-nexus/customer-federation and /var/lib/ssl-nexus/federation. Pairing requires Licence Authority 0.16.50 or a federation-compatible build. Ensure the advertised MSP listener port is allowed through the MSP firewall. Customer connections are outbound.
