# SSLNexus Client Server 1.0.7

Release date: 29 September 2026

## Overview

SSLNexus 1.0.7 expands first-party certificate deployment coverage and consolidates discovery into a clearer operator workflow while preserving the existing 1.0.x installation, upgrade and certificate-custody model.

## New certificate integrations

- Added first-party Apache Tomcat / Java certificate deployment for Linux targets using the established target-bound deployment workflow.
- Added Microsoft Exchange certificate lifecycle support using Windows remote management and Exchange-native certificate import/service binding.
- Added Fortinet FortiGate certificate deployment through its HTTPS API.
- Added Citrix ADC / NetScaler certificate deployment through NITRO.
- Added Kubernetes TLS Secret deployment through the Kubernetes API.
- Added HashiCorp Vault PKI as a native certificate authority connector while retaining Vault KV as a certificate destination.
- Added a Kemp LoadMaster adapter in **Lab** status. It is included for controlled qualification and is not represented as a production-qualified integration in this release.

## Discovery

- Added a dedicated Discovery page that separates verified-domain discovery from active network discovery.
- Domain Discovery now presents managed parent domains through a single dropdown workspace instead of rendering one card per domain.
- DNS TXT ownership verification is available directly from the Discovery workflow so administrators do not need to return to Organisation to complete verification.
- Verified-domain discovery can optionally restrict results to a CIDR boundary after name enumeration and DNS resolution. The CIDR is a result filter; it does not turn domain discovery into a subnet scan.
- Network Discovery exposes the existing active private-CIDR TLS scanner as a distinct workflow.
- Discovery and Organisation workflow cards now preserve their expanded/collapsed state across page re-renders.

## Windows target onboarding

- Improved the Windows target preparation guide with a complete PowerShell preparation block that can be copied directly from the dashboard.
- Improved automatic selection of the SSLNexus source address by preferring the Linux kernel route/source decision before falling back to interface enumeration.

## Compatibility and security model

- Existing deployment adapters continue to use the established SSLNexus certificate deployment engine rather than introducing a second automation engine.
- SSLNexus automation remains scoped to certificate lifecycle operations; the release does not introduce general-purpose server patching or configuration-management automation.
- Existing customer private-key custody expectations remain unchanged. Integrations that support target-side key generation retain keys within the customer-controlled target/infrastructure boundary.
- Existing 1.0.x native package upgrade paths are retained.

## Release verification

Production publication requires the qualified App1 release gate with exact Go 1.27.1 and `GOFIPS140=v1.0.0`, the complete Go/security test suite, CycloneDX SBOM generation and verification, finished DEB/RPM package verification, and the established install/upgrade/rollback smoke tests. Only artifacts that pass those checks are to be published.
