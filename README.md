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

| Repo | Subject |
|---|---|
| [**pc-princeofqin-doc**](https://github.com/vs-sr-dev/pc-princeofqin-doc) | *Prince of Qin* (秦殇, 2002) and Object Software's "EasyRPG" engine |
| [**pc-meridian59-doc**](https://github.com/vs-sr-dev/pc-meridian59-doc) | *Meridian 59* (1996), one of the first graphical MMORPGs — and 30 years of operational strata |
| [**pc-dungeonhack-doc**](https://github.com/vs-sr-dev/pc-dungeonhack-doc) | *Forgotten Realms: Dungeon Hack* (1993) and the AESOP/16 engine |
| [**pc-wackywheels-doc**](https://github.com/vs-sr-dev/pc-wackywheels-doc) | *Wacky Wheels* (Apogee, 1994) and its fixed-point pseudo-3D floor renderer |
| [**pc-battlebugs-doc**](https://github.com/vs-sr-dev/pc-battlebugs-doc) | *Battle Bugs* (Sierra/Epyx, 1994) — 800×600 in 16 planar colours, one asset set serving both modes, and a per-bitplane column-major image codec |
| [**pc-mm-doc**](https://github.com/vs-sr-dev/pc-mm-doc) | *Might & Magic: Secret of the Inner Sanctum* (1987) |
| [**pc-grandiahd-doc**](https://github.com/vs-sr-dev/pc-grandiahd-doc) | *GRANDIA HD Remaster* — the PSX GPU/SPU/CD libraries reimplemented on D3D11/XAudio2 |
| [**pc-secretofmana-doc**](https://github.com/vs-sr-dev/pc-secretofmana-doc) | *Secret of Mana* (2018 PC remake), a PhyreEngine title |
| [**pc-ff5-doc**](https://github.com/vs-sr-dev/pc-ff5-doc) | *FINAL FANTASY V* (2015 PC) and the mobile-port fingerprints in the build |
| [**pc-fftype0-doc**](https://github.com/vs-sr-dev/pc-fftype0-doc) | *FINAL FANTASY TYPE-0 HD* — PSP heritage and the HexaDrive render layer |
| [**pc-talesofberseria-doc**](https://github.com/vs-sr-dev/pc-talesofberseria-doc) | *Tales of Berseria* (2017) — container format and obfuscation |
| [**pc-infiniteundiscovery**](https://github.com/vs-sr-dev/pc-infiniteundiscovery) | *Infinite Undiscovery* (tri-Ace, Xbox 360) and the ASKA engine |
| [**android-talesofcrestoria-doc**](https://github.com/vs-sr-dev/android-talesofcrestoria-doc) | *Tales of Crestoria* (Bandai Namco, 2020) — a dead gacha running on tri-Ace's **ASKA**, twelve years after the Xbox 360: the same `SLZ` container with Zstandard bolted on, the same texture header field-for-field in little-endian, Direct3D 9 shader profiles still sitting inside a GLES3 cache — and a shipped native library with 99.7% of its code zeroed out |
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
