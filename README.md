# Silicon Relics

Homebrew, ports and preservation research for **obscure and failed vintage platforms** — the machines that flopped, got cancelled, or were never documented, and so have almost no public technical record — and native PC ports of console games that never left their console.

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

## ⚙️ Static recompilation

Console games brought to PC by translating their own machine code to C++ ahead of time and running it natively, with a runtime that stands in for the console's hardware. No emulator underneath and no source code needed: the game's code is the game's code, compiled for a different machine.

The work that every game on a console shares — its discs, its CPU, its graphics and sound hardware, its SDK — lives in a game-agnostic toolkit per console. Each toolkit grows inside the ports: a piece is written because a game needed it, then kept free of that game's knowledge.

| Toolkit | Console | What it replaces |
|---|---|---|
| [**wiikit**](https://github.com/vs-sr-dev/wiikit) | Wii and GameCube | Gekko → C++ recompiler; IOS, the GX GPU, the DSP's AX mixer, the Remote and its extensions, the GameCube's ARAM and controllers |
| [**saturnkit**](https://github.com/vs-sr-dev/saturnkit) | Sega Saturn | SH-2 → C++ recompiler; both SH-2s, VDP1 and VDP2, the SCU and its DSP, the CD block, the 68000 and SCSP |
| [**ps2kit**](https://github.com/vs-sr-dev/pc-extermination/tree/main/ps2kit) | PlayStation 2 | Disc, format and executable tooling beside PS2Recomp; still inside its first port, published on its own once a second game uses it |

| Port | Game | Built on |
|---|---|---|
| [**pc-victorious**](https://github.com/vs-sr-dev/pc-victorious) | *Victorious: Taking the Lead* (Wii, 2012) | wiikit, born here |
| [**pc-dragonquestswords**](https://github.com/vs-sr-dev/pc-dragonquestswords) | *Dragon Quest Swords* (Wii, 2007) | wiikit |
| [**pc-arcrisefantasia**](https://github.com/vs-sr-dev/pc-arcrisefantasia) | *Arc Rise Fantasia* (Wii, 2009) | wiikit |
| [**pc-monsterhunter3**](https://github.com/vs-sr-dev/pc-monsterhunter3) | *Monster Hunter Tri* (Wii, 2009) | wiikit |
| [**pc-finalfantasycrystalbearers**](https://github.com/vs-sr-dev/pc-finalfantasycrystalbearers) | *Final Fantasy Crystal Chronicles: The Crystal Bearers* (Wii, 2009) | wiikit |
| [**pc-thelaststory**](https://github.com/vs-sr-dev/pc-thelaststory) | *The Last Story* (Wii, 2011) | wiikit |
| [**pc-conduit2**](https://github.com/vs-sr-dev/pc-conduit2) | *Conduit 2* (Wii, 2011) | wiikit |
| [**pc-megamanxcm**](https://github.com/vs-sr-dev/pc-megamanxcm) | *Mega Man X: Command Mission* (GameCube, 2004) | wiikit |
| [**pc-virtualhydlide**](https://github.com/vs-sr-dev/pc-virtualhydlide) | *Virtual Hydlide* (Saturn, 1995) | saturnkit, born here |
| [**pc-deepfear**](https://github.com/vs-sr-dev/pc-deepfear) | *Deep Fear* (Saturn, 1998) | saturnkit |
| [**pc-extermination**](https://github.com/vs-sr-dev/pc-extermination) | *Extermination* (PS2, 2001) | PS2Recomp and ps2kit |
| [**pc-mikie**](https://github.com/vs-sr-dev/pc-mikie) | Konami's *Mikie* (arcade, 1984) | its own MC6809 → C recompiler (the sound board's Z80 emulated), verified instruction by instruction against MAME |

Where each one stands is at the top of its README, and in a [`.recomp.json`](https://recomp.fyi/spec) at its root that [recomp.board](https://recomp.fyi) reads.

## 🔀 Ports & reimplementations

### To other consoles

Games built from their released source for hardware they were never meant to run on.

| Repo | Target | Source |
|---|---|---|
| [**psx-lba**](https://github.com/vs-sr-dev/psx-lba) | PlayStation | *Little Big Adventure* (1994 DOS engine), at native 640×480 |
| [**ds-lba**](https://github.com/vs-sr-dev/ds-lba) | Nintendo DS | *Little Big Adventure* — 50 fps on a stock 4 MB DS, with voices, streamed music and a touch panel |
| [**jag-lba**](https://github.com/vs-sr-dev/jag-lba) | Atari Jaguar | *Little Big Adventure* at 640×480 interlaced, 3D bodies on the GPU |
| [**hs-lba**](https://github.com/vs-sr-dev/hs-lba) | Mattel HyperScan | *Little Big Adventure* on an S+core 7, from a servo-driven CD, saving 96 bytes to an RFID card |
| [**wiiu-lba2**](https://github.com/vs-sr-dev/wiiu-lba2) | Wii U | *LBA2 / Twinsen's Odyssey* from the 1997 Adeline source — completed start to finish on real hardware |
| [**n64-lba2**](https://github.com/vs-sr-dev/n64-lba2) | Nintendo 64 | *LBA2* on libdragon, its data (movies aside) in a 64 MB cartridge |
| [**dc-lba2**](https://github.com/vs-sr-dev/dc-lba2) | Dreamcast | *LBA2* on KallistiOS, with VMU saves |
| [**wiiu-planetblupi**](https://github.com/vs-sr-dev/wiiu-planetblupi) | Wii U | *Planet Blupi* (Epsitec) — GamePad touch as mouse, runs on Aroma |
| [**vis-wolf3d**](https://github.com/vs-sr-dev/vis-wolf3d) | Tandy/Memorex VIS | *Wolfenstein 3D*, Win16 native, OPL3 audio |
| [**3do-omf2097**](https://github.com/vs-sr-dev/3do-omf2097) | Panasonic 3DO | *One Must Fall: 2097*, built on OpenOMF |
| [**coleco-ff**](https://github.com/vs-sr-dev/coleco-ff) | ColecoVision | *Final Fantasy* (NES, 1987) rewritten in C, on the Super Game Module and a 512 KB MegaCart |

### Native reimplementations

Engines rebuilt for PC from their file formats and their behaviour.

| Repo | Game | State |
|---|---|---|
| [**pc-highlander**](https://github.com/vs-sr-dev/pc-highlander) | *Highlander: The Last of the MacLeods* (Jaguar CD, 1995) | engine reimplementation |
| [**pc-rpgmaker3**](https://github.com/vs-sr-dev/pc-rpgmaker3) | The *RPG Maker 3* engine (PS2, 2005) | formats and tools |
| [**pc-immercenary**](https://github.com/vs-sr-dev/pc-immercenary) | *Immercenary* (3DO, 1995) | formats and tools |
| [**pc-ragnarokodysseyace**](https://github.com/vs-sr-dev/pc-ragnarokodysseyace) | *Ragnarok Odyssey ACE* (PS3) | formats and tools |

All ports, recompiled or rebuilt, are **BYOA** — bring your own assets. They need a copy of the game you already own.

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

The larger families are indexed rather than listed: each index repository links one write-up per title, and the shared platform notes hold each finding once. Counts are kept in the indices, never here. Everything below is reachable from this page in at most two hops.

Some indices were created **before** their first title, so that the first disc had a structure to be filed into and a set of questions to be measured against. Their checklists mark every claim by where it came from — a disc that was opened, code that runs on the machine, or public documentation only — and never promote a mark because nothing contradicted it.

| Repo | Subject |
|---|---|
| [**cd32-gamelist-doc**](https://github.com/vs-sr-dev/cd32-gamelist-doc) | **Index of the Amiga CD32 / CDTV disc documentation**, one repository per pressing. Measurement where there was folklore: the `.TM` block pinned to a file rather than to a fixed sector, several timestamp epochs told apart, a cruncher wearing another's magic bytes |
| [**cd32-platformnotes-doc**](https://github.com/vs-sr-dev/cd32-platformnotes-doc) | **The shared Amiga CD32 / CDTV platform checklist** — the system identifier of a CD32 game reads **`CDTV`**, the **`.TM` block belongs to no file** and is not always at sector 21, and the claims later discs falsified are corrected in place |
| [**cdi-gamelist-doc**](https://github.com/vs-sr-dev/cdi-gamelist-doc) | **Index of the Philips CD-i disc documentation**. The discs bracket the format instead of agreeing on it: one is 2.4 % full, another 98 %, a CD-i Ready title hides entirely in the pregap of track 1, and two retail builds shipped their own symbol tables |
| [**cdi-platformnotes-doc**](https://github.com/vs-sr-dev/cdi-platformnotes-doc) | **The shared CD-i platform checklist** — Green Book layouts, OS-9 modules, DYUV, real-time interleave, and 29 seconds of authoring-system audio found **byte-identical** on three unrelated discs |
| [**3do-gamelist-doc**](https://github.com/vs-sr-dev/3do-gamelist-doc) | **Index of the 3DO disc documentation** — the odd one out among the optical families: no ISO 9660, but the 3DO's own Opera file system, big-endian on an ARM6 |
| [**3do-platformnotes-doc**](https://github.com/vs-sr-dev/3do-platformnotes-doc) | **The shared 3DO platform checklist** — begun as a scaffold of `[unverified]` claims from public documentation; each disc converts them into measurements, or into corrections with the wrong version left visible |
| [**dc-gamelist-doc**](https://github.com/vs-sr-dev/dc-gamelist-doc) | **Index of the Dreamcast disc documentation** — the best-documented machine here, so the risk is inheriting an answer rather than not finding one. The first retail disc falsified the line its checklist called most important |
| [**dc-platformnotes-doc**](https://github.com/vs-sr-dev/dc-platformnotes-doc) | **The shared Dreamcast platform checklist** — GD-ROM's two areas, `IP.BIN`, the SH-4 executable scrambled or not, and the ARM7 sound program: a second binary in a second instruction set on the same disc |
| [**vis-gamelist-doc**](https://github.com/vs-sr-dev/vis-gamelist-doc) | **Index of the Tandy / Memorex VIS disc documentation** — "game" being generous for a library of reference and educational discs. Also links the homebrew the platform knowledge came from |
| [**vis-platformnotes-doc**](https://github.com/vs-sr-dev/vis-platformnotes-doc) | **The shared VIS platform checklist**, which starts from the opposite end: the machine was known from homebrew before any retail disc was opened, so it keeps retail, `[authoring]` and `[unverified]` marks apart. The leading **84 bytes of `CONTROL.TAT` are byte-identical** across unrelated studios |
| [**tales-gamelist-doc**](https://github.com/vs-sr-dev/tales-gamelist-doc) | **Index of the *Tales* series documentation** — the one index organised **by saga rather than by platform**, from cartridges and discs to a keitai i-appli and a phone gacha |
| [**tales-blockcodec-doc**](https://github.com/vs-sr-dev/tales-blockcodec-doc) | **The shared *Tales* block codec** — Wolf Team's in-house LZSS, carried from the Super Famicom across every console generation since, with a reference decoder and the tests that tell shared code from a shared format |
| [**pc-gamelist-doc**](https://github.com/vs-sr-dev/pc-gamelist-doc) | **Index of the PC and portable-C game documentation** — DOS-era format archaeology, and modern remasters where the interesting layer is the older console the build is still pretending to be |
| [**dos-platformnotes-doc**](https://github.com/vs-sr-dev/dos-platformnotes-doc) | **A checklist for the MS-DOS-era subset** of the PC family, which as a whole has none — whether the subset has enough in common is answered by a sweep of the finished repositories, not by opinion |
| [**pc-infiniteundiscovery**](https://github.com/vs-sr-dev/pc-infiniteundiscovery) | *Infinite Undiscovery* (Xbox 360) and tri-Ace's ASKA engine |
| [**wii-thelaststory-re**](https://github.com/vs-sr-dev/wii-thelaststory-re) | *The Last Story* (Wii) and the LastWorld engine — the format notes that came before [pc-thelaststory](https://github.com/vs-sr-dev/pc-thelaststory) |
| [**snes-rudranohihou-re**](https://github.com/vs-sr-dev/snes-rudranohihou-re) | *Rudra no Hihou* (SNES, Square) — the Japanese text system |

## 🧰 Also

| Repo | What it is |
|---|---|
| [**undertow**](https://github.com/vs-sr-dev/undertow) | Emulator for the **ZAPiT Game Wave** (2005), the Canadian DVD-based console — runs each disc's own Lua 5.0.2 bytecode and reimplements the ZIT engine around it, MPEG-2 movies included. No firmware needed |
| [**ecliptic**](https://github.com/vs-sr-dev/ecliptic) | Emulator for the **Tapwave Zodiac** (2003), the Palm OS 5 handheld game console — Tapwave Native Applications on Unicorn, the 612-entry `TwGlue` OS table on the host. To our knowledge the first for the device |
| [**chiproll**](https://github.com/vs-sr-dev/chiproll) | Browser piano roll for chip music — NES, Atari TIA and POKEY. No install, no build, no server |
| [**pc-mediacatalog**](https://github.com/vs-sr-dev/pc-mediacatalog) | .NET 8 / WPF media cataloguer — perceptual-fingerprint duplicate detection across re-encodes |
| [**silicon-relics**](https://github.com/vs-sr-dev/silicon-relics) | The wider Silicon Relics codex — a showcase site covering work beyond what is published here |

---

## Reading the repository names

`<platform>-<subject>`, where the platform is the **target**, not the origin. So [`psx-lba`](https://github.com/vs-sr-dev/psx-lba) is Little Big Adventure *running on* PlayStation, and [`pc-victorious`](https://github.com/vs-sr-dev/pc-victorious) is a Wii game *brought to* PC.

Two suffixes narrow it further: **`-doc`** is documentation only, and **`-re`** is a reverse-engineering devlog. Anything without a suffix ships runnable code. A **`-kit`** is a game-agnostic toolkit, named after the console it stands in for.

## The wider Silicon Relics project

These repositories are part of a larger, ongoing body of cross-console work — an analog-horror ARG series and the homebrew and reverse-engineering that underpins it, spanning many years and many forgotten machines. Which platforms, and in what order, is something the series leaves for players to discover.

This is where that technical work surfaces publicly first.

## On method and attribution

This is a human + LLM collaboration, stated openly because the honesty is the point. **Claude acts as a technical bridge:** I bring decades of domain knowledge and direction — knowing these platforms, recognising when a result is a genuine first, and deciding where it's worth digging — and Claude provides implementation across architectures I could not otherwise approach: the drivers, the emulator patches, the disassembly and log forensics, the documentation. Neither side reaches these results alone.

I'm a professional technical translator, a field heavily affected by AI, and I hold a deliberate position about it: AI used for **net-new work that displaces no one** — reverse-engineering an abandoned console that nobody else was working on — is the case worth defending. Visibility of the collaboration is part of that argument, not a disclaimer.

— **[@vs-sr-dev](https://github.com/vs-sr-dev)**
