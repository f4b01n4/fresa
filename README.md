<h1 align="center">Fresa</h1>

<p align="center">
  <strong>Desktop CAM and machine control for hobby CNC routers.</strong><br>
  Mill PCBs that actually work on a cheap 3018, cut and engrave from DXF/SVG, carve 3D reliefs from STL and pictures —
  and run it all from one app that talks to GRBL, grblHAL, FluidNC and Marlin.
</p>

<p align="center">
  <a href="../../releases/latest"><img alt="Latest release" src="https://img.shields.io/github/v/release/f4b01n4/fresa?include_prereleases&label=download&color=5b9cff"></a>
  <a href="../../releases"><img alt="Downloads" src="https://img.shields.io/github/downloads/f4b01n4/fresa/total?color=3ec46d"></a>
  <img alt="Platforms" src="https://img.shields.io/badge/macOS%20%7C%20Windows%20%7C%20Linux-free-f0b33a">
  <a href="README.pt.md"><img alt="Português" src="https://img.shields.io/badge/🇵🇹-Português-lightgrey"></a>
</p>

<p align="center">
  <a href="../../releases/latest"><b>⬇ Download</b></a> ·
  <a href="docs/guide/en/README.md"><b>User guide</b></a> ·
  <a href="docs/guide/pt/README.md">Guia em português</a> ·
  <a href="../../issues">Report a problem</a>
</p>

<p align="center"><img src="docs/images/pcb.png" alt="Fresa — PCB workspace with the tool-fit check" width="900"></p>

## Why Fresa

Milling a PCB on a hobby machine fails for boring reasons: the blank is 0.2 mm warped
so a V-bit at 0.08 mm cuts air on one side and through the copper on the other; two
pads are closer than the cut, so they stay shorted; the spindle has runout and the groove
is three times wider than the catalogue says. Fresa was built on exactly such a machine
and deals with those things instead of pretending they don't happen:

- **Probe height map** — probe a grid on the copper, and every toolpath follows the
  surface. Verify the map, re-probe Z at tool changes, retouch one area that came out shallow.
- **Tool-fit check** — before cutting, Fresa shows where copper is closer than the cut
  width. Narrow gaps get a single cut down the middle instead of a short.
- **Real machine control** — connect by USB or network, detect the firmware, home, jog,
  zero, probe; run from the SD card or stream from the app; live position, progress and
  time left; stop and resume mid-file or the next day.
- **One pipeline for everything** — PCBs, 2D cutting/engraving and 3D reliefs share
  the same tool library, machine link, checklist and wear counter.

## What it does

| | |
|---|---|
| **PCB** — KiCad Gerber/Excellon in; isolation, drilling, milled holes and slots, cut-out with tabs, copper clearing, panels, double-sided boards with alignment pins, combined file with tool-change pauses. | <img src="docs/images/pcb.png" width="420"> |
| **Machine** — GRBL 1.1, grblHAL, FluidNC, Marlin. Firmware detection, machine library, settings editor with backup, feed/spindle overrides, pre-cut checklist, live view. Simulators for all four firmwares to try everything without a machine. | <img src="docs/images/machine.png" width="420"> |
| **Cut & Engrave** — DXF and SVG; profiles with tabs and ramps, pockets with islands, engraving, V-carve, drilling; wood, MDF, acrylic and aluminium presets; simulate before cutting. | <img src="docs/images/cut-engrave.png" width="420"> |
| **3D relief** — STL models and PNG/JPG pictures; roughing with a flat endmill, finishing with a ball-nose, shaded preview. | <img src="docs/images/relief.png" width="420"> |

Interface and guide in **English** and **European Portuguese**.

## Install

Download from **[Releases](../../releases/latest)**:

| System | File | Updates |
|---|---|---|
| macOS 11+ (Intel and Apple silicon) | `Fresa_<version>_universal.dmg` | in-app |
| Windows 10/11 | `Fresa_<version>_x64-setup.exe` (or `.msi`) | in-app (setup.exe) |
| Linux | `Fresa_<version>_amd64.AppImage` (or `.deb`) | in-app (AppImage) |

Fresa checks for new versions itself and installs them with one click
(Settings → Updates). Updates are signed; anything else is refused.

**First launch**

- **macOS**: Fresa is not signed by Apple. Open it once, dismiss the warning, then
  System Settings → Privacy & Security → **Open Anyway**
  (or `xattr -dr com.apple.quarantine /Applications/Fresa.app`).
- **Windows**: SmartScreen may say "Windows protected your PC": **More info → Run anyway**.
- **Linux**: `chmod +x Fresa_*.AppImage` and run it. For USB serial access:
  `sudo usermod -aG dialout $USER`, then log out and in.

## Getting started

1. Open the app, pick **Simulator** in the Machine tab and press Connect: you can try
   every feature with no hardware.
2. Export Gerbers from KiCad (File → Fabrication Outputs), **Open folder…** in Fresa.
3. Read [Your first PCB](docs/guide/en/first-pcb.md) — ten minutes, and it covers the
   things that ruin boards.

Full guide: [English](docs/guide/en/README.md) · [Português](docs/guide/pt/README.md).

## Hardware it was made on

A Two Trees TTC3018Pro with an MKS DLC32 running FluidNC, a 30° V-bit, 1 mm bits, a
crocodile-clip probe. If it works there, it works on most 3018-class machines; bigger
machines (Genmitsu 4040, LongMill, Shapeoko) are in the machine library.

## Feedback

Found a bug, have a board that comes out wrong, own a machine Fresa should know?
Open an [issue](../../issues) — a screenshot of the Result tab and the console log
(Machine → Console → Copy) is usually all that's needed.

---

This repository hosts the released builds and the documentation. The source code is
not public. © 2026 Fresa — the binaries are free to download and use; see [LICENSE](LICENSE).
