# 3.0 Stable — Privacy and Network Data

**No ZTM Vanguard reporting or analytics pipeline is included in this release.** The app requires no I2PS login, private wallet keys, recovery phrases or passwords.

Data stored on the computer may include hardware inventory, CPU/RAM/thermal observations, local worker ID, measured hashrate, accepted/rejected shares, thread configurations, report evidence and the **public** wallet receiving address.

Expected external services are the chosen mining pool (work/shares and public wallet + rig identifier), official GitHub-hosted verified XMRig release downloads, Ubuntu APT repositories, and optional official wallet resources opened by the user. Pool traffic can be non-TLS. A worker ID may enable correlation by the pool. Reports remain local unless the user exports or shares them. Inspect and remove identifiers before posting reports publicly.