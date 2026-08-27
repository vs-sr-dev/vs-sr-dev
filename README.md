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
| [**pc-corridor7-doc**](https://github.com/vs-sr-dev/pc-corridor7-doc) | *Corridor 7: Alien Invasion* (Capstone / IntraCorp, 1994) — a licensed **Wolfenstein 3-D** taken to 256 colours, shipping its levels in TED5's `TED5v1.0` **editor work file** with the map directory linked into the EXE; the MUSE tags still carry each track's source name and MS-DOS timestamp, dating the whole soundtrack to the day — and ten credit sprites hang along a corridor on level 1 |
| [**pc-hurl-doc**](https://github.com/vs-sr-dev/pc-hurl-doc) | *H.U.R.L.* / *Slob Zone 3D* (Deep River Publishing, 1995) on Lary Myers’ **ACK-3D** — the first rung of the ladder that ends at 3D GameStudio. Levels ship as commented ASCII source naming 661 of the game’s 684 bitmaps by their original artist file names; capitalisation alone separates the engine’s parser keywords from the eleven the studio bolted on; every projectile is parked in a sealed room off the edge of the map because the engine allocates nothing at run time. Disassembling the DOS/4GW image settled the rest: a level-select and arbitrary-file-load switch in the retail build, an objective system wired up and never switched on, three unshipped “editions” still in the title archive — and a direction comment the designers followed that the engine disagrees with, so every “90°” in the data renders as 96° |
| [**pc-mm-doc**](https://github.com/vs-sr-dev/pc-mm-doc) | *Might & Magic: Secret of the Inner Sanctum* (1987) |
| [**pc-sargon5-doc**](https://github.com/vs-sr-dev/pc-sargon5-doc) | *Sargon V: World Class Chess* (Mediagenic, 1991) — the PC front end around the Spracklens' engine. Five files with four different extensions turn out to be **one container**, whose LZW is packed **least-significant bit first** where every LZW you have met packs the other way: read it MSB-first and the first screen yields 955 plausible bytes before falling apart, read it backwards and it lands on exactly 64,000. There is no EGA art and no Tandy art — every palette block carries 768 bytes of VGA values **plus** a 768-byte 256-to-16 dither table, so one 8-bit asset set drives all four displays, and one of the four drivers is a **hand-written Tandy 1000 SL/TL 640×200×16** that never calls the BIOS. Every game, lesson and puzzle in the release is the same 512-byte record whose move stream is one byte per half-move — decoded by counting openings: 113 games from the initial position take exactly four first-byte values, and they are 1.e4, 1.d4, 1.Nf3 and 1.c4 in the right proportions. The tutorial lessons are **decision trees**, 258 anticipated mistakes each with its own coaching line for a twenty-turn game, and their plain-text **authoring sources shipped** in a directory the file dialog cannot list. Also: an unused ASCII board importer, a Game Blaster driver with no command-line switch, a programmer credited only as **Dr. Destructo**, and an About box that — with `h` held down — signs itself *Hamster Gone Bad Productions* and, three stages later, replaces the white king with a hamster |
| [**pc-nitemare3d-doc**](https://github.com/vs-sr-dev/pc-nitemare3d-doc) | *Nitemare-3D: A House of Horrors* (David P. Gray, 1994) — a one-man 256-colour shooter that owes **nothing** to Wolfenstein: every format is Gray's own and **none of it is compressed**, because the engine demand-pages its art through a three-tier cache (conventional RAM / XMS / disk) that keeps its own reload and thrash counters. Images are stored **column major** and a wall block carries **two different textures** rather than a light/dark pair. The encrypted `.BSF` gave up the only **credits** in the release — its cipher is a 52-byte repeating XOR whose phase **restarts at every chunk**, which is why the file resists the obvious attack and folds instantly once you read the four-instruction decoder. An artist's placeholder shipped in the retail data as a wall reading *"See file TILES007.PCX"* — unreachable, and 8 KB of it in every copy |
| [**cdi-ultracdisoccer-doc**](https://github.com/vs-sr-dev/cdi-ultracdisoccer-doc) | *Ultra CD-i Soccer* (Krisalis / Philips Interactive Media, 1997) — a Green Book disc that is **2.4 % full and compresses nothing**: every background is a raw CLUT plane, and the one coded format is a run-length sprite the executable still calls `rlspr` in a path string pointing at a file that was dropped. In front of the file system sit **2,269 valid Mode 2 Form 2 sectors whose user data is the ECMA-130 scrambler sequence** — XOR it out and 1,064 are zeroes while 1,203 become 15.7 s of 44.1 kHz PCM, mono in a stereo container, left identical to right in all 692,928 frames; the padding at the *other* end of the disc is plain zeroes, so two different filler mechanisms are at work in one image. **Ten per cent of the file system is empty files** — German, French and Spanish screens shipped as 1,070,080 bytes of zero, their palettes real and their pictures never drawn. The executable asks for **`/segalogo_gfx`**, the abandoned art is **320×224** (a Mega Drive PAL frame, not a CD-i one) and the credits thank **Cross Products**, whose SNASM systems were the British Sega toolchain; two of those files are the **Manchester United club crest** and a third a licensed trophy photograph, in a game that renames Ian Wright to *Ian Write*. The developers put **Rotherham United** — the only correctly-spelled squad on the disc — and **themselves** in the team database, next to a joke side from *FUG land* with every attribute at 100. Also shipped: a **placeholder copyright** (“La di da … Put some copyright … Message crap in here or something”), the string system’s own unprintable error message, `CHEAT MODE ON`, an IBM **CP437** font on a 68000 running OS-9, and eight named pieces of music with no file to play |
| [**cdi-origami-doc**](https://github.com/vs-sr-dev/cdi-origami-doc) | *Origami* (EagleVision interactive productions, 1993) — the opposite end of the CD-i format from *Ultra CD-i Soccer*: a disc **98 % full** in which **52 sectors out of 326,400** are the file system and the program, and everything else is multi-channel real-time video and audio. The disc is catalogued `(En,Fr,De,Nl)` and carries **five** ADPCM narration channels, a five-entry language menu and five localised disc-error screens — the fifth is **Japanese**, four hours of narration nobody wrote down. **Every photograph is stored twice**, once per video standard (384×193 PAL, 384×167 NTSC — 69 % of the picture height in both), so **21.7 % of the pressing is video the player in front of you will never read**; frame *k* of one channel correlates 0.88 with frame *k* of the other against 0.6–0.75 with its neighbours. The 5.2 MB in front of the file system descrambles to **29 s of 44.1 kHz speech no file references**, and the recovered audio jumps at every sector boundary by exactly a **six-frame gap — the 24 bytes of sync, header and subheader** the authoring system laid over each block of a CD-DA stream. Inside the binary, before any code, the **Philips base-library author list** (`M.Armendariz,…,J.Piesing,…`) rides along as a free toolchain fingerprint for any CD-i disc. Also shipped: a **video-plane hex dumper** still linked into the retail executable, `model2` and `model3` with no `model1`, three spellings of the publisher's own name — one of them inside the copyright notice — an `abstract` field reading **“ORIGAMI is great!”**, and a root file, referenced by nothing, holding the programmer's home address |
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
