# Troubleshooting

| Symptom | Cause and fix |
|---|---|
| The machine stops answering after editing `config.yaml` | FluidNC does not accept comments after a value on the same line. Connect over USB, send `$SS` to read the errors, then `$Config/Filename=<previous file>` and `$Bye`. |
| "No SD card" | The card is exFAT. Format it FAT32 (MS-DOS FAT, Master Boot Record on macOS). |
| Isolation is clean in some areas and only scratched in others | The blank flexes or moved. Stick it over the whole area, re-probe, use **Retouch area**. |
| ALARM:14 | The machine needs homing (`$H`). |
| ALARM:5 while probing | Nothing was touched within the search distance: clip not on the copper, or the point is on an isolated copper island. |
| Trackpad goes erratic with USB | Ground leakage from the CNC supply; use the network link. |
| The map range is above 0.3 mm | The board is not flat on the bed; fix it better before cutting. |
| Pads and tracks come out much narrower than drawn, some cut through, even with a flat board | The groove is wider than the app thinks: spindle or collet runout makes a "0.1 mm" V-bit cut 0.3–0.5 mm wide. Run `fixtures/calibration/vbit-grooves.nc` on a free copper area (zero XY there, Z with the probe), measure the 6 grooves under a microscope and put the width of the shallowest one as the **tip diameter** of that V-bit in Tools…. Lower the depth to 0.05 mm. Gaps narrower than the real cut are then cut down the middle (Result lists them). Clean and re-seat the collet; a 2–4-flute conical V-bit runs truer than a single-flute "D" bit. |
