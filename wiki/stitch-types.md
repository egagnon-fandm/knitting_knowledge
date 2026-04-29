# Stitch Types

**Summary**: The two elementary stitches — knit (K) and purl (P) — combine into four canonical fabric patterns (stockinette, garter, rib, seed) with distinctly different mechanical responses determined by the symmetry of yarn segments connecting neighboring stitches.

**Sources**: `raw/Singal_NatureComm_2024.pdf`, `raw/Poincloux_PRX_2018.pdf`, `raw/notes_for_Tim.pdf`, `raw/Knitting Science, Technology, Process and Materials.pdf`

**Last updated**: 2026-04-13

---

## Elementary stitches

### Knit stitch (K, front stitch)
Formed by passing a loop of yarn from the **back to the front** of the fabric through an existing loop.

### Purl stitch (P, back stitch)
Formed by pulling a loop from the **front to the back**. Geometrically, a purl is a knit rotated 180° about the fabric's y-axis (the wale direction). They are fundamentally the same object.

## Four canonical fabrics

### Stockinette (plain knit, jersey)
- **Pattern**: All Ks on one face (rows of KKKK…)
- **Symmetry**: Even connecting yarn segments in **both** x (course) and y (wale) directions
- **Mechanics**: Stiffest in the course direction of the four fabrics; strong anisotropy
- **Shape**: Characteristic catenary form; curls at edges when unloaded (source: Poincloux_PRX_2018.pdf)
- **Visual**: Smooth V-shaped stitches on one face, bumpy on the other

### Garter (links-links)
- **Pattern**: Alternating rows of Ks and Ps (KKKK… / PPPP…)
- **Symmetry**: Even segments in x, **odd** segments in y
- **Mechanics**: Softer in y (wale) direction due to odd segments; stiffer in x. Lies flat.

### Rib (1×1 rib)
- **Pattern**: Alternating columns of Ks and Ps (KPKP… in each row)
- **Symmetry**: **Odd** segments in x (course), even segments in y (wale)
- **Mechanics**: By far the softest in the x (course) direction — extreme extensibility. Stiffest in y among the softer fabrics.

### Seed
- **Pattern**: Checkerboard of Ks and Ps (KPKP… / PKPK…)
- **Symmetry**: **Odd** segments in **both** x and y directions
- **Mechanics**: Softest overall; nearly isotropic. Only odd connecting segments.

## Even and odd connecting yarn segments

This classification is the key microscopic insight of Singal 2024 (see [[stitch-topology]]):

- **Even symmetry** (K-K or P-P neighbors): The connecting yarn segment must curve to accommodate extension → stiffer spring (~$180B/\lambda^3$)
- **Odd symmetry** (K-P or P-K neighbors): The segment can rotate as a moment arm → softer by ~10× (~$12B/\lambda^3$)

This explains why fabrics with only odd segments (seed, rib in course direction) are far more extensible than those with only even segments (stockinette).

## Interlock fabric

A fifth canonical weft-knit structure not included in the Singal 2024 four-fabric study but important industrially (source: Jamshaid & Mishra 2024):

- **Pattern**: Two interlocked rib structures; formed on double-bed circular machine using two feeds
- **Construction**: Alternate needles knit in each feed, so dial/cylinder needles are directly opposite (unlike rib, where they alternate)
- **Mechanics**: More stable and dimensionally rigid than single jersey or rib; requires more force to deform. Front/back loops are directly opposite → deformation of one loop is resisted by the opposite loop
- **Elongation**: Coursewise elongation less than rib; walewise extension also less than coursewise
- **Application**: More suitable for technical textiles due to dimensional stability

The textbook mechanics hierarchy: Interlock > Jersey > Seed ≈ Garter > Rib for dimensional stability; reversed for extensibility in course direction.

## Simulation unit cells

In yarn-level simulations (see [[yarn-simulation]]), each fabric type is simulated as a periodic unit cell containing a defined set of cross-overs and connections:

- **Stockinette**: 2 cross-overs (parity 0 and 1), 4 connecting curves
- **Garter, rib, seed**: larger unit cells reflecting their longer repeat pattern

## Related pages

- [[knitted-fabrics]]
- [[stitch-topology]]
- [[knit-elasticity]]
- [[wale-and-course]]
- [[yarn-simulation]]
- [[singal-naturecomm-2024]]
- [[poincloux-prx-2018]]
- [[jamshaid-mishra-2024]]
