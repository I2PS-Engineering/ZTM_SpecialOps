# ZTM Special Ops 3.1 Stable — Build 3.1.2 release verification

This record applies to the **3.1.2 first public file-release candidates**, not any earlier version. It summarizes verified **static artifact integrity** and distinguishes those checks from real-hardware validation. The release must not be represented as public until the GitHub draft is actually published.

## Release archives

| Platform | GitHub draft asset name | SHA-256 (outer ZIP) |
|---|---|---|
| Linux Ubuntu Desktop x86-64 | `ZTM-Special-Ops-3.1.2-Linux.RELEASE.zip` | `fc3da76eab8c747f76bf3db9b6474cae8e9f71d835481e1d4c1186669cdc2744` |
| Intel macOS and Mac Apple Silicon | `ZTM-Special-Ops-3.1.2-macOS.RELEASE.zip` | `5584516a8b61f10342778bff5bec5b47fb924d6953e3b87e7dd9cab490d27bd6` |

Internal original entries as audited:

- Debian package `ZTM-Special-Ops-3.1-Stable_3.1.2_amd64.deb` SHA-256: `401c728c2d9db2bec127dccaca4a97c8d0645bb17414e7120535ac1d3a887fe8`.
- Signed macOS application nested archive `ZTM_Special_Ops_3.1.2_Stable.zip` SHA-256: `479607d55db474b5f5f3eed9e20dd71aca85e8c6844a21e0d687042f9981a947`.
- Both original ZIP CRC checks and internal SHA256SUMS.txt manifests passed. The signed macOS application archive was preserved byte-for-byte during external-documentation corrections.
- The Debian package was documentation-only repacked: exactly two installed documentation files differed, with **68 other payload entries**, Debian control archive, compiled modules, and executable files verified unchanged against the submitted prior package.

## Verification boundaries

These are **static** comparisons. They do not independently certify Apple notarization against Apple's current service, successful fresh installation on every supported host, continuous 24-hour mining qualification on every supported host, or every hardware-dependent security/thermal condition. Those require separate tests and evidence. Do not carry earlier-version automated test counts into 3.1.2 as though they were rerun.

## Permissions and disclosure

All users must authorize benchmark work in the application before it starts. The benchmark uses a development payout address, and personal mining remains locked until the same installation completes the qualified 24-hour baseline. Personal mining includes the separately scheduled I2PS contribution and XMRig's independent developer donation. The two release packages include version-specific [Terms](TERMS.md), [Privacy](PRIVACY.md), [License](LICENSE.md) and [Third-party Notices](THIRD_PARTY_NOTICES.md).

## Distribution boundary

This repository contains user-facing documentation and approved research artwork, not the proprietary engineering source tree or internal handoff archives. The Linux and macOS executable distributions are delivered only as the two official GitHub Release assets. The download ZIPs, Debian binaries and the macOS signed application must not be rebuilt as part of repository documentation cleanup.
