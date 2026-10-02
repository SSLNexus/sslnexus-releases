# SSLNexus Client Server 1.0.9

- Microsoft AD CS certificate enrollment and renewal through CES HTTPS, configurable per deployment target.
- Persistent CA request tracking handles manual approval and restart recovery. Uncertain submissions pause for explicit reconciliation.
- Outbound Nexus-to-Nexus lifecycle orchestration lets an MSP request issuance, renewal and deployment through a customer’s local SSLNexus engine.
- Customer controls include approved certificates, domain scope, operation approval and independent MSP suspension. CA and deployment credentials remain local.
- Relay-only customers cannot use AD CS or automated customer-local deployment through Relay. These features require an appropriately licensed customer Client Server and a supported deployment target.

The AD CS connector currently supports CES Username/Password authentication. Kerberos-only CES, certificate-authenticated CES and AD CS revocation are not included. Qualify enrollment, approval, renewal and deployment against your environment before adopting this connector for production workloads.

## Verify Your Download

SSLNexus release signing fingerprint:

`74BF4A349C301928FC648E143D8BF961F5457F79`

Confirm this fingerprint through the official SSLNexus website before trusting the downloaded public key. Download SSLNexus-Release-Signing.asc, SHA256SUMS, SHA256SUMS.asc and the signature for your selected package.

```bash
gpg --show-keys --fingerprint SSLNexus-Release-Signing.asc
gpg --import SSLNexus-Release-Signing.asc
gpg --verify SHA256SUMS.asc SHA256SUMS
sha256sum --ignore-missing --strict -c SHA256SUMS
```

For Debian:

```bash
gpg --verify ssl-nexus_1.0.9_amd64.deb.asc ssl-nexus_1.0.9_amd64.deb
```

For Enterprise Linux 10, after confirming the public key fingerprint:

```bash
sudo rpmkeys --import SSLNexus-Release-Signing.asc
rpmkeys --checksig --verbose ssl-nexus-1.0.9-1.el10.x86_64.rpm
```

DEB signatures are detached; dpkg does not automatically enforce their verification.
