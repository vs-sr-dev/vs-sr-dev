# Silicon Relics

Homebrew, ports and preservation research for **obscure and failed vintage platforms** — the machines that flopped, got cancelled, or were never documented, and so have almost no public technical record.

The goal is concrete: take technical knowledge that exists nowhere else — compiler bugs, hardware register maps, undocumented file formats, emulator internals — and make it **publicly verifiable** for the people who come after. For several of these platforms, these repositories are the only public documentation of their kind.

Everything below is either original code or documentation. **No repository here contains game assets, ROM data or copyrighted content** — the tools read media you already own.

*Everything here is published as is. This is reverse-engineering work, not a specification: findings are revisited and corrected over time, but nothing in these repositories is guaranteed to be complete or correct, whether or not a given page says so. Where a claim can be checked mechanically, the repository ships the command that checks it — run that rather than trusting the prose.*

---

## 🕹️ Homebrew

Original software, written from scratch for the target hardware.

| Repo | Platform | What it is |
|---|---|---|
| [**fcf-quest**](https://github.com/vs-sr-dev/fcf-quest) | Fairchild Channel F (1976) | A JRPG in 4 KiB of cartridge and **64 bytes of RAM**, F8 assembly |
| [**fcf-bufo**](https://github.com/vs-sr-dev/fcf-bufo) | Fairchild Channel F (1976) | *BUFO*, a road-and-river crossing game in 2 KiB, F8 assembly |
| [**vis-synth**](https://github.com/vs-sr-dev/vis-synth) | Tandy/Memorex VIS (1992) | OPL3 polyphonic synth — pad instrument, SMF player, live MIDI from host hardware over a custom MAME bridge |
| [**vis-fileviewer**](https://github.com/vs-sr-dev/vis-fileviewer) | Tandy/Memorex VIS (1992) | Media browser for photos, OPL3 audio and FLC video, the native Modular Windows way on an 80286 |
| [**wiiu-crema**](https://github.com/vs-sr-dev/wiiu-crema) | Wii U | *Crema* — a clean-room GX2/AX engine, benchmarked on real silicon |

The Channel F is the constraint that best explains the appeal: a 1976 console with **64 bytes** of system RAM, and two complete games written into it.

## 🔀 Ports & reimplementations

Existing games brought to hardware they were never meant to run on, or rebuilt natively.

| Repo | Target | Source |
|---|---|---|
| [**psx-lba**](https://github.com/vs-sr-dev/psx-lba) | PlayStation | *Little Big Adventure* (1994 DOS engine), at native 640×480 |
| [**ds-lba**](https://github.com/vs-sr-dev/ds-lba) | Nintendo DS | *Little Big Adventure* — 50 fps on a stock 4 MB DS, with voices, streamed music and a touch panel |
| [**wiiu-lba2**](https://github.com/vs-sr-dev/wiiu-lba2) | Wii U | *LBA2 / Twinsen's Odyssey* from the 1997 Adeline source — completed start-to-finish on real hardware |
| [**dc-lba2**](https://github.com/vs-sr-dev/dc-lba2) | Dreamcast | *LBA2* on KallistiOS — v0.9 alpha, real-hardware boot blocker still open |
| [**wiiu-planetblupi**](https://github.com/vs-sr-dev/wiiu-planetblupi) | Wii U | *Planet Blupi* (Epsitec) — GamePad touch as mouse, runs on Aroma |
| [**vis-wolf3d**](https://github.com/vs-sr-dev/vis-wolf3d) | Tandy/Memorex VIS | *Wolfenstein 3D*, Win16 native, OPL3 audio |
| [**3do-omf2097**](https://github.com/vs-sr-dev/3do-omf2097) | Panasonic 3DO | *One Must Fall: 2097*, built on OpenOMF |
| [**pc-mikie**](https://github.com/vs-sr-dev/pc-mikie) | portable C | Konami's *Mikie* (1984) statically recompiled from MC6809, verified instruction-by-instruction against MAME |
| [**pc-highlander**](https://github.com/vs-sr-dev/pc-highlander) | PC | *Highlander: The Last of the MacLeods* (Jaguar CD, 1995) — native reimplementation |
| [**pc-rpgmaker3**](https://github.com/vs-sr-dev/pc-rpgmaker3) | PC | The *RPG Maker 3* (PS2) engine — native reimplementation |
| [**pc-immercenary**](https://github.com/vs-sr-dev/pc-immercenary) | PC | *Immercenary* (3DO, 1995) — tooling and docs, port in progress |
| [**pc-ragnarokodysseyace**](https://github.com/vs-sr-dev/pc-ragnarokodysseyace) | PC | *Ragnarok Odyssey ACE* (PS3) — tooling and docs, port in progress |

All ports are **BYOA** — bring your own assets. They need a copy of the game you already own.

## 📖 Documentation & reverse engineering

### Platform research

Three platforms with essentially no prior public reverse-engineering record.

| Repo | Platform | Result |
|---|---|---|
| [**hyperscan-homebrew**](https://github.com/vs-sr-dev/hyperscan-homebrew) | **Mattel HyperScan** (2006) — Sunplus S+Core 7, RFID cards, a total commercial flop | 16+ reproducible bugs in the unmaintained GCC `score-elf` backend with verified workarounds; PPU, RFID-NFC and I²C drivers from scratch; the **first emulated HyperScan audio in MAME** ([video](https://www.youtube.com/watch?v=1vh_27eTpfc)) |
| [**ngpc-homebrew-notes**](https://github.com/vs-sr-dev/ngpc-homebrew-notes) | **SNK Neo Geo Pocket Color** (1999) — Toshiba TLCS-900/H | Verified toolchain and binary inventory, plus the **first NGPC↔Dreamcast link-cable bridge ever emulated** — retail hardware from 1999 that had never been emulated on either side ([homebrew](https://www.youtube.com/watch?v=x2IV3T3Z0oM) · [retail](https://www.youtube.com/watch?v=mmxnnkZzu-s)) |
| [**pippin-homebrew**](https://github.com/vs-sr-dev/pippin-homebrew) | **Bandai Pippin @WORLD** (1996) — Apple-licensed PowerPC 603 | Upstreamable **DingusPPC** fixes giving it serial-over-DBDMA, which **put the emulated Pippin on the real Internet** (ping, and a live page in Netscape), plus a homebrew thin-client browser — and an honest, `tcpdump`-backed account of the one symptom that turned out *not* to be the emulator's fault |

### Game and engine documentation

Format archaeology: containers, sprite codecs, map formats, text systems, and the strata a shipped build accidentally preserves. Each repository carries machine-checkable verification commands, not just prose — the claims can be re-run against the files years from now.

The four largest families are now indexed rather than listed: each index repository holds the per-title write-ups verbatim, and links to the shared platform notes so there is only ever one copy of a finding. Everything below is reachable from here in at most two hops.

| Repo | Subject |
|---|---|
| [**cd32-gamelist-doc**](https://github.com/vs-sr-dev/cd32-gamelist-doc) | **Index — 17 Amiga CD32 / CDTV repositories** covering **18 pressings**, carrying the full write-up that used to sit in this table. Eighteen pressings in, the family has produced a measured baseline table of eighteen columns, the `.TM` block pinned to a file rather than a fixed sector, five timestamp epochs, nine container formats, and a floppy-port-versus-CD32-first compression rule proved as a controlled experiment rather than a correlation. Shared findings live in the checklist below |
| [**cd32-platformnotes-doc**](https://github.com/vs-sr-dev/cd32-platformnotes-doc) | **The shared Amiga CD32 / CDTV platform checklist** the eighteen discs above feed into, so later Amiga CD pipelines extend one copy instead of forking it — disc identification (the system identifier of a CD32 game reads **`CDTV`**), the **`.TM` block that belongs to no file**, is pointed at only by a field in the volume descriptor, is **not always at sector 21 and not always 2,048 bytes**, is required for the disc to boot at all, shipped to developers as a file (`CD32.TM`, `CDTV.TM`) and holds **whatever that file was — not what the console was**, three claims here that later discs **falsified and that are corrected in place**, RNC ProPack, the Imploder *and* Bytekiller with the argument for lifting a decruncher out of the loader rather than trusting a format description — and the correction that **a scan finding no compression magic proves nothing**, the AmigaDOS epoch hiding a build log in the directory timestamps, the two greps that say whether a loader touches the OS at all, RNC ProPack method 1 with the bit-reader detail that makes it self-checking, hunk executables, copper lists and interleaved planar bitmaps, and the encodings not to assume |
| [**cdi-gamelist-doc**](https://github.com/vs-sr-dev/cdi-gamelist-doc) | **Index — 5 Philips CD-i discs**, one repository each, carrying the full write-up that used to sit in this table. Five discs that bracket the format instead of agreeing on it: 2.4 % full to 98 % full, a CD-i Ready title hiding entirely in the 69,150-sector pregap of track 1, and two retail builds that shipped their own symbol tables. Shared findings live in the checklist below |
| [**cdi-platformnotes-doc**](https://github.com/vs-sr-dev/cdi-platformnotes-doc) | **The shared CD-i platform checklist** the five discs above feed into, rather than each forking a copy — sector and Green Book layouts, OS-9 module validation, coding bytes, DYUV, real-time interleave, and the 29 seconds of authoring-system audio that turns up **byte-identical** on three unrelated discs, two from 1993 and one from 1995 |
| [**tales-gamelist-doc**](https://github.com/vs-sr-dev/tales-gamelist-doc) | **Index — 16 *Tales* titles across ten platforms** (SNES, PS1, PS2, GameCube, Wii, Nintendo DS, i-appli keitai, Xbox 360, PC, Android), one repository each, carrying the full write-up that used to sit in this table. This is the one index organised **by saga rather than by platform**, because the shared thing — Wolf Team's in-house LZSS — belongs to the series and not to any one machine: no platform except PC has enough *Tales* on it to hold an index of its own. The codec itself is the repository below |
| [**tales-blockcodec-doc**](https://github.com/vs-sr-dev/tales-blockcodec-doc) | **The shared *Tales* block codec** the sixteen carts and discs feed into, rather than each forking a copy — Wolf Team's in-house LZSS, from the Super Famicom in 1995 to the Xbox 360 in 2008, with a reference decoder, per-title lineage reports and the identity tests that decide whether two builds share code or only share a format. Its long-form write-up moved to [tales-gamelist-doc](https://github.com/vs-sr-dev/tales-gamelist-doc) with the rest of the series |
| [**pc-gamelist-doc**](https://github.com/vs-sr-dev/pc-gamelist-doc) | **Index — 15 PC and portable-C titles**, one repository each, carrying the full write-up that used to sit in this table. Two strands run through it: DOS-era format archaeology from 1987 to 1995 — containers, sprite codecs, map formats, and the editor work files that shipped by accident — and modern remasters and PC ports, where the interesting layer is the older console the build is still pretending to be. No shared platform checklist here: this family has the machine in common and almost nothing else |
| [**wii-thelaststory-re**](https://github.com/vs-sr-dev/wii-thelaststory-re) | *The Last Story* (Wii) and the LastWorld engine |
| [**snes-rudranohihou-re**](https://github.com/vs-sr-dev/snes-rudranohihou-re) | *Rudra no Hihou* (SNES, Square) — the Japanese text system |

## 🧰 Also

| Repo | What it is |
|---|---|
| [**chiproll**](https://github.com/vs-sr-dev/chiproll) | Browser piano roll for chip music — NES, Atari TIA and POKEY. No install, no build, no server |
| [**pc-mediacatalog**](https://github.com/vs-sr-dev/pc-mediacatalog) | .NET 8 / WPF media cataloguer — perceptual-fingerprint duplicate detection across re-encodes |
| [**silicon-relics**](https://github.com/vs-sr-dev/silicon-relics) | The wider Silicon Relics codex — a showcase site covering work beyond what is published here |

---

## Reading the repository names

`<platform>-<subject>`, where the platform is the **target**, not the origin. So [`psx-lba`](https://github.com/vs-sr-dev/psx-lba) is Little Big Adventure *running on* PlayStation, and [`pc-mikie`](https://github.com/vs-sr-dev/pc-mikie) is an arcade game *brought to* PC.

Two suffixes narrow it further: **`-doc`** is documentation only, and **`-re`** is a reverse-engineering devlog. Anything without a suffix ships runnable code.

## The wider Silicon Relics project

These repositories are part of a larger, ongoing body of cross-console work — an analog-horror ARG series and the homebrew and reverse-engineering that underpins it, spanning many years and many forgotten machines. Which platforms, and in what order, is something the series leaves for players to discover.

This is where that technical work surfaces publicly first.

## On method and attribution

This is a human + LLM collaboration, stated openly because the honesty is the point. **Claude acts as a technical bridge:** I bring decades of domain knowledge and direction — knowing these platforms, recognising when a result is a genuine first, and deciding where it's worth digging — and Claude provides implementation across architectures I could not otherwise approach: the drivers, the emulator patches, the disassembly and log forensics, the documentation. Neither side reaches these results alone.

I'm a professional technical translator, a field heavily affected by AI, and I hold a deliberate position about it: AI used for **net-new work that displaces no one** — reverse-engineering an abandoned console that nobody else was working on — is the case worth defending. Visibility of the collaboration is part of that argument, not a disclaimer.

— **[@vs-sr-dev](https://github.com/vs-sr-dev)**
