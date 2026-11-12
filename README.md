# i_hate_powervr

> "Dear Harry, who's responsible? Sign that, 'Affectionately, A Dissatisfied Customer.'"
>
> — Hawkeye Pierce, dictating his telegram to Harry S. Truman, *M\*A\*S\*H*, "Dr. Pierce and Mr. Hyde" (1973)

Open, clean-room replacements for the closed parts of Imagination Technologies' PowerVR GPU stack, so you can run
these GPUs without Imagination's proprietary code and eventually forget it ever existed.

## Part of the "forbidden secret math" driver series

They make real chips, then keep selling them with drivers they know are broken. Half the features the silicon
supports never make it into the driver at all. Nobody even files bug reports anymore: the $5 dongle just doesn't
work, and it ends up in a drawer. The firmware is locked so nobody else can fix it. The out-of-tree driver rots until
the device is e-waste, and the next product ships with the same problems. This series does the job they keep sweeping under the rug:
well-maintained, feature-complete open replacements, so their code and patent troll behaviours can be deleted and
forgotten.

The closed path stays in use until its open replacement matches it on every feature and measures as good or better.

- [i_hate_realtek](https://github.com/DaveWK/i_hate_realtek): Realtek firmware and drivers
- [i_hate_powervr](https://github.com/DaveWK/i_hate_powervr): PowerVR GPU firmware (Rust)
- [design_deez](https://github.com/DaveWK/design_deez): Synopsys DesignWare (DDR PHY training first)

## Why

The Linux kernel driver (`drivers/gpu/drm/imagination`) and Mesa's PowerVR driver are open source. The GPU still won't
run without a **closed firmware image** that executes on the GPU's own microcontroller. Its licence allows
redistribution only unmodified and forbids reverse engineering. So every system with a PowerVR GPU depends on an opaque
binary that nobody outside Imagination can fix, audit or improve.

This repository is where the open replacement gets built.

## Scope

- **Open GPU firmware, in Rust.** It is written against the kernel↔firmware interface that Imagination's own open
  kernel driver publishes (`pvr_rogue_fwif*.h`, `pvr_rogue_cr_defs*.h`, the MIPS/RISC-V memory maps), plus black-box
  behaviour observed from the open host side.
- **Host tools:** firmware container packer, device-info (BVNC) table generator, interface bindings, test harnesses.
- **Documentation** of the firmware interface and the per-core facts, each with its open source cited.
- **Parity and benchmark results** against the closed firmware.

First target: the BXM-4-64 (BVNC 36.56.104.183) in the Allwinner A733, which has a MIPS firmware processor.

## What this repository does NOT contain

- No Imagination firmware binaries, source or headers that aren't already published under an open licence.
- Nothing obtained by disassembling, decompiling or dumping their firmware.

See [CONTRIBUTING.md](CONTRIBUTING.md). Clean room is the whole point: it keeps the result unencumbered.

## Status

Groundwork: toolchain, interface bindings, firmware packer, and a P0 firmware that answers the kernel driver's
start-up handshake. Contributions are welcome, including LLM-assisted ones, under the rules in CONTRIBUTING.md.

## Licence

MIT unless a file says otherwise. Code derived from GPL-licensed headers keeps their licence, noted per file.
