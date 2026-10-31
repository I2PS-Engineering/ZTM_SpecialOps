# ZTM Special Ops — 3.0 Stable engineering verification

This document records engineering verification separately from the public [README](README.md). The documentation target is **ZTM Special Ops 3.0 Stable, version 3.0.0**, on Ubuntu Desktop x86-64 and macOS (Intel x86-64 and Apple Silicon arm64). A GitHub Release has not yet been published.

## Implementation and automated checks

The 3.0.0 package passes its automated suites: **Linux 124 tests**, run against the code extracted from the built Debian package, and **macOS 187 tests**, run with mocked Mac hardware inventory. They cover, among other things:

- the reference-bracket planner, scoring, noise floor and share gate;
- the 24-hour qualification accounting and the same-machine Mining gate;
- equal conditions without turning any machine away: huge pages reported on every start, trials under different conditions excluded from winning on Linux, the single XMRig with live reload on macOS, and the Intel Mac superpage measurement;
- XMRig share-counter parsing on both platforms;
- the one-shot macOS preparation controls, chart history bounds and Memory Guardian behavior;
- installer identity, version and safe replacement checks.

The 24-hour baseline duration, the fixed I2PS benchmark payout, the unified Mining tab and the STOP controls are part of the tested behavior.

## Physical qualification and release controls

Automated tests validate specific behaviors but **do not certify a completed 24-hour physical baseline and Mining unlock on every supported machine**. Hardware acceptance requires qualifying evidence from real systems and real mining sessions. The macOS superpage measurement makes a macOS-only system call; it is exercised on Intel Macs, not by the automated suites.

Release gates:
1. Clean Ubuntu installation and safe coexistence with unrelated applications.
2. Real-pool configuration discovery, sustained-winner measurement and same-machine qualification.
3. Every machine benchmarks on real hardware: a low-RAM Linux machine and a fragmented Intel Mac complete the benchmark, with huge pages reported correctly.
4. Correct STOP, termination of owned XMRig processes and no orphaned workload.
5. Durable results presentation and correct Mining lock/unlock behavior, including interruption cases.
6. Personal mining wallet routing, the scheduled I2PS contribution and XMRig's upstream donation.
7. Network loss and recovery, thermal behavior and rejection of incomplete runs.
8. Privileged-operation security review, dependency integrity and package authenticity.

## Distribution boundary

The public repository contains product documentation and media. The official distribution will provide the Debian package, the macOS application, the installer and an integrity manifest through GitHub Releases when published. Private engineering source, handoff archives and test fixtures are not published as release assets.

The application contains readable Python runtime modules. The proprietary license governs legal permission but **does not technically conceal readable modules**. Third-party software, including XMRig, retains its own license rights.
