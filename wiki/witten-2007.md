# Witten 2007 — Stress Focusing in Elastic Sheets

**Summary**: Review paper (Rev. Mod. Phys. 79, 643, 2007) by T. A. Witten. Covers the physics of crumpling in thin elastic sheets: Föppl–von Kármán equations, d-cones (singular vertices), stretching ridges between vertices, ridge width scaling, and the dominance of ridge–vertex interactions in crumpled sheet mechanics. Background context for understanding elastic sheet behaviour in confined geometries.

**Sources**: `raw/RevModPhys.79.643.pdf`

**Last updated**: 2026-04-17

---

## Main subject

When a thin elastic sheet is confined (e.g., inside a sphere), it develops sharply localised deformations rather than distributing strain uniformly. Two elementary singularities appear:

1. **d-cone (developable cone)**: a single vertex where elastic energy concentrates. The sheet bends strongly around the vertex tip; the core region size is set by the sheet thickness t. Bending energy ∝ t² ln(R/t) where R is the sheet size.

2. **Stretching ridge**: a line connecting two d-cone vertices. Width scales as w ∝ t^(1/3) L^(2/3). The elastic energy stored in ridges typically exceeds that in cones.

At large deformations, ridges and vertices dominate all other contributions to the stored elastic energy and control the mechanics of crumpled sheets.

---

## Theoretical framework

The governing equations are the **Föppl–von Kármán equations**, which couple:
- A potential for the **curvature tensor** (related to bending energy)
- A potential for the **stress tensor** (related to stretching/in-plane energy)

They are fourth-order in the fields and nonlinear, controlling the shapes of strongly deformed membranes. Key properties of the equations:
- Derived by Föppl (1907) and von Kármán (1956) for nearly inextensible thin sheets
- Admit singular solutions (d-cones, ridges) that become sharper as thickness → 0
- Extended into the postbuckling regime by Koiter, Hutchinson, Thompson in the 1980s–90s

---

## Relevance to knitted fabrics

Knitted fabric is not a classical elastic sheet, but the sheet analogy is relevant in several ways:

- At large scales, knitted fabric panels are modelled as 2D elastic sheets with anisotropic constitutive relations (used in [[constitutive-model]] and FEA applications in Singal 2024)
- Under complex loading (twisting, bending, draping), fabric panels may form ridge-like and cone-like deformations analogous to crumpled sheets
- The Föppl–von Kármán framework is the theoretical backdrop for the continuum mechanics used in thin-shell analyses of textile materials

The connection is indirect — knitted fabric's extensibility and topological structure make it quite different from a classical thin elastic sheet — but Witten 2007 is useful background for understanding stress focusing in any 2D elastic medium.

---

## Related pages

- [[deformation]]
- [[constitutive-model]]
- [[knitted-fabrics]]
- [[likharev-chap7]]
