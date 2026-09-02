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

The largest families are now indexed rather than listed: each index repository holds the per-title write-ups verbatim, and links to the shared platform notes so there is only ever one copy of a finding. Counts are kept in the indices, never here. Everything below is reachable from this page in at most two hops.

Some families are indexed **before** having any titles in them, so that the first disc has a structure to be filed into and a set of questions to be measured against rather than a blank page. Those checklists mark every claim by where it came from and never promote a mark because nothing contradicted it — the 3DO and Dreamcast ones are `[unverified]` throughout, meaning public documentation rather than a disc that was opened, while the VIS one separates what was measured on retail pressings from what was proven by writing code that runs on the machine. Each says which it is at the top, and an empty table there is empty on purpose.

| Repo | Subject |
|---|---|
| [**cd32-gamelist-doc**](https://github.com/vs-sr-dev/cd32-gamelist-doc) | **Index of the Amiga CD32 / CDTV disc documentation** — one repository per pressing, each carrying the full write-up that used to sit in this table. What the family has produced is measurement where there was folklore: the `.TM` block pinned to a file rather than to a fixed sector, several timestamp epochs to tell apart, a shelf of Amiga crunchers including one wearing another's magic bytes, and a floppy-port-versus-CD32-first compression rule proved as a controlled experiment rather than a correlation. The disc count and the side-by-side baselines are one click away |
| [**cd32-platformnotes-doc**](https://github.com/vs-sr-dev/cd32-platformnotes-doc) | **The shared Amiga CD32 / CDTV platform checklist** the discs in the index feed into, so later Amiga CD pipelines extend one copy instead of forking it — disc identification (the system identifier of a CD32 game reads **`CDTV`**), the **`.TM` block that belongs to no file**, is pointed at only by a field in the volume descriptor, is **not always at sector 21 and not always 2,048 bytes**, is required for the disc to boot at all, shipped to developers as a file (`CD32.TM`, `CDTV.TM`) and holds **whatever that file was — not what the console was**, three claims here that later discs **falsified and that are corrected in place**, RNC ProPack, the Imploder *and* Bytekiller with the argument for lifting a decruncher out of the loader rather than trusting a format description — and the correction that **a scan finding no compression magic proves nothing**, the AmigaDOS epoch hiding a build log in the directory timestamps, the two greps that say whether a loader touches the OS at all, RNC ProPack method 1 with the bit-reader detail that makes it self-checking, hunk executables, copper lists and interleaved planar bitmaps, and the encodings not to assume |
| [**cdi-gamelist-doc**](https://github.com/vs-sr-dev/cdi-gamelist-doc) | **Index of the Philips CD-i disc documentation** — one repository per disc, each carrying the full write-up that used to sit in this table. The discs bracket the format instead of agreeing on it: one is 2.4 % full and compresses nothing, another is 98 % full with 52 sectors of file system, a CD-i Ready title hides entirely in the 69,150-sector pregap of track 1, and two retail builds shipped their own symbol tables. Shared findings live in the checklist below |
| [**cdi-platformnotes-doc**](https://github.com/vs-sr-dev/cdi-platformnotes-doc) | **The shared CD-i platform checklist** the discs in the index feed into, rather than each forking a copy — sector and Green Book layouts, OS-9 module validation, coding bytes, DYUV, real-time interleave, and the 29 seconds of authoring-system audio that turns up **byte-identical** on three unrelated discs, two from 1993 and one from 1995 |
| [**tales-gamelist-doc**](https://github.com/vs-sr-dev/tales-gamelist-doc) | **Index of the *Tales* series documentation** — one repository per title, spanning cartridges, discs, a keitai i-appli and a phone gacha, each carrying the full write-up that used to sit in this table. This is the one index organised **by saga rather than by platform**, because the shared thing — Wolf Team's in-house LZSS — belongs to the series and not to any one machine: no platform except PC carries enough *Tales* to hold an index of its own. The codec itself is the repository below |
| [**tales-blockcodec-doc**](https://github.com/vs-sr-dev/tales-blockcodec-doc) | **The shared *Tales* block codec** the carts and discs feed into, rather than each forking a copy — Wolf Team's in-house LZSS, carried from the Super Famicom across every console generation since, with a reference decoder, per-title lineage reports and the identity tests that decide whether two builds share code or only share a format. Its long-form write-up moved to [tales-gamelist-doc](https://github.com/vs-sr-dev/tales-gamelist-doc) with the rest of the series |
| [**pc-gamelist-doc**](https://github.com/vs-sr-dev/pc-gamelist-doc) | **Index of the PC and portable-C game documentation** — one repository per title, each carrying the full write-up that used to sit in this table. Two strands run through it: DOS-era format archaeology — containers, sprite codecs, map formats, and the editor work files that shipped by accident — and modern remasters and PC ports, where the interesting layer is the older console the build is still pretending to be. No shared platform checklist here: this family has the machine in common and almost nothing else |
| [**3do-gamelist-doc**](https://github.com/vs-sr-dev/3do-gamelist-doc) | **Index of the 3DO disc documentation** — one repository per pressing. **Empty so far**: the index and its checklist were created before the first disc rather than out of it, so that the first pipeline has somewhere to be filed and a set of questions to be measured against. The platform is the odd one out among the optical families here — it does not use ISO 9660 at all, but the 3DO's own Opera file system, big-endian on an ARM6, with what appears to be a per-file list of duplicate block locations in the directory record itself |
| [**3do-platformnotes-doc**](https://github.com/vs-sr-dev/3do-platformnotes-doc) | **The shared 3DO platform checklist** discs will feed into — the volume label at sector 0, the Opera directory hierarchy, `LaunchMe` and ARM6 big-endian code, CELs and Cel Control Blocks, SDX2 audio and the Data Streamer. **A scaffold, and it says so on every line**: every claim carries the mark `[unverified]`, meaning it came from public documentation rather than from a disc that was opened, and the first pipeline converts each one into a measurement, a correction with the wrong version left visible, or a deletion. What is already real is the set of questions — *does anything use the CEL engine?*, *what is in the sectors that belong to no file?*, *is any asset pressed byte-identical on unrelated discs?* — carried over from the two families that answered them |
| [**dc-gamelist-doc**](https://github.com/vs-sr-dev/dc-gamelist-doc) | **Index of the Dreamcast disc documentation** — one repository per pressing. **Empty so far**, and created before the first disc for the same reason as the 3DO index. The platform brings a problem the others do not: it is the best-documented machine in this collection by a wide margin, so the risk is not finding an answer but inheriting one — and inherited fact is exactly what the Amiga CD and CD-i checklists exist to falsify |
| [**dc-platformnotes-doc**](https://github.com/vs-sr-dev/dc-platformnotes-doc) | **The shared Dreamcast platform checklist** discs will feed into — GD-ROM's two areas and what each dump form throws away, `IP.BIN` in front of the file system, the ISO 9660 volume behind it, the **scrambled** SH-4 executable, the middleware most of the content actually belongs to, PowerVR textures, and the ARM7 sound program that is a second binary in a second instruction set on the same disc. **A scaffold**, marked `[unverified]` throughout on the same terms as the 3DO one. Its open questions are where a cross-disc result would come from: how many generations of the `IP.BIN` bootstrap there are, whether the ARM7 driver is shared between unrelated studios, and how much of a typical disc is dummy padding — which is to say how much every published capacity figure for this platform is off by |
| [**vis-gamelist-doc**](https://github.com/vs-sr-dev/vis-gamelist-doc) | **Index of the Tandy / Memorex VIS disc documentation** — one repository per pressing. **No title documented yet**, but unlike the two indices above it does not start from nothing: three retail pressings are in hand and their `CONTROL.TAT` blocks have already been compared. The name is generous and the repository says so — the VIS library is largely reference and educational discs, and two of the three in hand are an atlas and a fitness programme. Also links the three homebrew projects the platform knowledge came from, because that provenance should be visible rather than implicit |
| [**vis-platformnotes-doc**](https://github.com/vs-sr-dev/vis-platformnotes-doc) | **The shared Tandy / Memorex VIS platform checklist** — and the one that starts from the opposite end, because here **the machine is partly known and its discs are not**. Three years of homebrew on this console measured its timers, its audio, its display path and its input without ever opening a retail disc, so the document keeps **three marks instead of one**: `[N of 3]` for retail pressings, `[authoring]` for what was proven by writing code that runs on the machine, and `[unverified]` for what is only in the Tandy SDK — and never promotes one to another. Section 2 is already measured on all three discs in hand: the leading **84 bytes of `CONTROL.TAT` are byte-identical** across three unrelated studios, the file **names and dates the Tandy tool that pressed it** — two builds of `Maketat`, six weeks apart, are already visible — and its title field carries the leftovers, including a **retail pressing of *Bible Lands* that still calls itself a prototype demo** and a *Fitness Partner* that shipped as `V.90`. Two `[authoring]` corrections are recorded in place with the wrong version left visible: a **PCM DAC these notes had recorded as absent**, and a display flag read as `NOWAIT` for a whole session that was `STRETCH 2X` all along |
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
