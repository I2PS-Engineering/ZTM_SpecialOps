# 3.0 Stable — Terms and CPU-Work Disclosure

## Authorization and duration
The GUI requires one checkbox, **“I authorize the 24-hour benchmark.”** A confirmation explains developer-directed payouts, heat, electricity, and sustained CPU work before the user initiates mining. The benchmark targets 24 hours of qualified online RandomX work. Connection interruptions can extend wall-clock duration. Installation alone does not start mining.

## Benchmark payouts
The baseline 24-hour benchmark mines to a **fixed I2PS development receiving address**, except for XMRig's independently administered upstream 1% developer donation. The user wallet is **not** used during this stage.



## Personal Mining
Wallet entry and Start/Stop Mining share one tab. Personal mining unlocks only after a qualifying baseline, and its wallet controls lock while benchmark work runs. It uses a **public Monero address**, never wallet seed phrases, private keys or passwords. Personal mining schedules 60 seconds of I2PS development mining per 6,000 seconds (1% of runtime), plus XMRig's built-in upstream 1% donation. Actual accepted-share and payout proportions may differ.

## Power, heat and interruption
Sustained CPU work consumes electricity, produces heat and may increase fan usage or wear. Operate only on hardware you own or have permission to use. STOP is available for benchmark and STOP MINING for the personal-mining tab. Early-stop reports are not qualified completed benchmarks. Thermal safeguards reduce but cannot eliminate hardware risk. Administrator authorization may be requested for certain system settings.

## Network and data
The configured mining pool receives wallet and worker/rig identifiers. Depending on configuration, mining traffic may be unencrypted. Setup may reach Ubuntu repositories and official XMRig downloads; official wallet sites open on user action. No Vanguard analytics reporting pipeline ships in 3.0 Stable; measured reports are saved locally. Consult [Privacy](PRIVACY.md).

## Legal
I2PS-owned application materials are proprietary. See [License](LICENSE.md); third-party licenses remain applicable. No mining return, throughput, or uninterrupted operation is guaranteed.