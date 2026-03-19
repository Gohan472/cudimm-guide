# DDR5 Memory Guide: SODIMM · CSODIMM · CUDIMM

**A consumer and technician reference for understanding DDR5 memory module variants, the new Clocked DIMM standard, JEDEC part number decoding, and platform compatibility.**

> Based on real hardware — three modules photographed, labeled, and annotated side by side.

---

## What This Is

A single-file HTML guide covering everything you need to know to buy, sell, upgrade, or troubleshoot DDR5 memory in laptops, mini-PCs, and compact workstations. Written for technicians, system builders, eBay buyers/sellers, and curious users who got a BIOS warning they didn't expect.

The guide was built around three real DDR5 SODIMM modules representing three distinct generations and use cases:

| Module | JEDEC String | Type |
|--------|-------------|------|
| SK Hynix 8GB | `PC5-4800B-SC0-1010-XT` | Standard SODIMM — entry/budget config |
| Kingston 16GB | `PC5-5600B-SA0-1110-XT` | Standard SODIMM — mainstream upgrade |
| Micron 16GB | `PC5-6400B-VA0-1211-XT` | **CSODIMM** — Clocked, CKD equipped |

---

## What's Covered

**10 sections, fully illustrated with inline HTML/CSS diagrams — no external dependencies, no JavaScript frameworks, single file.**

1. **Three Modules, Three Generations** — The DDR5 SODIMM spectrum and what you actually get at different retail price points. Why 1Rx16 vs 1Rx8 matters as much as the clock speed.

2. **On-Die ECC** — Why every DDR5 module has error correction whether or not the label says so, how it works inside the DRAM die, and why it's not the same as an ECC SODIMM.

3. **DDR5 Architecture** — What actually changed from DDR4: the on-module PMIC, dual 32-bit subchannels, the SPD Hub, and why these changes are why CSODIMM requires firmware support rather than being purely plug-and-play.

4. **The Clock Signal Problem** — Why standard DDR5 degrades above 6400 MT/s, what the Client Clock Driver (CKD) does, and how CSODIMM solves signal integrity at the module level.

5. **Reading the Label** — Faithful reconstructions of all three physical module labels with annotated field breakdowns. Includes PN, JEDEC string, serial, and manufacturer identifiers — formatted for eBay research.

6. **Part Number Anatomy** — Full decoding of `PC5-6400B-VA0-1211-XT`:
   - Bandwidth math (`B_W = MT/s × bus width`)
   - Speed grade bins (Class A / B / C)
   - Rank interleaving diagram (1R vs 2R)
   - CAS latency formula (`t_AA = CL × 2000 ÷ MT/s`) with worked examples
   - CQDIMM roadmap (quad-rank, 128–256 GB)
   - XT suffix: TVS diodes, gold finger spec, temperature ratings

7. **The BIOS Warning** — Faithful reconstruction of the HP Wolf Security CUDIMM bypass mode screen with line-by-line explanation of what the firmware is actually doing and why.

8. **Platform Compatibility** — Which platforms support CKD natively (Intel Arrow Lake), which fall back to bypass mode (Ryzen AI 300 series), and which need standard SODIMM only. Montage Technology / Rambus CKD silicon, JESD301 reference.

9. **Buying & Selling Guide** — When to buy standard SODIMM vs CSODIMM, and how to list or evaluate either on eBay without getting burned by profile code mismatches.

10. **Glossary** — 21 terms defined: DDR5-SODIMM, CSODIMM, CUDIMM, CKD, PMIC, SPD Hub, Dual Subchannel, ODECC, ECC SODIMM, 1Rx8 vs 1Rx16, Rank Interleaving, CQDIMM, t_AA, Speed Grade, Bypass Mode, TVS Diode, MT/s, JEDEC Profile Code, JESD79-5 / JESD401-5B, QVL, AOD.

---

## The Key Thing Most Guides Miss

Not all DDR5 is created equal. The same "DDR5 SODIMM" label can cover:

- A **1Rx16 module at 4800 MT/s** — 4 chips, narrower internal bus, lowest cost, common in budget retail configs
- A **1Rx8 module at 5600 MT/s** — 8 chips, full-width bus, mainstream performance, plug-and-play everywhere
- A **CSODIMM at 6400 MT/s** — physically identical, but with a CKD chip on the PCB that requires explicit BIOS support to initialize — and will trigger a bypass mode warning on platforms that lack it

The JEDEC profile code is the single fastest compatibility check. In `PC5-6400B-VA0`:
- `S` = standard SODIMM → works anywhere
- `V` = CSODIMM with CKD → requires firmware support

That one character is the difference between plug-and-play and a 3200 MT/s fallback.

---

## Using the Guide

**Live:** [https://gohan472.github.io/cudimm-guide/](https://gohan472.github.io/cudimm-guide/)

Or clone the repo and open `index.html` in any browser — no server required, no build step, no dependencies.

---

## Technical Reference

| Specification | Source |
|--------------|--------|
| DDR5 core standard | JEDEC JESD79-5 / JESD79-5B |
| Module labeling nomenclature | JEDEC JESD401-5B |
| Clock Driver specification | JEDEC JESD301 |
| CKD silicon vendors | Montage Technology, Rambus |

---

## Contributing

If you have additional information that could improve the guide — platform compatibility data, BIOS version confirmations, corrections — open an issue.

---

## License

[MIT](LICENSE) — use freely, attribution appreciated.
