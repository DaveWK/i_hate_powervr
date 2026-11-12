# Contributing (clean-room rules)

These rules apply to everyone, human or LLM-assisted. Contributions that break them will be removed.

## Allowed inputs

- **Open-source code and headers under an open licence:** the Linux kernel (`drivers/gpu/drm/imagination`), Mesa
  (`src/imagination`), Imagination's GPL/MIT-licensed kernel driver sources as published by SoC vendors, and other
  open drivers.
- **Public documentation:** datasheets, talks, papers and mailing-list posts that are publicly available without an NDA.
- **Black-box observation from the open side:** register reads and writes performed by the open kernel driver, the
  timing and behaviour of the hardware, and the results of running our own firmware.

## Forbidden inputs

- Any Imagination firmware binary, including anything learned from disassembling, decompiling, hex-dumping or
  diffing it.
- Leaked, confidential or NDA material of any kind.
- Code copied from a source whose licence doesn't permit it.

## Requirements for every contribution

1. **Provenance.** Cite the open source for each interface fact, constant or sequence, as file and line or URL.
2. **Licence.** State it for new files. Code derived from GPL headers keeps the GPL.
3. **Tests.** Interface layouts are checked against the C headers. Firmware changes come with the test or hardware
   log that shows what they do.
4. **LLM-assisted work** follows the same rules. Tell the model the forbidden inputs above, and review its sources
   before submitting.

## Reporting

If you find something in the repository that came from a forbidden input, open an issue. It will be removed and
rewritten clean.
