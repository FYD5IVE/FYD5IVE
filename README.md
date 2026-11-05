# Dream Maker 5 (`@FYD5IVE`) — Native CLAP Synth Workstation Architecture (`0700-AAM`)

**Principal Architect:** JJ Simmons V / Dream Maker 5 (`@FYD5IVE`)  
**Commercial & OEM Licensing Inquiries:** `dreammaker5audio@gmail.com`  
**Upstream Integration:** [Issue #26 (RFC)](https://github.com/MusicTribeOpenSource/0700-AAM/issues/26) | [PR #27 (Layer 1 Host Engine)](https://github.com/MusicTribeOpenSource/0700-AAM/pull/27)

---

### Architectural Overview & Hardware Telemetry (RK3588 / 48kHz PCM)

This repository houses the foundational clean-room C++ `ClapInstrumentProcessor` (`AudIO`) real-time synthesizer host and `ComProtocol` hardware event bridge for the Behringer KICK (`0700-AAM`) `aarch64` platform:

* **Zero-Jitter Real-Time Audio Engine:** 100% pre-allocated, lock-free SPSC event ring buffer and audio processing pipeline (`0 Bytes` real-time heap allocation inside `processAudioBlock`).
* **Continuous Hardware Stress Verification:** Proven across a 58-minute (57m 56s) continuous hardware stress test on the RK3588 (`166,848,000+` sample frames / `80.64 MB` capture at 48kHz PCM, `< 2.0s` offline stem throughput, `0 XRUNs`).
* **The Audiom Matrix & Poly-Aftertouch Throughput:** Simultaneous lock-free event merging across 16 RGB pads, 4 endless encoders (Banks A/B for 8 X/Y macros), capacitive touch strip, optical gesture camera, 4x CV/Gate hybrid loops, and external 61-key MIDI/USB controllers (`clap_input_events_t` / `clap_event_param_mod_t`).

---

### Authorship, Copyright & Commercial Dual-Licensing Notice

**Copyright (c) 2026 JJ Simmons V / Dream Maker 5 (`@FYD5IVE`). All Rights Reserved.**

1. **Open-Source Layer 1 Core (`AGPL-3.0-or-later`):** The foundational `ClapInstrumentProcessor` (`AudIO`) real-time C++ host engine and `ComProtocol` event bridge contributed to `MusicTribeOpenSource/0700-AAM` (Issue #26 / PR #27) are provided under the GNU Affero General Public License v3.0 (`AGPL-3.0`). Any open-source fork, redistribution, or derivative work must retain all original `Dream Maker 5 (@FYD5IVE)` SPDX copyright headers and `Signed-off-by` DCO attributions, and must disclose its complete modified source code under `AGPL-3.0`.
2. **Commercial Product Rollouts (Dual-License Required):** Third-party OEMs, hardware integrators, or software vendors wishing to incorporate the Dream Maker 5 `ClapInstrumentProcessor` architecture, `The Audiom Matrix` event routing, or derivative host code into closed-source commercial products, proprietary firmware images, or paid distributions without `AGPL-3.0` source disclosure must obtain a separate Commercial OEM License directly from Dream Maker 5 (`dreammaker5audio@gmail.com`).
3. **Proprietary Layer 2 User-Space & Hardware IP:** The `MancerMaps` user-space macro-binding compiler (`/mnt/sdcard/Plugins/CLAP/`), `Pin-Bind Protocol` controller auto-discovery profiles, `The Alch-Loop` hybrid analog CV/Gate calibration matrices, and Phase 2 `KICK KEYS` hardware daughterboard schematics remain the exclusive proprietary intellectual property of Dream Maker 5 and are not licensed under `AGPL-3.0`.

---
