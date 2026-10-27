# Example finite-element case

This folder contains **one authentic example case** from the local dataset used for the manuscript. It is a single-heating-line, 300 × 300 × 8 plate case with 3,721 point samples. It is **not** the full training, test, or validation dataset and is not sufficient on its own to reproduce the paper's aggregate results.

## Files

| File | Shape | Meaning |
| --- | --- | --- |
| `point_features.npy` | `(3721, 9)` | Initial point coordinates and line-relative mask/distance features |
| `disp.npy` | `(3721, 3)` | Three displacement components, row-aligned with the point features |
| `global_features.npy` | `(13,)` | Plate geometry and heating-process parameters |
| `meta.json` | — | Feature names, process values, and deduplication information |

All three NumPy arrays are `float32`. The numerical array files were copied unchanged from the source case; their Git blob hashes were checked after upload. The only change to `meta.json` was removal of a local absolute source path and normalization of the relative output path.

### Point-feature columns

`[x, y, z, mask1, dist1, mask2, dist2, mask3, dist3]`

The three slots refer to the left, middle, and right heating lines. For an existing line, its mask is 1 and `dist = x - x_line`; for an absent line, both mask and distance are 0. The spatial coordinates and displacements retain the source simulation's units.

### Global-feature columns

`[plate_length, plate_width, plate_thickness, num_lines, x_left, x_mid, x_right, temp_left, temp_mid, temp_right, speed_left, speed_mid, speed_right]`

The full process values for this case are also listed in `meta.json`. Inactive line slots have zero-filled numeric values.

## Quick check

```python
import numpy as np

points = np.load("point_features.npy", allow_pickle=False)
displacement = np.load("disp.npy", allow_pickle=False)
process = np.load("global_features.npy", allow_pickle=False)

assert points.shape == (3721, 9)
assert displacement.shape == (3721, 3)
assert process.shape == (13,)
print(points[0, :3], displacement[0], process)
```

The array rows preserve their original pairing and deduplication order. Please do not interpret this example as release of all 22,620 cases reported in the manuscript.
