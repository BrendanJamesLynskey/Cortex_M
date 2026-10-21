<!-- portfolio-strip:start (brief 40) -->
<sub>**Brendan Lynskey** · [Portfolio home](https://brendanjameslynskey.github.io/) · [Interactive sites](https://brendanjameslynskey.github.io/#sites)</sub>
<!-- portfolio-strip:end -->

# ◈ Arm Cortex-M Presentation Series

Interactive slide decks covering the Arm Cortex-M family end-to-end — from the history of Arm itself, through the Armv6-M / v7-M / v8-M architectures, the exception model, memory system, DSP &amp; Helium extensions, debug infrastructure, and TrustZone security.

Designed as interview preparation for embedded-systems, firmware, and silicon engineers working with Cortex-M microcontrollers.

## ▶ [Open the Series Landing Page](https://brendanjameslynskey.github.io/Cortex_M/)

> **Setup:** Enable GitHub Pages (Settings → Pages → Deploy from `main` branch, `/ (root)` directory).
>
> Alternatively, open `index.html` locally in any browser — all presentations work offline after first load.

---

## Presentations

| # | Topic | Slides | Status |
|---|-------|--------|--------|
| 01 | History of Arm &amp; the Architecture | 20 | ✅ Complete |
| 02 | Architecture &amp; Programmer's Model | 28 | ✅ Complete |
| 03 | Exceptions, Interrupts &amp; NVIC | 26 | ✅ Complete |
| 04 | Memory System &amp; MPU | 25 | ✅ Complete |
| 05 | DSP, FPU &amp; Helium (MVE) | 24 | ✅ Complete |
| 06 | Debug &amp; Trace — CoreSight | 24 | ✅ Complete |
| 07 | Low-Power Design | 23 | ✅ Complete |
| 08 | TrustZone for Armv8-M | 25 | ✅ Complete |

---

## Presentation 01: History of Arm &amp; the Architecture

20 slides covering:

**Prehistory** — Acorn Computers, the BBC Micro, the evaluation of 80286 / 68000 / NS32016 and the Berkeley-RISC inspiration that led Sophie Wilson and Steve Furber to design the ARM1 in-house.

**ARM1 (1985)** — 25,000 transistors on VLSI Technology 3 µm CMOS, 6 MHz, ~44 instructions. The famous "running on leakage" anecdote.

**ARM2 / ARM3** — the Acorn Archimedes as the world's first RISC desktop; ARM3 adds the first on-die cache.

**1990 — Apple / VLSI spin-out** — Advanced RISC Machines Ltd is founded as a pure IP licensing company. The Newton MessagePad ships the first commercial Arm IP design.

**ARM7TDMI (1994)** — Thumb, Debug, Multiplier, ICE-RT. The mobile-phone breakthrough; hundreds of millions of Nokia and TI OMAP shipments.

**Architecture versions — Armv1 → Armv9** — interactive picker showing what each generation added and when.

**The 2004 profile split** — why Arm separated Application / Real-time / Microcontroller profiles; the strategic decision to make the Cortex-M3 the first v7-M core.

**The Cortex-M timeline** — M3 (2004) → M0 &amp; M4 (2009/10) → M0+ → M7 (2014) → M23/M33 (2016) → M35P → M55/M85 (2020/22) → M52 (2024).

**Corporate history** — LSE IPO (1998), SoftBank acquisition (2016), the failed Nvidia deal (2020–22), the NASDAQ IPO as Arm Holdings plc (2023).

**Lessons for the interview** — why Thumb-only, why NVIC is architectural, why caches only on M7+, how to position Cortex-M against RISC-V in 2024/5.

## Presentation 02: Architecture &amp; Programmer's Model

28 interactive slides covering:

**The Cortex-M family** — M0, M0+, M1, M3, M4, M7, M23, M33, M35P, M52, M55, M85. How the M-profile fits alongside A-profile (application) and R-profile (real-time). Positioning by performance class and silicon area.

**Architecture versions** — Armv6-M (M0/M0+/M1/M23), Armv7-M / v7E-M (M3/M4/M7), Armv8-M Baseline &amp; Mainline (M23/M33/M35P/M55/M85), Armv8.1-M (Helium, M52/M55/M85).

**The Thumb-2 ISA** — 16-bit and 32-bit mixed encoding, code density, condition codes, the IT (If-Then) block, BL/BLX/BX, load/store multiple.

**Programmer's model** — R0–R12, SP (MSP/PSP banking), LR, PC, xPSR (APSR, IPSR, EPSR), PRIMASK/FAULTMASK/BASEPRI, CONTROL. Thread vs Handler mode and Privileged vs Unprivileged execution.

**Stacks** — dual-stack architecture, MSP for handlers/kernel, PSP for threads, stack frame layout, auto-push of {R0-R3, R12, LR, PC, xPSR}.

**Endianness, alignment, and unaligned access support.**

## Presentation 03: Exceptions, Interrupts &amp; NVIC

26 slides covering the complete exception model — the 15 system exceptions (NMI, HardFault, MemManage, BusFault, UsageFault, SecureFault, SVCall, DebugMonitor, PendSV, SysTick) plus up to 480 external IRQs. Vector table layout; `SCB-&gt;VTOR` relocation. NVIC priority registers, priority grouping, enable/pending/active bits. Exception entry/exit cycle counts across M0/M3/M4/M7. Tail-chaining, late arrival, pop-preemption. Lazy floating-point stacking. Wake-up Interrupt Controller (WIC). Fault handlers, CFSR/HFSR, diagnosing a HardFault step-by-step.

## Presentation 04: Memory System &amp; MPU

25 slides on the Cortex-M memory architecture — the eight fixed regions (Code, SRAM, Peripheral, external RAM/device, PPB). Bit-banding. Memory types &amp; attributes (Normal / Device / Strongly-Ordered; Cacheable, Bufferable, Shareable). Barriers (DMB, DSB, ISB). MPU — v7-M PMSA (8 regions, power-of-two sizes, subregion disable) vs v8-M MPU (base/limit addressing, MAIR attribute indirection). Caches (M7, M55, M85). Tightly-Coupled Memory (ITCM/DTCM).

## Presentation 05: DSP, FPU &amp; Helium (MVE)

24 slides on signal-processing acceleration — DSP extension (QADD8/QSUB8, SMLAD, SMLSD), saturating arithmetic (QADD/QSUB), dual multiply-accumulate. FPU variants (FPv4-SP, FPv5-SP, FPv5-DP). Helium (MVE) — 128-bit beat-wise SIMD, tail-predication, low-overhead loops, scatter-gather. Int8 and FP16 in Helium for TinyML. CMSIS-DSP &amp; CMSIS-NN integration.

## Presentation 06: Debug &amp; Trace — CoreSight

24 slides on the Cortex-M debug infrastructure — SWD vs JTAG; Debug Access Port (DAP); Breakpoint Unit (FPB / BPU); Data Watchpoint &amp; Trace (DWT); Instrumentation Trace Macrocell (ITM); Embedded Trace Macrocell (ETM); TPIU &amp; SWO; Micro Trace Buffer (MTB) for M0+; semihosting; SEGGER RTT.

## Presentation 07: Low-Power Design

23 slides on Cortex-M power management — Sleep and Deep-Sleep via WFI / WFE; SLEEPDEEP, SLEEPONEXIT, SEVONPEND; Wake-up Interrupt Controller (WIC); tickless RTOS; ULPMark (EEMBC); STM32 STOP/STANDBY, NXP LPM, Ambiq subthreshold patterns.

## Presentation 08: TrustZone for Armv8-M

25 slides on the M-profile security extension — Secure and Non-Secure state; SAU and IDAU; state transitions (SG, BXNS, BLXNS, FNC_RETURN); veneer (NSC) tables; secure exception handling with banked vector tables; MPU banking; Platform Security Architecture (PSA) and Trusted Firmware-M (TF-M).

---

## Technical details

- **Framework:** [Reveal.js 4.6.1](https://revealjs.com) from CDN
- **Fonts:** Playfair Display (headings), DM Sans (body), JetBrains Mono (code)
- **Offline:** works after first load (fonts &amp; Reveal.js cached by the browser)
- **Navigation:** `→` / `←` for slides, `Esc` for overview, `F` for fullscreen, `S` for speaker notes

## Related repositories

- [Hardware](https://github.com/BrendanJamesLynskey/Hardware) — parent hub
- [RISC-V SoC platform](https://github.com/BrendanJamesLynskey/RISCV_SoC) — contrasting open-ISA in-order pipeline
- [Modern SoC Design](https://github.com/BrendanJamesLynskey/SoC) — same visual style, complementary topics

## License

Educational use. Content © Brendan Lynskey. Fonts and Reveal.js retain their own licenses.
