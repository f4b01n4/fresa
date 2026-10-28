# Connect your machine

Fresa talks to **GRBL 1.1**, **grblHAL**, **FluidNC** and **Marlin**
controllers and detects which one is connected (it sends `$I`, then `M115`).
Open the **Machine** tab.

| Firmware | Card | How files get to the card | Overrides | Settings editor |
|---|---|---|---|---|
| FluidNC | yes | network (WebDAV) | yes | yes (new config file + restart) |
| grblHAL | if the board has one | — | yes | yes (`$` settings) |
| GRBL 1.1 | no | — (stream from the app) | yes | yes (`$` settings) |
| Marlin | if the board has one | over the cable (M28) | no | yes (M92/M203/M201 + M500) |

Without a card, jobs are **streamed** from the app line by line: keep the
computer awake and connected until the job ends.

## Network (Telnet) — recommended for FluidNC
Type: **Network (Telnet, port 23)**, address: the controller's IP (shown in its
WebUI) or `fluidnc.local`. Click **Connect**. You should see the firmware and
machine name under the buttons and positions updating.

## USB serial
Type: **USB serial**, pick the port (`/dev/cu.usbserial-…` on macOS, `COM3` on
Windows). If the Mac's trackpad goes erratic while the USB cable is plugged in,
the CNC's power supply is leaking to ground through USB: use the network link,
or the grounded (3-pin) Mac charger lead, or a USB isolator.

## First checks
1. **Homing** (needs limit switches).
2. Touch the two probe clips together: the **Probe** line must read
   **IN CONTACT**.
3. Jog with the arrows; check +X moves the spindle right, +Y away from you,
   −Z down.

## Which machine is it?
After connecting, Fresa shows the firmware it found and, if you have not chosen
a machine yet, suggests matching profiles from the **machine library**
(**Machines…**). Choosing one sets the travel used to check that jobs fit. The
built-in profiles show where their numbers come from; only those marked as
checked on a real machine were measured. Use **Make it mine** to copy a profile
and edit it; your machines are saved in the app data folder and can be
exported/imported.

## Machine settings
**Machine settings…** reads the controller's settings into one form for every
firmware: steps/mm, maximum speed, acceleration, travel, motor direction,
homing, limits, spindle range, probe input. Changed fields are highlighted;
**Apply** shows the list of changes first. Before writing anything Fresa saves
a copy of the current settings in the `machine-backups` folder of the app data.

- **GRBL / grblHAL / Marlin**: the changes are written straight away (Marlin
  also stores them with `M500`).
- **FluidNC**: Fresa writes a *new* config file (`fresa-<date>.yaml`) to the
  controller and selects it. Click **Restart controller now**: Fresa restarts
  it, reconnects and checks it came back with the new file. If it did not (an
  error in the file), **Use previous config** selects the old one again. Your
  original `config.yaml` is never overwritten.

Two helpers live in the same window:
- **Calibrate steps/mm**: jog a known distance, measure what the machine really
  moved, and Fresa computes the corrected value.
- **Check motor directions**: jog each axis a little in +; if it went the wrong
  way, one click inverts that motor.

## The SD card
Format it **FAT32** (cards above 32 GB come as exFAT and are not read). In the
**Card and run** section, set the controller's address (HTTP) and use **Upload** to
send the files; Fresa checks the sizes with `$SD/List`.

## Simulator
Choose **Simulator** to try everything without a machine, and pick which
firmware it imitates (FluidNC, GRBL 1.1, grblHAL or Marlin).
