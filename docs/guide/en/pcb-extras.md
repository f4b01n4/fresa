# Panels, copper clearing, hole checks and tool wear

## Panel (several copies)
**Job parameters → Panel (copies)**: set columns and rows. Every program
(isolation, clearing, holes, cut-out) covers all copies; the probe grid covers
the whole panel. The gap between boards must be at least the cut-out endmill
diameter + 2 mm, otherwise the cut-outs meet (Fresa warns). Each copy keeps its
own tabs.

## Copper clearing
**Copper clearing** removes the copper that is not part of any net, after the
isolation (`clearing.nc`, listed right after `isolation.nc`). The clearing tool
keeps its edge half an isolation cut away from the copper, so it overlaps the
isolation groove without touching the tracks.

- Use a 1 mm or larger endmill: clearing a whole board takes much longer than
  the isolation (the preview shows the time).
- **Only near the copper** clears a band of the chosen width around the
  copper instead of the whole board — faster, and usually enough for
  soldering.
- The stepover is limited to 50 % so no narrow strip is left uncut.
- It is levelled with the height map like the isolation.

## Hole checks
Before anything is cut Fresa checks the drill file against the board and
lists problems under **Warnings** (amber squares in the preview):
- two holes whose edges are closer than 0.2 mm (the web between them breaks);
- a hole closer than 0.3 mm to the board edge;
- a drilled pad left with less than 0.15 mm of copper ring.

## Tool images and wear
Tools are drawn from their numbers next to each tool choice, in the library
and in the checklist (V-bits show the cut width at the chosen depth).

Each library tool counts what it has cut: metres for V-bits and endmills,
holes for drills. The count goes up when a job ends (or by the part done when
it is stopped). If Fresa cannot tell which library tool was used, it asks.
The bar turns amber at 80 % of the expected life and red at 100 %; the
checklist warns too. After fitting a new bit, open **Tools…** and click
**Reset (new tool)**. The expected life is editable per tool (defaults: V-bit
30 m, endmill 50 m, drill 300 holes in FR4).
