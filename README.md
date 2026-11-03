# ZTM Special Ops — 3.1 Stable · Build 3.1.2

**Built by I2PS Engineering.**  
**Different machines. Different capabilities. Same destination.**

A bicycle, a motocross bike, and a sport motorcycle do not have the same engine, gearing, tires, cooling or traction. You would not prepare all three for an uphill journey in exactly the same way. Nor should every processor be told to mine RandomX with the same thread count, initialization budget, memory assumptions and CPU placement.

Consider the mountain as the mining journey. The **engine** is the CPU; preparation is dataset initialization, Huge Pages and supported MSR optimizations; **grip** is the interaction of thread affinity, cache-sharing and memory efficiency; **road conditions** are thermals, power behavior and system contention; **endurance** is sustained, *measured* hashrate. The **slope** represents pool share difficulty (VarDiff): a steeper slope represents a higher-difficulty, rarer accepted share. That does **not** mean raising VarDiff by itself produces more blocks. Greater sustained hashrate increases attempts per second and hence the chance of finding hashes that meet a difficult target. A pool adjusts share difficulty largely to control share-submission frequency.

An old motorcycle may accelerate brilliantly in first gear, then lose speed climbing under heat or load. Likewise, a CPU's initial hashrate spike does not establish its sustained capability. **ZTM Special Ops seeks the best repeatable performance of *that machine***, rather than one impressive peak or a universal configuration. Modest recycled hardware deserves a measured configuration just as much as powerful hardware does.

![Motorcycle, sport motorcycle and cross/off-road motorcycle ascend increasingly difficult terrain](assets/figures/01-motorcycle-var-diff-whiteboard.png)

*Figure — The vehicles illustrate machine-specific preparation, not a guaranteed performance ranking. Higher pool share difficulty is not a shortcut to a higher block-discovery rate.*

ZTM Special Ops measures real RandomX CPU performance with supervised XMRig workloads, logs local hardware and measurement evidence, and uses **24 hours of qualified online work** to determine sustained behavior. After a valid, same-machine benchmark, the single **Mining** tab can unlock personal Monero mining.

**First public file release:** ZTM Special Ops **3.1 Stable**, build **3.1.2**, for **Ubuntu Desktop x86-64**, **Intel macOS**, and **Mac Apple Silicon**. The Linux and macOS packages are distributed separately. Proprietary I2PS application code is not open source; XMRig remains separately licensed under GPLv3.

> **Release assets:** The filenames below identify the supplied release candidates. Obtain them only through the official I2PS GitHub Releases page when I2PS publishes them; no publication is implied by this README. Confirm the ZIP SHA-256 through an independent trusted channel before installing.

| Platform | Official file name | Outer ZIP SHA-256 |
|---|---|---|
| Linux x86-64 | `ZTM-Special-Ops-3.1.2-Linux.RELEASE.zip` | `fc3da76eab8c747f76bf3db9b6474cae8e9f71d835481e1d4c1186669cdc2744` |
| macOS Intel / Apple Silicon | `ZTM-Special-Ops-3.1.2-macOS.RELEASE.zip` | `5584516a8b61f10342778bff5bec5b47fb924d6953e3b87e7dd9cab490d27bd6` |

## Contents

1. [Purpose and boundaries](#1-purpose-and-boundaries)
2. [Platform capabilities](#2-platform-capabilities)
3. [System requirements](#3-system-requirements)
4. [Installing the first release](#4-installing-the-first-release)
5. [Authorization and 24-hour benchmarking](#5-authorization-and-24-hour-benchmarking)
6. [Current engine selection and statistical validation](#6-current-engine-selection-and-statistical-validation)
7. [GUI, measurements and 15-minute charts](#7-gui-measurements-and-15-minute-charts)
8. [Qualified time, reports and Mining unlock](#8-qualified-time-reports-and-mining-unlock)
9. [Personal Mining and contributions](#9-personal-mining-and-contributions)
10. [Safety, STOP and failure handling](#10-safety-stop-and-failure-handling)
11. [Files, privacy and network behavior](#11-files-privacy-and-network-behavior)
12. [Approved mathematical research reference](#12-approved-mathematical-research-reference)
13. [Troubleshooting](#13-troubleshooting)
14. [Project boundaries and license](#14-project-boundaries-and-license)

---

## 1. Purpose and boundaries

ZTM Special Ops is a real-machine CPU benchmarking and local optimization application, not a CPU simulator or a promise of mining income. It measures the machine as it is: hardware topology, memory conditions, worker-count configuration, pool-connected RandomX hashrate and sustained performance. Observed results, unavailable sensors, configuration changes and interruption causes are recorded, not invented.

The benchmark spends **86,400 qualified online seconds** using real pool work. Benchmark rewards go to the disclosed fixed I2PS development receiving address, separately from XMRig's built-in upstream developer donation. Only after the local report passes the same-machine qualification checks does the Mining workflow become available for the user's public wallet address.

No mining starts on installation. The application requires explicit authorization and a second confirmation. It does not overclock hardware, guarantee full Huge Pages coverage, guarantee a hashrate improvement, or relay telemetry to ZTM Vanguard.

## 2. Platform capabilities

| Capability | Ubuntu Linux x86-64 | Intel macOS | Mac Apple Silicon |
|---|---|---|---|
| Hardware scope | Intel, AMD and hybrid P/E topology where exposed | Intel x86-64 | Apple Silicon arm64 |
| Candidate search | Worker counts **and** CPU-affinity placements | Worker counts, native macOS scheduling | No search; XMRig automatic configuration |
| Current winner decision | Engine selection with uncertainty and A-B-B-A tiebreak | Engine selection with uncertainty and A-B-B-A tiebreak | Not applicable |
| XMRig lifetime | Fresh supervised process per configuration | Single process, live worker-count reload to retain its dataset | Single process for the run |
| Memory preparation | Huge Pages and supported MSR preparation, both reported | Superpages measured/reported | Normal pages; no superpages |
| Benchmark duration | 24 hours of qualified online time | 24 hours of qualified online time | 24 hours of qualified online time |
| Pool connection | `pool.hashvault.pro:443`, TLS | `pool.hashvault.pro:443`, TLS | `pool.hashvault.pro:443`, TLS |
| Mining unlock | Verified report from the same host | Verified report from the same Mac | Verified report from the same Mac |

A Mac Apple Silicon benchmark is a monitored, 24-hour **automatic XMRig baseline**, not an Intel-style optimization search. Linux CPU pinning and Linux-specific Memory PSI/MSR features are never attributed to a Mac.

## 3. System requirements

**Linux:** Ubuntu Desktop x86-64 (Intel/AMD), Python 3.10 or newer and Tk, with normal desktop access and administrative authorization for controlled preparation. The Debian package declares `python3`, `python3-tk`, `pkexec`, `apt`, `ca-certificates`, `kmod` and `msr-tools`. Internet access is needed for Ubuntu package mirrors, official verified XMRig downloads and the mining pool.

**macOS:** macOS 11 or newer on Intel or Apple Silicon. The application can request Python.org Python 3.13 with Tk if missing; the Python.org installer is separately downloaded, SHA-256 and Apple-package-signature checked, and opened only with user consent. The macOS app is distributed as a universal application signed with a Developer ID and notarized by Apple (the release owner's confirmed distribution status; this inspection verified embedded signature metadata but did not query Apple's notarization service).

**Both:** Leave the computer dedicated to the benchmark during the full session, avoiding sleep and competing CPU/GPU workloads. Adequate cooling, stable electricity and a live connection matter; an interrupted connection can make 24 qualified hours take longer in wall-clock time.

## 4. Installing the first release

### Ubuntu Linux

1. Download and extract `ZTM-Special-Ops-3.1.2-Linux.RELEASE.zip` from the official release once published.
2. In its extracted `ZTM-Special-Ops-3.1.2-Linux/` directory, verify the **Debian package and installer** against `SHA256SUMS.txt`:

   ```bash
   sha256sum -c SHA256SUMS.txt
   ```

3. Run `bash install.sh` as a regular desktop user (never as root). Read prompts before granting administrative access.
4. Open **ZTM Special Ops 3.1 Stable** from the desktop menu or run `ztm-special-ops` in a normal user session. Use **PREPARE LINUX + INSTALL XMRIG** and authorize any privileged preparation separately.

The installer validates Ubuntu/AMD64, package identity, exact version and checksum. It refuses a downgrade, refuses a running conflicting workload and preserves the worker ID and reports. **Launcher migration is an intentional part of this installer:** matching outdated ZTM launchers/icons may be **moved to backup directories**, including under a user's desktop/menu directories. They are not silently deleted. Inspect the installer before proceeding if that behavior affects your environment. The packaged system desktop entry is `/usr/share/applications/ztm-special-ops.desktop` with `Name=ZTM Special Ops 3.1 Stable`.

### macOS Intel and Mac Apple Silicon

1. Download and extract `ZTM-Special-Ops-3.1.2-macOS.RELEASE.zip`. Verify its internal checksum file with `shasum -a 256 -c SHA256SUMS.txt` from the extracted directory.
2. Unzip `ZTM_Special_Ops_3.1.2_Stable.zip` to obtain `ZTM Special Ops 3.1.2 Stable.app`.
3. Open the signed, notarized application through the normal macOS security dialog. On first launch, the install manager can install it as `~/Applications/ZTM Special Ops 3.1 Stable.app`, keeping reports and the worker identity; nothing is installed without authorization.
4. Follow the native preflight/setup controls, including any separately approved Python/XMRig preparation, then explicitly authorize the 24-hour benchmark.

The macOS `.app` is universal for both CPU architectures. The benchmark and Mining session do not automatically start at login or in the background. Triple-click the application title to inspect version/build information and the code fingerprint.

## 5. Authorization and 24-hour benchmarking

**System Preparation → Explicit authorization → Discovery / reference measurements → Winner decision (where supported) → Sustained measurement → Final Results → Mining eligibility.**

For Linux and Intel macOS, the planner starts with XMRig's **automatic** configuration, evaluates up to five physically motivated challengers, and ends discovery with another identical automatic-reference run to expose drift. The plan has at most seven full configurations and maintains a constant dataset-initialization thread choice during the campaign.

Each full configuration receives **600 qualified online seconds** after warm-up. Linux may screen distinct CPU-affinity placements before the full trial; Intel macOS uses native scheduling and does not pin logical CPUs. Apple Silicon has no challenger search: it runs the standard XMRig automatic configuration for 24 qualified online hours.

Benchmarks use an actual online mining pool. Their work and pool rewards go to the explicitly disclosed I2PS receiving address, apart from XMRig's separate upstream donation. A completed benchmark is **not** a promise of profit and its time target is not a promise of a 24-hour wall-clock finish.

## 6. Current engine selection and statistical validation

The release's current decision rule is **engine selection**, not a fixed incumbent-preference margin.

A trial must be qualified, run under comparable conditions, and pass statistical/operational gates to compete. Once at least 30 shares are recorded, more than 5% rejected shares disqualifies the trial; a coefficient of variation above 0.15 also disqualifies it. Share counts gate validity; they do not multiply the speed score.

The speed statistic is the median of the 10-second readings, corrected for measurable reference drift where applicable. Correlated observations are grouped into consecutive blocks (`k = min(6, floor(n / 2))`, `k >= 4`); block medians estimate uncertainty. The leader and runner-up are compared using a Welch–Satterthwaite interval. A leader wins outright only if the lower confidence bound exceeds zero and its advantage is greater than both **0.5%** and the reference-run residual.

When insufficiently separated, candidates enter a **300-second A-B-B-A** paired tiebreak, with a second round only if unresolved. It records `statistically_resolved`, `practical_tie`, or `provisional_unresolved`. All available decision evidence, intervals and gates are written to the local report. Unresolved does not mean a fabricated winner: the report records how the provisional leader was retained.

The older approved *hardware-prior* equations are preserved in §12 as mathematical research context. They are not misrepresented as the current 3.1.2 final winner decision.

## 7. GUI, measurements and 15-minute charts

ZTM Special Ops 3.1.2 uses a desktop GUI on **both Ubuntu Linux and macOS**, with the same four main work areas. No terminal commands are required to operate the normal benchmark controls after platform-specific installation and preparation. The exact layout and available controls depend on the platform, display size, hardware capabilities and benchmark state.

| GUI area | What it shows |
|---|---|
| **ONGOING** | Preparation, explicit CPU-work authorization, benchmark Start/Stop controls, progress, real runtime events and hardware/worker status |
| **PROFILE RESULTS** | Profile and trial evidence, six synchronized rolling 15-minute charts, annotated transitions and the event inspector |
| **FINAL RESULTS** | Local qualification outcome, report evidence, result review and available report-folder controls |
| **MINING (LOCKED / UNLOCKED)** | Qualification-gated personal CPU mining, public Monero receiving address, terms acceptance, Start/Stop Mining and the official wallet-resource link |

There is **one Mining tab**. There is no separate Wallet tab or local wallet creator. A qualified same-machine 24-hour report is required before personal mining is available, and the benchmark and personal-mining workloads never run concurrently.

### Linux GUI — Ubuntu Desktop x86-64

The Linux window identifies the machine and worker, provides display scaling controls and groups the benchmark workflow in **ONGOING**:

1. **PREPARE LINUX + INSTALL XMRIG** performs the separately authorized system preparation and verified XMRig setup. The preparation terminal and status checks remain visible in the GUI.
2. Select **I authorize the 24-hour benchmark.** Read the disclosed payout, electricity and dedicated-computer requirements before starting.
3. **START BENCHMARK** begins the supervised RandomX run; **STOP** ends an active workload. The ongoing view exposes measured hashrate, profile information, accepted shares and available CPU/RAM/thermal evidence.
4. **PROFILE RESULTS** provides the six live charts, measured configurations, affinity-screening evidence and **OPEN EVENT INSPECTOR** for annotated events. On compact displays, the navigation may shorten **PROFILE RESULTS** to **PROFILES**.
5. **FINAL RESULTS** provides **VIEW TELEMETRY GRAPHS**, **REFRESH REPORT** and **OPEN RESULTS FOLDER**. On compact displays its tab may be labelled **RESULTS**.

The Linux engine can evaluate **worker counts and supported CPU-affinity placements**. Unavailable temperature or system metrics are marked unavailable rather than filled with invented values. The Mining tab stays locked until valid same-machine qualification has been recorded.

### macOS GUI — Intel Mac and Mac Apple Silicon

The macOS window identifies the worker and native CPU architecture, then exposes a platform-specific preparation flow in **ONGOING**:

1. **RUN NATIVE PREFLIGHT** checks native macOS readiness and supported requirements.
2. **PREPARE macOS + INSTALL XMRIG** prepares the architecture-appropriate, verified XMRig runtime with user authorization.
3. Select the explicit continuous-CPU-work authorization checkbox, then use **START 24H BENCHMARK**. **STOP** remains the controlled stop action; live runtime messages, progress and available sensor measurements are shown in the window.
4. **PROFILE RESULTS** shows the measured 15-minute charts and event inspector. **FINAL RESULTS** displays local report information and **SHOW REPORTS FOLDER PATH**.
5. **MINING (LOCKED / UNLOCKED)** uses the same public-address and consent model; eligibility is established by a validated 24-hour same-machine benchmark.

**Intel macOS** uses supported thread-count optimization under native macOS scheduling; it does **not** use Linux-style CPU-affinity placement. **Mac Apple Silicon** runs its native XMRig automatic CPU configuration for the benchmark: advanced CPU optimization and an **Optimized Performance** personal-mining profile are not offered on Apple Silicon. Hardware/sensor availability may differ from Intel macOS.

### Shared GUI charts and event annotations

The **six synchronized live charts** share a rolling **15-minute** clock in the Profile Results view:

| Chart | Display / data policy |
|---|---|
| CPU temperature | Orange; available OS temperature sensor readings only |
| CPU usage | Yellow; observed system-wide CPU usage |
| RAM usage | Red; Linux charts display system RAM, not a fabricated XMRig RSS figure |
| Hashrate | Green; pool-connected XMRig hashrate, with unmeasured periods distinguished from zero |
| Pool VarDiff | Violet; normal pool difficulty, with XMRig donation intervals clearly marked |
| Share activity | Accepted shares green, rejected shares red; cumulative curves continue through intervals with no new share rather than breaking |

Charts include actual profile-change markers and available event explanations; relevant affinity screening, transitions and donation intervals are distinguished. Missing telemetry remains **unavailable**, never silently interpolated into a measured value. The winning-profile trophy/validation indicator is an event cue, **not** independent proof of benchmark qualification.

**GUI screenshots:** This section describes the verified 3.1.2 shipped interfaces. No 3.0-era screenshot or simulated application image is presented as a 3.1.2 capture. Real screenshots can be added separately without modifying the application packages.

## 8. Qualified time, reports and Mining unlock

Only intervals bounded by verified pool messages not more than **90 seconds apart** count as qualified online time; there is no invented offline credit or unconfirmed tail. A completed session must accumulate **86,400 qualified online seconds**. The report's trial, tiebreak and sustained components must reconcile within **0.25 seconds** for Mining eligibility.

The final JSON report records hardware inventory, worker identity, plan, trials, evidence, winner decision, telemetry and stop reason. It is sealed with a machine-local key (HMAC) and checked against the **same worker and machine**. A copied or edited report does not qualify that other machine. A seal is an integrity check, not protection against someone with unrestricted control of the local machine and seal key.

STOP, a failed run or an incomplete qualification leaves Mining locked unless a different, already valid, same-machine report qualifies it. A fresh benchmark is available when idle and prepared.

## 9. Personal Mining and contributions

The single **MINING** tab accepts only a **public Monero receiving address** and includes a link to the official [Monero website](https://www.getmonero.org/) for wallet resources. The application does not generate local wallets, request seed phrases, collect private keys or hold recovery credentials.

Only after qualification does **START MINING** become available. Linux and Intel Mac can use a suitable measured configuration recorded in the verified report; Apple Silicon uses XMRig's automatic configuration. The **Optimized Performance** choice is not offered on Apple Silicon.

- **I2PS Engineering:** one scheduled 60-second interval to the I2PS development address for every 6,000 seconds of continuous personal-mining runtime; this is **1% of scheduled time**, not a guaranteed percentage of shares or revenue.
- **XMRig:** its own independent upstream `donate-level: 1` remains active, commonly described as a separate 1% contribution. Both contributions are disclosed; they are not a second hidden miner.

One supervised XMRig process performs personal mining; contributions use validated address reconfiguration. On Linux a rejected mandatory contribution switch stops Mining rather than bypassing it. **STOP MINING** stops the miner. Switching GUI tabs does not stop an active Mining session. The benchmark and personal Mining never run simultaneously.

## 10. Safety, STOP and failure handling

Sustained CPU work draws electricity, produces heat, may increase fan activity and can accelerate wear. Only run it on systems you own or have permission to use, with adequate power and cooling. Huge Pages / MSR / superpages are attempted and reported when supported; lack of full allocation does not automatically reject a machine.

**STOP** cleanly ends an active benchmark and records it as incomplete. An early-stop report does not confer qualification. Pool interruptions pause qualification time. The app records the first fault as the primary stop reason and appends later cleanup failures rather than concealing the first cause. A report write failure never becomes a false “successful benchmark.”

The macOS version stops on OS-reported critical thermal pressure (and its benchmark on serious pressure lasting 30 seconds); Linux records available temperatures but does not guarantee that its sensors detect every dangerous condition or stop on an arbitrary temperature threshold. The user remains responsible for thermal safety. Unrelated processes are not killed; if a conflicting XMRig is active, the benchmark refuses to start.

## 11. Files, privacy and network behavior

| Information | Ubuntu Linux | macOS |
|---|---|---|
| System app | `/usr/lib/ztm-special-ops/` | `~/Applications/ZTM Special Ops 3.1 Stable.app` |
| Report data | `~/ZTM-Special-Ops-Results/` | `~/Library/Application Support/I2PS/ZTM Special Ops/results/` |
| Report seal key | `~/.local/share/ztm-special-ops/report_seal.key` | `~/Library/Application Support/I2PS/ZTM Special Ops/report_seal.key` |
| Launcher backups (installer only) | `~/.local/share/ztm-special-ops-retired-launchers/` and `/var/lib/ztm-special-ops/retired-launchers/` | Not applicable |

The pool is `pool.hashvault.pro:443` with **TLS enabled for benchmark and personal Mining on both platforms**. The pool sees the payout address and worker ID. Official GitHub assets are used for verified XMRig downloads; Ubuntu uses its package mirrors; macOS can use Python.org only after user consent; wallet resources open only when requested.

ZTM Special Ops does not require an I2PS account and does not include a ZTM Vanguard telemetry relay. Reports remain local unless you choose to export or share them. A persistent worker ID and public wallet address can still correlate sessions at the pool. Read reports before posting them publicly.

## 12. Approved mathematical research reference

The original mathematical framework below remains part of the public engineering explanation. **The equations and coefficients in this section have not been recalculated or retuned.** They document hardware-aware candidate priors and the earlier reference-noise research method; §6 above describes the **actual current 3.1.2 winner decision**. The methodological distinction is intentional: theoretical ranking is not a substitute for measured online evidence.

Let `L` be allowed logical CPUs, `P` physical core groups, `B` the verified XMRig automatic worker count, `n` active mining workers, `A` a legal affinity set, and `I` dataset-initialization threads. `P_p` and `P_e` are performance/efficiency-core counts when those classes are exposed. Initialization threads are not steady-state mining workers.

### Constant initializer and memory feasibility prior

$$
I=\min\big(L,\;I_{mem}\big),\qquad I_{mem}=\begin{cases}\lceil P/2\rceil & \text{if measured copy bandwidth}<3\ \text{GB/s or available RAM}<2{,}336+1{,}024\ \text{MiB}\\ P & \text{otherwise}\end{cases}
$$

### Physically motivated candidate anchors

$$
\mathcal{A}=\langle\,B{+}1,\;P,\;C_3,\;C_3{+}1,\;B{-}1,\;B{+}2,\;[P_p,\;P_p{+}\lceil P_e/2\rceil,\;P_p{+}P_e]_{\text{hybrid}},\;L,\;C_2,\;P{+}1,\;B{-}2,\;B{+}3\,\rangle
$$

Here $C_3=\sum_d\lfloor S_d/2\,\text{MiB}\rfloor$ over L3 domains and $C_2=\sum_d\lfloor S_d/256\,\text{KiB}\rfloor$ over L2 domains, each capped at $L$. The budgets reflect the RandomX working sets. The theoretical lower bound for sufficiently many physical cores is $f=\max(2,\lceil B/2\rceil)$, with the documented performance-core exception.

### Linux placement prior

$$
J(A)=2P_{L3}+0.6P_{L2}+0.35P_{L1}+1.3\,\varphi\,\frac{S(A)}{P}+E(A)+P_{mem}(A)+0.12\frac{|n-B|}{L}-0.12\frac{n}{L}+P_{L1,fallback}
$$

$P_{Lk}=\sum_d \max(0,a_d-c_d)/c_d$, where $c_d=\max(1,\lfloor C_d/R_k\rfloor)$. The original vendor-SMT factor $\varphi$ is Intel `1.0`, AMD `0.25`, unknown `0.6`; $E(A)=0.5\cdot\min(e_{sel},p_{idle})/n$ penalizes selecting an E-core while a P-core remains idle. This is a dimensionless **prior**, not a predicted hashrate.

With $n$ workers, $S$ SMT siblings, $P$ physical cores and $o=\max(0,n-P)$, the approved memory-penalty terms are:

| Term | Applied when | Original formula |
|---|---|---|
| Capacity | Available RAM $M$ measured | $M<M_{min}=2{,}336+2n+1{,}024$ MiB: $\;1.8+\min\!\big(4,\tfrac{M_{min}-M}{1024}\big)\big(0.3+\tfrac{n}{P}\big)$, otherwise zero |
| Bandwidth proxy | Copy bandwidth $W$ (GB/s) measured | $0.70\cdot\min\!\big(3,\tfrac{\max(0,\,n-c)}{c}\big)$, $\;c=\max(1,W/2)$ |
| Bandwidth × SMT | $W$ measured | $0.18\cdot\tfrac{S}{P}\cdot\min\!\big(2,\tfrac{\max(0,\,8-W)}{6}\big)$ |
| Latency proxy | Pointer-chase latency $\lambda$ (ns) measured | $0.35\cdot\min\!\big(2,\max(0,\tfrac{\lambda-95}{95})\big)\cdot\big(\tfrac{o}{P}+0.2\tfrac{n}{P}\big)$ |
| DDR speed prior | Rated/configured MT/s with confidence weight | $0.08\cdot\text{conf}\cdot\operatorname{clamp}(3200/\text{MT/s},\,0.25,\,2)\cdot\tfrac{o}{P}$ |
| Verified channels | Verifiable channel count | $0.20\cdot\tfrac{\max(0,\,n-T/4)}{\max(1,\,T/4)}$, $\;T=\text{MT/s}\times8\times\text{channels}/1000$ |
| Memory pressure | Linux PSI some avg10 $>2\%$ | $0.40\cdot\min\!\big(3,\tfrac{\text{PSI}-2}{10}\big)\cdot\tfrac{n}{P}$ |
| Huge Pages shortfall | Free Huge Pages $<2{,}336+2n$ MiB | $0.04\cdot\tfrac{n}{P}$ |

Missing inputs must not be replaced by fictitious measurements. Memory bandwidth and latency probes are proxies, not RandomX-specific measurements. Physical topology, RAM performance, Huge Pages allocation and temperature are hypotheses until the online measurements confirm their impact.

### Original reference-repeat noise formulation (research reference)

$$
g=\frac{|H_{rep}-H_{ref}|}{(H_{ref}+H_{rep})/2},\qquad \hat\sigma=g\,\frac{\sqrt{\pi}}{2},\qquad \delta=\operatorname{clamp}\!\Big(2\sqrt{\tfrac32}\,\hat\sigma,\;1\%,\;10\%\Big)
$$

The original analysis used $E|X_1-X_2|=2\sigma/\sqrt\pi$ and a $\sqrt{3/2}$ variance adjustment. Other reference-model expressions included the trial quality term $Q=\tilde H\cdot\max(0.70,\,1-\min(\mathrm{CV},0.30))$, the drift correction $\tilde H_i=H_i/(1+d\,\tau_i)$ for $d=H_{rep}/H_{ref}-1$, and the historical reference-margin decision $Q_{c^*}>\bar Q_{ref}\,(1+\delta)$. **That final margin decision does not describe the currently shipped 3.1.2 engine selection**; see §6 for the current statistical/tiebreak method.


**Additional notation retained from the approved mathematical reference:** Count feasibility spans $1..L$, where the automatic baseline is $B$ and a neighbor candidate can be $B{+}1$. Performance- and efficiency-core counts are $P_p$ and $P_e$; an eligible performance-core-only exception requires $P_p\ge2$. $C_3$ denotes the L3 anchor. A placement is $A$, its extra sibling occupation is $S(A)$, and its memory prior is $P_{mem}$. The historical warm-up rule was $\min(25\,\text{s},\,\text{duration}/5)$, and its variation statistic was $\mathrm{CV}$. The reference-noise estimate $\hat\sigma$ could produce a provisional $\delta=3\%$ or a high-noise flag at $\delta>10\%$, with a noise-margin symbol $\delta$, relative trial position $\tau_i\in[0,1]$ and $\bar Q_{ref}$ the mean of reference results. These are retained as original research symbols, **not a substitution for the release's current decision logic**.

## 13. Troubleshooting

| Symptom | Interpretation / action |
|---|---|
| Huge Pages or superpages below 100% | Recorded, not fatal; compare only measured equivalent conditions |
| A competing XMRig is active | Stop it yourself before starting ZTM; the app does not take ownership of that process |
| 24 hours of wall time have elapsed but benchmark is unfinished | Offline/unverified intervals do not count; check the online-qualified timer |
| `provisional_unresolved` | Tiebreak did not establish a statistically separable winner; the report records the result |
| Mining remains locked | Check same-machine report seal, status, worker identity and reconciled qualification time |
| Missing temperature or memory metric | Sensor unavailable; ZTM does not fabricate readings |
| Linux desktop menu shows an unexpected launcher | Check the installed system `.desktop` entry and any retained user-specific shortcut; the installer backs up matching superseded entries rather than silently deleting them |

## 14. Project boundaries and license

ZTM Special Ops is distinct from ZTM Vanguard. This release has no Vanguard data-upload or remote-analytics pipeline; its CPU, memory, affinity and workload data are useful for the I2PS Dual-ISA Lab's processor research when voluntarily collected and analyzed.

Read the **build-specific copies included inside your Linux or macOS release ZIP**. Those files define the distribution's actual disclosure text, rather than an unrelated older repository document:

- `LICENSE.md` — I2PS proprietary noncommercial end-user terms.
- `TERMS.md` — explicit benchmark authorization, payout and electricity disclosures.
- `PRIVACY.md` — local evidence, worker identifiers and network scope.
- `THIRD_PARTY_NOTICES.md` — third-party rights including XMRig GPLv3.

**Built by I2PS Engineering.**  
Copyright © 2026 I2PS Engineering / I2PS Solutions. All rights reserved.
