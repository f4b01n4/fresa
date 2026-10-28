# Your first PCB

## 1. Export from KiCad
Plot → Gerber, X2 format, mm. Layers **F.Cu** and **Edge.Cuts**. Generate the
Excellon drill files in mm (decimal). Also generate the job file (`.gbrjob`):
it carries the board thickness.

## 2. Open the folder
**Open folder…** and check that each file has the right role.

## 3. Parameters
- **Material** and **Tools…** (the library) set sensible feeds.
- Watch the **Cut width**: it must fit between your closest pads. If the result
  panel shows a red "the tool does not fit" box, reduce the depth or use a
  narrower V-bit. Click a warning to zoom to it.

## 4. Fix the blank flat
Stick it with double-sided tape over the **whole** area on a flat spoilboard
(Machine → *Surface the spoilboard* makes one flat). A board that flexes under
the probe cannot be levelled.

## 5. Zero and probe
Machine tab: **Homing**, jog the bit to the board's bottom-left corner 1–2 mm
above the copper, **Zero XY here**, clip on the copper and wire on the bit,
**Zero Z with the probe**, then **Probe grid**. The range should stay below
0.3 mm; above it, fix the board better.

## 6. Run
With **Apply on export** on, **Upload** the files and **Run** them one at a
time: isolation, drilling, milled holes, cut-out. After every tool change,
**Zero Z with the probe** again (or use the [single file](combined-file.md)).

## 7. If an area came out shallow
In the preview, **Retouch area**, drag a rectangle over it and run
`isolation-retoque.nc`: only that area, a little deeper.
