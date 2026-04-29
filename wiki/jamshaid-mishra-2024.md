# Jamshaid & Mishra (eds.) — Knitting Science, Technology, Process and Materials (2024)

**Summary**: Edited textbook covering industrial knitting from fundamentals through mechanics, with chapters on yarn selection, weft knitting machines, fabric structure, mechanics of weft-knitted fabrics, dyeing, quality control, and technical applications.

**Sources**: `raw/Knitting Science, Technology, Process and Materials.pdf`

**Last updated**: 2026-04-13

---

## Citation

Jamshaid, H., & Mishra, R. (Eds.). (2024). *Knitting Science, Technology, Process and Materials: A Sustainable Approach*. Springer Nature Switzerland. DOI: 10.1007/978-3-031-44927-7

## Chapter overview

| Chapter | Title | Book pages |
|---|---|---|
| 1 | Introduction: Knitting Fundamentals | 1–11 |
| 2 | Yarns in Knitting | 13–43 |
| 3 | Weft Knitting Machines | 45–79 |
| 4 | Weft-Knitted Structure and Their Effect on Fabric Properties | 81–107 |
| 5 | Mechanics of Weft-Knitted Structure | 109–137 |
| 6 | Knitwear Dyeing: Theory and Sustainability | 139–155 |
| 7 | Textile Testing and Quality Control in Knitting | 157–179 |
| 8 | Technical Applications of Knitted Fabrics | 181–203 |

## Chapter 1: Knitting Fundamentals

### Weft vs. warp knitting

**Weft knitting**: yarn fed in the width (crosswise) direction; loops formed row by row. One yarn can make a whole fabric. Machines: circular or flat (V-bed). Most common for garments.

**Warp knitting**: yarn runs lengthwise in zig-zag pattern; each needle takes its own yarn. Multiple yarns fed simultaneously. Machines: flat only. Subtypes: Tricot, Raschel. More dimensionally stable, used for technical textiles.

| Property | Weft-knit | Warp-knit |
|---|---|---|
| Yarns required | One (minimum) | One per needle |
| Extensibility | Higher | Lower |
| Dimensional stability | Lower | Higher |
| Run risk | High (from single broken loop) | Low |
| Primary use | Garments, comfort wear | Technical textiles, lace |

### Knitting terminology

- **Loop (stitch)**: basic unit; formed of head (top arc), legs (vertical segments), foot (connecting sinker loop)
- **Face loop**: passes front-to-back of previous loop (V visible on front)
- **Back (reverse) loop**: passes back-to-front (arch visible on back)
- **Course**: horizontal row of loops; analogous to weft in weaving; measured as CPI (courses per inch) or C.P.cm
- **Wale**: vertical column of loops; analogous to warp; measured as WPI (wales per inch) or W.P.cm
- **Stitch density**: CPI × WPI (stitches per square inch)
- **GSM**: grams per square meter — areal weight of fabric
- **Stitch length (S.L.)**: length of yarn consumed per loop; fundamental control parameter
- **Machine gauge**: needles per inch in the needle bed
- **Machine pitch**: gaps between needles per inch

All fabric properties (extensibility, areal weight, thickness, porosity) can be engineered by adjusting stitch length and machine gauge.

## Chapter 5: Mechanics of Weft-Knitted Structure

### Two-regime stress-strain curve

The stress-strain curve of knitted fabric is nonlinear, characterized by two stages:
1. **Regime 1 (structural)**: loops straighten and align; nonlinear low-stiffness region dominated by geometric reorganization
2. **Regime 2 (material)**: yarn itself stretches; approximately linear, higher stiffness

The flexural rigidity of the stitch controls regime 1: $G_0 = B \times R = \pi d^4 E / 64$ where $d$ is yarn diameter and $E$ is yarn Young's modulus.

### Single jersey mechanics

- Course direction: loops straighten and deform directly, elongation up to ~60–80%
- Wale direction: leg length of loops increases as wale spacing decreases; similar J-shape but failure at lower elongation than course direction
- Course elongation > wale elongation under same force (for plain stockinette/jersey)
- Curls at edges from imbalanced tensile structure

### Rib fabric mechanics

- Manufactured on double-bed machines; alternating face and back loops in columns
- Can stretch up to **200%** in course direction — highest of all structures studied (this is the upper limit; Singal 2024 reports 180% extension under the same applied stress as 21% for stockinette, a different measurement basis — see [[singal-naturecomm-2024]])
- Coursewise elongation ~2× that of single jersey under same force, because both front and back loops straighten simultaneously
- Walewise elongation less than coursewise
- Anisotropy is opposite to single jersey in some loading configurations

### Interlock fabric mechanics

- Double-bed circular machine; front/back loops directly opposite (unlike rib where they alternate)
- Requires two feeds per course; alternating needles in each feed
- More stable than single jersey and rib; requires more force to deform
- Elongation in course direction less than rib, similar to or greater than jersey
- Walewise extension < coursewise extension (like jersey)

### Yarn loop model (modified Pierce model)

The modified Pierce model describes the loop geometry with:
- $P$ = course spacing
- $J$ = wale spacing
- $d$ = yarn diameter (contact circles)

Under tensile loading, loop deforms as per the relation $B_1 = B \times OB/OC$ (length ratio scaling).

### Flexural rigidity formula

$$G_0 = \frac{\pi d^4 E}{64}$$

This is equivalent to the Euler-Bernoulli bending stiffness $EI$ for a circular cross-section yarn of diameter $d$. Higher $G_0$ → stiffer bending → stiffer fabric in regime 1. See also [[cornelissen-2009]] for measurement and [[yarn]] for the $E^b$ parameter used in simulation.

### Friction effects

Yarn friction coefficient affects deformation; higher friction reduces strain under load. Rib fabrics show stronger friction effects than jersey. Shear resistance of knitted fabrics is lower than woven and non-woven equivalents.

## Broader context

Chapter 8 covers technical applications: medical devices (hernia mesh, heart valves, vascular grafts), geotextiles, ballistic protection (aramid knits), and smart/electronic textiles. These applications exploit the anisotropy, extensibility, and programmability of knitted fabrics — the same properties studied mechanically in the research papers of this wiki.

## Related pages

- [[stitch-types]]
- [[wale-and-course]]
- [[yarn]]
- [[knitted-fabrics]]
- [[knit-elasticity]]
- [[stitch-topology]]
