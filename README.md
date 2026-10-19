# parts
KiCad symbol, footprint and 3D-model library shared by all projects.

## Layout
| Folder | KiCad library | What goes here |
|---|---|---|
| `symbols/` | **`Parts`** (symbol lib, folder type) | One `.kicad_sym` file per symbol, file name = symbol name. KiCad loads every file in this folder as one library; **sub-folders are not loaded**, so keep it flat. |
| `parts.pretty/` | **`parts`** (footprint lib) | One `.kicad_mod` per footprint. Do not rename existing footprints: projects (Lucca58, Badge2026, Lazy-Kiwi, ...) link to them by name, and some project `fp-lib-table`s point straight at this folder. |
| `3dmodels/` | – | STEP models, referenced from footprints as `${MAKA_PARTS}/3dmodels/<file>.step`. |
| `tools/` | – | Helper tools (e.g. `kiswitch` key-switch footprint generator). Not a library. |
| `_archive/` | – | Retired files kept for reference (old/broken symbols, backups, stock duplicates). Safe to delete. |

`MAKA_PARTS` = `/home/maka/PCBs/parts` is set in KiCad *Preferences → Configure Paths*; the global
`sym-lib-table` / `fp-lib-table` use `${MAKA_PARTS}/symbols` and `${MAKA_PARTS}/parts.pretty`.

## Conventions
- **Symbols** are named after the orderable part number (`CS43131-CNZ`, `TPS62840DLC`).
- **Footprints** are named after the package (`Texas_RGT0016C_VQFN-16-1EP_3x3mm_P0.5mm_EP1.68x1.68mm`), so parts can share them.
- Every symbol sets **Footprint** (`parts:<name>` or a stock `Library:<name>`), **Datasheet** and **Description**.
- Don't copy stock KiCad symbols/footprints unless they are modified; reference the stock library instead.
- Vendor downloads: put the symbol in `symbols/`, the footprint in `parts.pretty/`, the model in `3dmodels/`,
  then fix the symbol's Footprint field to `parts:<footprint>` (vendor files use their own library nickname).
