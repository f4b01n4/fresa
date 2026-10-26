# Fresa

**Desktop CAM and machine control for hobby CNC routers** — PCB isolation milling
with probe autolevelling, cutting and engraving from DXF/SVG, and 3D reliefs from
STL models and pictures. Talks to GRBL 1.1, grblHAL, FluidNC and Marlin.

[Português](README.pt.md)

## Download

Go to **[Releases](../../releases/latest)** and pick the file for your system:

| System | File | Updates |
|---|---|---|
| macOS 11+ (Intel and Apple silicon) | `Fresa_<version>_universal.dmg` | in-app |
| Windows 10/11 | `Fresa_<version>_x64-setup.exe` (or `.msi`) | in-app (setup.exe) |
| Linux | `Fresa_<version>_amd64.AppImage` (or `.deb`) | in-app (AppImage) |

Once installed, Fresa checks for new versions itself and installs them with one
click (Settings → Updates) — no need to download again.

## First launch

- **macOS**: Fresa is not signed by Apple. Open it once, dismiss the warning,
  then System Settings → Privacy & Security → **Open Anyway** (or
  `xattr -dr com.apple.quarantine /Applications/Fresa.app`).
- **Windows**: SmartScreen may say "Windows protected your PC": **More info →
  Run anyway** (the installer is not code-signed).
- **Linux**: `chmod +x Fresa_*.AppImage` and run it. For USB serial access add
  yourself to the `dialout` group once: `sudo usermod -aG dialout $USER`, then
  log out and in.

## What it does

- **PCB**: KiCad Gerber/Excellon in, isolation / drilling / cut-out G-code out;
  tool-fit check, copper clearing, panels, double-sided boards, probe height map
  for warped blanks.
- **Cut & Engrave**: DXF and SVG; profiles with tabs, pockets, engraving,
  V-carving, drilling, for wood, MDF, acrylic and aluminium.
- **3D relief**: STL models and pictures; roughing and ball-nose finishing.
- **Machine**: connect by USB or network, detect the firmware, jog, zero, probe,
  run from the SD card or stream, live progress, stop and resume, machine
  settings editor, tool library with wear counter. English and European
  Portuguese.

This repository only hosts the released builds. The source code is not public.

© 2026 Fresa. The binaries are free to download and use; see [LICENSE](LICENSE).
