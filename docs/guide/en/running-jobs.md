# Running a job

## Before every run: the checklist
**Run** opens a checklist. Fresa checks what it can (homed this session, work
zero set, Z zeroed with the probe recently, height map applied and its range,
the toolpaths inside the machine travel, probe clip removed, the file on the
card is the one you exported) and asks you to tick the rest (the mounted tool,
the collet nut, the spindle). Red items need a second click to run anyway.

## While it runs
- The **preview** shows the tool live (colour = machine state) with a short
  trail; the paths already cut turn green and the current one yellow.
  **Follow tool** keeps it in view.
- The **Machine** tab shows the percentage, the current path, the time elapsed
  and the time left (corrected by the real pace after the first minute).
- **Overrides**: feed and spindle ±10 % (100 % resets), rapids 25/50/100 %.
  They act immediately, without stopping the job.
- Jobs started from the WebUI or the controller's screen are followed too when
  the file name matches one of the open project's files.

## Stopping and resuming
**Stop job** pauses and resets the controller. Fresa remembers the path where it
stopped: *Resume from path* → **Make the resume file** creates
`…-resume-N.nc` (same tool and parameters, starting at path N). Home, check the
zero, upload it and run it. An alarm or a lost connection during a job is
recorded the same way.

## Switching off and continuing the next day
Fresa keeps the work zero (G54), the Z reference and where the job stopped in the
project's `fresa.json`. Next day: connect, **Homing**, then in the *Saved
session* box **Check saved zero** (the controller usually still has it) or
**Restore saved zero**, and **Check Z at the reference** (one probe touch: if it
reads more than 0.05 mm off, the board or the tool moved — zero Z again).
Needs homing switches; without them, mark the position before switching off.

## Verify map
Before a long isolation job, **Verify map** probes the four corners and the
centre again and compares with the map; more than 0.1 mm means re-probe.

## Keyboard jog and the ruler
Turn on *Jog with the keyboard*: arrows move X/Y, Page Up/Down move Z, `[` and
`]` change the step, Esc stops. **Measure** in the preview toolbar: drag to get
the distance, ΔX, ΔY and the angle (snaps to hole centres).
