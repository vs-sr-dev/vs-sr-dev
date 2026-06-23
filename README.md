# Silicon Relics

Cross-console preservation research and homebrew development for **obscure and failed vintage platforms** — the machines that flopped, got cancelled, or were never documented, and so have almost no public technical record.

The work here is a long-running solo effort assisted by Claude (Anthropic). The goal is concrete: take technical knowledge that exists nowhere else — compiler bugs, hardware register maps, undocumented drivers, emulator internals — and make it **publicly verifiable** for the people who come after. For several of these platforms, these repositories are the only public documentation of their kind.

---

## Featured work

Three documentation repositories, each covering a platform with essentially no prior public reverse-engineering record:

### 🎮 [hyperscan-homebrew](https://github.com/vs-sr-dev/hyperscan-homebrew)
**Mattel HyperScan (2006)** — Sunplus S+Core 7, RFID cards, a total commercial flop.
16+ reproducible bugs in the unmaintained GCC `score-elf` backend with verified workarounds; the PPU, RFID-NFC and I²C drivers written from scratch; and the **first-ever emulated HyperScan audio in MAME** ([video](https://www.youtube.com/watch?v=1vh_27eTpfc)).

### 🕹️ [ngpc-homebrew-notes](https://github.com/vs-sr-dev/ngpc-homebrew-notes)
**SNK Neo Geo Pocket Color (1999)** — Toshiba TLCS-900/H.
A verified toolchain setup and binary inventory, plus the **first NGPC↔Dreamcast link-cable bridge ever implemented in emulation** — hardware that saw retail use in 1999 but had never been emulated on either side ([homebrew test](https://www.youtube.com/watch?v=x2IV3T3Z0oM) · [retail test](https://www.youtube.com/watch?v=mmxnnkZzu-s)).

### 🍎 [pippin-homebrew](https://github.com/vs-sr-dev/pippin-homebrew)
**Bandai Pippin @WORLD (1996)** — Apple-licensed PowerPC 603.
Upstreamable fixes to the **DingusPPC** emulator (GPLv3) that gave it working serial-over-DBDMA and **put the emulated Pippin on the real Internet** (ping + a live web page in Netscape) — plus a homebrew thin-client browser, and an honest, `tcpdump`-backed account of the one symptom that turned out *not* to be the emulator's fault.

---

## The wider Silicon Relics project

These three are part of a larger body of cross-console work spanning several years and many platforms — an analog-horror ARG series and the homebrew/reverse-engineering that underpins it:

- **SR1** — mid-90s home consoles (Sega Saturn, 3DO, Amiga CD32, Atari Jaguar).
- **SR2** — Sega Dreamcast, PlayStation 2, and HyperScan; includes world-first homebrew on the **Casio Loopy**.
- **SR3 (Gaiden)** — forgotten handhelds (Neo Geo Pocket Color, Game.com, Atari Lynx, WonderSwan Color).
- **SR4** — exploratory work on the Bandai Playdia, Tandy/Memorex VIS, Philips CD-i, and Bandai Pippin.

The three repositories above are where that work is documented publicly first.

---

## On method and attribution

This is a human + LLM collaboration, stated openly because the honesty is the point. **Claude acts as a technical bridge:** I bring decades of domain knowledge and direction — knowing these platforms, recognising when a result is a genuine first, and deciding where it's worth digging — and Claude provides implementation across architectures I could not otherwise approach: the drivers, the emulator patches, the disassembly and log forensics, the documentation. Neither side reaches these results alone.

I'm a professional technical translator, a field heavily affected by AI, and I hold a deliberate position about it: AI used for **net-new work that displaces no one** — reverse-engineering an abandoned console that nobody else was working on — is the case worth defending. Visibility of the collaboration is part of that argument, not a disclaimer.

— **[@vs-sr-dev](https://github.com/vs-sr-dev)**
