# SSLNexus 1.0.5 Release Notes

Release date: 25 September 2026

SSLNexus 1.0.5 is a retained production release focused on multi-tenant MSP operation, appliance certificate workflows, Internal PKI improvements, operational visibility and native Linux package distribution.

## Highlights

- Expanded multi-tenant MSP management and organisation isolation.
- Added and refined first-party certificate workflows for network and infrastructure platforms including F5 BIG-IP, VMware vCenter and PAN-OS.
- Expanded Internal PKI capabilities and access controls.
- Improved operational health, notification routing, backup/restore workflows and certificate-capacity handling.
- Added native DEB and RPM release distribution with immutable versioned package records and version-aware upgrade notifications.
- Improved parent-domain discovery and provider-neutral certificate adoption workflows.
- Improved Vendor Portal lifecycle, issuance recovery, support and account-management behavior.
- Added source-control integration for Deployment Plugins while keeping plugin secret values in the local protected secret store.

## Compatibility

1.0.5 is retained for rollback and compatibility scenarios. Administrators upgrading to a later release should keep a current backup and follow the normal native-package upgrade process.

## Release assets

- `ssl-nexus_1.0.5_amd64.deb`
- `ssl-nexus-1.0.5-1.el10.x86_64.rpm`
- `ssl-nexus-1.0.5.cdx.json`
- `SHA256SUMS`

Always verify package checksums before installation.
