# Double-sided boards

Needs F.Cu, B.Cu and Edge.Cuts. Turn on **Double-sided** in the parameters.

- Two alignment pins sit on the board's horizontal centre line, outside the
  board by default (pin Ø 3.175 = the shank of a broken bit).
- The board flips **left to right** (about an axis parallel to Y). Fresa
  mirrors the bottom layer about the board centre, so the pins land in the same
  holes and the XY zero does not move.
- Top side: isolation, drilling, milled holes and `alignment.nc` (through the
  board and a little into the spoilboard). Bottom side: mirrored isolation and
  the cut-out.
- Each side has its own height map: probe again after flipping.

The **Result** tab shows the step-by-step guide with your job's numbers and the
current step highlighted.
