# ZTM Special Ops 3.1 Stable — Terms and required CPU-work disclosure (Build 3.1.2)

The sections below reproduce the corresponding documents supplied with the **verified official 3.1.2 release archives**. For the actual installed package, the included document is authoritative. Platform differences are intentional; I2PS Engineering has not combined or modified the original terms.

## Linux — verbatim release document

# ZTM Special Ops 3.1 Stable — Terms and Required CPU-Work Disclosure (Linux)

**Benchmark isolation:** for the whole benchmark (about 24 qualified online hours), leave the computer dedicated to ZTM. Do not use other applications, start competing CPU or GPU workloads, or let the system sleep. Background activity changes CPU load, heat, memory pressure and hashrate and makes the comparison unreliable. Qualified online time can take longer than 24 hours of wall time when there are interruptions. This is a requirement of the method, not a claim that ZTM can prevent all interference.

## 1. Explicit authorization

Before START BENCHMARK, the app requires **I authorize the 24-hour benchmark.** A separate confirmation explains the payout destination, XMRig's upstream donation, electricity use and sustained CPU heat. Nothing mines on installation.

## 2. The 24-hour benchmark

The app runs real RandomX jobs against a mining pool, measures CPU, memory and placement (affinity) configurations and runs the selected configuration for the rest of the qualified online period. The run targets 24 hours of valid online work; network interruptions can lengthen the elapsed time. **Pool rewards during the entire benchmark go to the fixed I2PS development receiving address**, apart from XMRig's built-in upstream donation. They are not paid to the user's wallet.

## 3. After qualification

After a completed, verified 24-hour benchmark, the final results and personal mining are available. START BENCHMARK remains available for a fresh 24-hour run.

## 4. Personal Mining

After qualification, the Mining tab accepts the user's **public Monero receiving address** and links to the official wallet resources. It never asks for recovery phrases or private keys. Personal mining devotes an intended 60 seconds per 6 000 seconds (1 % of scheduled runtime) to the fixed I2PS address and otherwise mines to the user's address, with XMRig's separate upstream 1 % donation. Accepted shares and payouts can differ from runtime percentages. Personal mining and the benchmark never run at the same time.

## 5. Electricity, safety, STOP

CPU use can be continuous, produce heat, run fans, draw electricity and add wear. Users must watch their hardware and have permission to operate it. STOP is available during the benchmark and STOP MINING during personal mining. A stopped benchmark is recorded as incomplete and does not qualify. ZTM records CPU temperature where sensors expose it but does not stop on temperature; cooling and hardware condition remain the user's responsibility. Administrator authorization is requested for the privileged preparation.

## 6. Network and privacy

Pool traffic reveals the receiving address and a persistent worker identifier to the pool. Pool connections use TLS to `pool.hashvault.pro:443`. The app also contacts the Ubuntu package mirrors and GitHub for the official XMRig release. Reports are stored locally; ZTM sends no analytics. See [PRIVACY.md](PRIVACY.md).

## 7. License and third parties

The I2PS application is proprietary and free for the personal uses permitted by [LICENSE.md](LICENSE.md); resale, redistribution, modified builds and commercial deployment are prohibited without written authorization. XMRig is separately licensed under the GNU GPLv3. ZTM Special Ops does not guarantee mining revenue or hashrate improvements.

## 8. Mining unlock

Personal mining is locked until the same installation completes a genuinely qualified 24-hour benchmark. There is no bypass. The public receiving address, the terms consent, the I2PS 60 s / 6 000 s interval and XMRig's upstream donation always apply.

## macOS — verbatim release document

# ZTM Special Ops 3.1 Stable — Terms and Required CPU-Work Disclosure (macOS)

**Benchmark isolation:** for the whole benchmark (about 24 qualified online hours), leave the computer dedicated to ZTM. Do not use other applications, start competing CPU or GPU workloads, or let the system sleep. Background activity changes CPU load, heat, memory pressure and hashrate and makes the comparison unreliable. Qualified online time can take longer than 24 hours of wall time when there are interruptions. This is a requirement of the method, not a claim that ZTM can prevent all interference.

## 1. Explicit authorization

Before START BENCHMARK, the app requires **I authorize the 24-hour benchmark.** A separate confirmation explains the payout destination, XMRig's upstream donation, electricity use and sustained CPU heat. Nothing mines on installation.

## 2. The 24-hour benchmark

The app runs real RandomX jobs against a mining pool, measures thread-count configurations on Intel Macs (Apple Silicon runs XMRig's standard automatic configuration) and runs the selected configuration for the rest of the qualified online period. The run targets 24 hours of valid online work; network interruptions can lengthen the elapsed time. **Pool rewards during the entire benchmark go to the fixed I2PS development receiving address**, apart from XMRig's built-in upstream donation. They are not paid to the user's wallet.

## 3. After qualification

After a completed, verified 24-hour benchmark, the final results and personal mining are available. START BENCHMARK remains available for a fresh 24-hour run.

## 4. Personal Mining

After qualification, the Mining tab accepts the user's **public Monero receiving address** and links to the official wallet resources. It never asks for recovery phrases or private keys. Personal mining devotes an intended 60 seconds per 6 000 seconds (1 % of scheduled runtime) to the fixed I2PS address and otherwise mines to the user's address, with XMRig's separate upstream 1 % donation. Accepted shares and payouts can differ from runtime percentages. Personal mining and the benchmark never run at the same time.

## 5. Electricity, safety, STOP

CPU use can be continuous, produce heat, run fans, draw electricity and add wear. Users must watch their hardware and have permission to operate it. STOP is available during the benchmark and STOP MINING during personal mining. A stopped benchmark is recorded as incomplete and does not qualify. The benchmark and personal mining stop on critical macOS thermal pressure (the benchmark also on serious pressure lasting 30 seconds); cooling and hardware condition remain the user's responsibility.

## 6. Network and privacy

Pool traffic reveals the receiving address and a persistent worker identifier to the pool. Pool connections use TLS to `pool.hashvault.pro:443`. The app also contacts Python.org (only if you accept the Python installation) and GitHub for the official XMRig release. Reports are stored locally; ZTM sends no analytics. See [PRIVACY.md](PRIVACY.md).

## 7. License and third parties

The I2PS application is proprietary and free for the personal uses permitted by [LICENSE.md](LICENSE.md); resale, redistribution, modified builds and commercial deployment are prohibited without written authorization. XMRig is separately licensed under the GNU GPLv3. ZTM Special Ops does not guarantee mining revenue or hashrate improvements.

## 8. Mining unlock

Personal mining is locked until the same installation completes a genuinely qualified 24-hour benchmark. There is no bypass. The public receiving address, the terms consent, the I2PS 60 s / 6 000 s interval and XMRig's upstream donation always apply.
