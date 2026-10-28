# Install

## macOS
1. Open the `.dmg` and drag **Fresa** to Applications.
2. Fresa is not signed by Apple. On the first launch:
   - **macOS 15 or later:** open it once, dismiss the warning, then System
     Settings → Privacy & Security → **Open Anyway**. Or in Terminal:
     `xattr -dr com.apple.quarantine /Applications/Fresa.app`
   - **macOS 14 or earlier:** right-click → Open → Open.
3. Click the gear icon (top right) to choose the language.

## Windows
Run `Fresa_<version>_x64-setup.exe`. SmartScreen may say "Windows protected
your PC": **More info → Run anyway** (the installer is not code-signed). USB
serial ports appear as `COM3`, `COM4`… (install the CH340/CP210x driver of your
board if none shows up).

## Linux
Use the **AppImage** (it updates itself): `chmod +x Fresa_*.AppImage` and run
it. A `.deb` is there too, updated by your package manager. For USB serial
access add yourself to `dialout` once: `sudo usermod -aG dialout $USER`, then
log out and in.

## Coming from pcbmill
Your tool library is copied on the first launch. Project folders keep working:
Fresa reads `pcbmill.json` and `pcbmill.heightmap*.json` and writes
`fresa.json` / `fresa.heightmap*.json` from then on.

## Updates
Fresa checks for updates on start (Settings → Updates) and installs them in
place with one click — macOS, Windows (setup.exe installs) and the Linux
AppImage. Updates are signed; Fresa refuses anything else.
