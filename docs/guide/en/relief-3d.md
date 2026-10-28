# 3D relief (STL and pictures)

The **3D relief** workspace carves a relief — a sign, a medallion, a
topographic map, a lithophane-like picture — from an **STL model** or a
**PNG/JPG picture**: roughing with a flat endmill, then finishing with a
ball-nose endmill.

## 1. Open the model
- **STL** (binary or ASCII; Printables, Thingiverse, your CAD): Fresa looks at
  it from above. Turn it in 90° steps about X, Y or Z until the side you want
  faces up; set the scale (100 % = file units as mm; **File is in inches** for
  inch models) or **Fit to stock**.
- **Picture**: light parts stay high, dark parts are cut deepest (**Dark =
  high** inverts it). Set the width and the depth of black; gamma shapes the
  curve, smoothing removes JPEG noise.

Then place it on the stock, and choose how far below the stock top its highest
point sits (0 = touching the top). **Detail** is the grid the surface is
sampled on (0.1 mm suits a 3 mm ball; finer is slower).

## 2. Stock and area
Material (feeds come from the tool library), size, thickness, Z0 (top of the
stock or the spoilboard). **Cut area**: the whole relief rectangle, or only
the model's silhouette (plus a margin), leaving the stock around it untouched.

## 3. Roughing and finishing
- **Roughing** (flat endmill): removes material in Z levels of the step-down,
  clearing each level with concentric passes, and stops a little above the
  final surface (**Leave for finishing**, 0.3 mm by default). It never cuts
  into that skin.
- **Finishing** (ball-nose endmill, add one in **Tools…** with **Ball nose**
  ticked): parallel passes along X, Y or both; the stepover follows from the
  **scallop height** you accept between passes (0.02 mm is smooth in wood).
  The tool follows the surface exactly where it can reach it (the ball's radius
  limits how sharp a hollow can be).

Programs: `relief-roughing.nc` and `relief-finishing.nc`. Big reliefs take a few
seconds to compute — the progress shows under the preview, with **Cancel**.

## 4. Run
As for every workspace: **Result** saves the files next to the model, the
**Machine** tab runs them (card or streaming, checklist, progress, stop and
resume, tool wear). 3D reliefs are **not levelled** with a height map: face the
stock top first (**Machine → Surfacing**) so Z0 is flat. Settings are saved
next to the model as `<name>.relief.fresa.json`.
