# Cut & Engrave (DXF and SVG)

The **Cut & Engrave** workspace (top bar) turns a 2D drawing into programs for
wood, MDF, acrylic or light aluminium work: cutting parts out, pockets,
engraving, V-carving and drilling.

## 1. Open the drawing
**Open DXF/SVG…**. Supported:
- **DXF** (LibreCAD, FreeCAD, Fusion, AutoCAD, QCAD…): lines, arcs, circles,
  polylines (with arcs), splines, ellipses and blocks. Units come from the file;
  if it does not say, choose mm or inch. Loose segments are joined into closed
  shapes automatically (ends within 0.01 mm).
- **SVG** (Inkscape, Illustrator…): paths, rectangles, circles, ellipses,
  lines, polygons, groups and transforms. Sizes in mm/cm/in are exact; sizes in
  pixels need the right DPI (96 for Inkscape and browsers, 72 for older
  Illustrator files). Inkscape layers become layers.
- **Text is not imported**: convert it to curves first (Inkscape: Path →
  Object to Path).

The layers list shows what came in; untick a layer to hide it.

## 2. Stock
Material (wood, MDF, acrylic, aluminium — the feeds come from the tool
library for that material and are **starting points**: tune them on scrap),
size and thickness, where the drawing sits on it, where X0 Y0 is (stock corner,
stock centre or the drawing's own origin) and where Z0 is (top of the stock, or
the spoilboard). A new drawing gets stock 10 mm larger than it all round.

## 3. Operations
Add operations with the buttons; each takes the paths of chosen layers, or
paths you click in the preview (**Pick in the preview**, shift-click adds).

| Operation | What it does |
|---|---|
| Profile | Cuts along shapes: **outside** (the part), **inside** (a hole) or **on the line**, in depth steps, with tabs, ramped entry, climb or conventional direction, optional allowance |
| Pocket | Clears the inside of closed shapes; shapes inside shapes stay as islands; the wall pass is last |
| Engrave | Follows the lines at a depth (open lines too) |
| V-carve | Clears closed shapes with a V-bit at one depth, so the edges get the V's bevel (true variable-depth V-carving comes later) |
| Drill | Drills the circles (with a drill), or mills them as a helix (with an endmill), filtered by diameter |

Whatever order you list them in, the programs run engrave → V-carve → drill →
pocket → inside profiles → outside profiles, so the part comes loose last.
Each operation is one file, `01-engrave.nc`, `02-profile.nc`, ….

**Simulate** in the preview shows the cut up to a point in time.

## 4. Run
The **Result** tab saves the `.nc` files next to the drawing; the **Machine**
tab works exactly as for PCBs: card or streaming, checklist, progress, stop and
resume, tool wear. Settings are saved next to the drawing as
`<name>.fresa.json`.

On uneven stock you can probe a height map (it needs a conductive surface or a
probe) and tick **Follow the height map**: every program then follows the
surface.
