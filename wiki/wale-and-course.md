# Wale and Course

**Summary**: Course and wale are the two principal directions of a knitted fabric — course runs along rows (x-direction), wale runs along columns (y-direction). The stitch geometry in each direction, characterized by dimensions $c$ and $w$, determines the fabric's anisotropic mechanical response.

**Sources**: `raw/Poincloux_PRX_2018.pdf`, `raw/Singal_NatureComm_2024.pdf`, `raw/notes_for_Tim.pdf`, `raw/Knitting Science, Technology, Process and Materials.pdf`

**Last updated**: 2026-04-13

---

## Directions

- **Course direction** (x): along rows of stitches, perpendicular to the knitting direction
- **Wale direction** (y): along columns of stitches, parallel to the knitting direction

These two directions are generally not equivalent — most fabrics are **anisotropic**. The degree and character of anisotropy depends on [[stitch-types]].

## Stitch dimensions

Each stitch occupies a rectangular unit cell defined by two length scales (source: Poincloux_PRX_2018.pdf):

- $c$ = stitch size in the course direction (lateral spacing)
- $w$ = stitch size in the wale direction (longitudinal spacing)

In the reference (unloaded) state, these take values $c^*$ and $w^*$, measured experimentally from high-resolution imaging. For the model nylon stockinette in Poincloux PRX 2018: $c^* = 3.93$ mm, $w^* = 2.08$ mm.

## Catenary geometry

Under tension in the wale direction, the yarn in a stockinette stitch adopts a **catenary shape** — the form taken by a hanging chain. This is consistent with the boundary conditions imposed by the neighboring stitches and the yarn's bending elasticity. The catenary character is much less pronounced in free (laterally sliding) boundary conditions than clamped ones (source: Poincloux_PRX_2018.pdf).

## Unit cell and periodicity

In [[yarn-simulation]] frameworks, the periodicity of the fabric is encoded in two lattice vectors:

$$\mathbf{a}_1 = a_1(1, 0, 0), \quad \mathbf{a}_2 = a_2(0, 1, 0)$$

where $a_1$ (course spacing) and $a_2$ (wale spacing) are the unit cell dimensions. In Dimitriyev's stockinette simulation, initial guesses are $(a_1, a_2) = (6.0, 3.5)$ in units of yarn radius (source: notes_for_Tim.pdf).

## Fabric geometry parameter $\delta$

The parameter $\delta$ (measured to be ~0.86 for stockinette) relates the asymmetric contributions of course and wale dimensions to the conservation of yarn length per stitch (source: Poincloux_PRX_2018.pdf):

$$\langle \ell \rangle = \langle c \rangle + \delta \langle w \rangle = \text{const}$$

$\delta$ characterizes the machining process (needle spacing) and is independent of applied strain.

## Curvature structure

The yarn in a stitch has three characteristic radii of curvature (source: Poincloux_PRX_2018.pdf):
- $R_c$: in-plane curvature along the course direction
- $R_w$: in-plane curvature along the wale direction
- Out-of-plane curvatures responsible for the 3D shape (curling) of unloaded stockinette; negligible for clamped mechanical response

## Textile measurement conventions

From industrial practice (source: Jamshaid & Mishra 2024):

- **CPI**: Courses per inch — measures row density; equivalent to $1/c$ in research notation
- **WPI**: Wales per inch — measures column density; equivalent to $1/w$
- **Stitch density**: CPI × WPI (stitches per square inch)
- **GSM**: Grams per square meter — areal weight
- **Stitch length (S.L.)**: yarn length consumed per loop (equivalent to loop length $L$ in research papers)
- **Machine gauge**: needles per inch in the needle bed; determines which yarn counts can be used
- **Machine pitch**: gaps between needles per inch (= 1/gauge)

All fabric properties can be engineered by adjusting stitch length: longer stitch length → larger loops → more extensible, more porous, lower GSM; shorter stitch length → tighter fabric.

## Peirce cover factors and geometric similarity

The stitch dimensions $c$ and $w$ are equivalent to the **cover factors** introduced by F.T. Peirce (1947):

$$K_c = n_c \cdot d = \frac{d}{c}, \qquad K_w = n_w \cdot d = \frac{d}{w}$$

where $n_c = 1/c$ is the course density and $d$ is the yarn diameter. $K_c = 1$ means yarns are just touching in the course direction (maximum course cover).

**Geometric similarity principle** (Peirce 1947): two fabrics with the same cover factors $K_c$ and $K_w$ but different yarn sizes are mechanically equivalent when stress and length are normalised by $B/d^3$ and $d$ respectively. This is why the normalised rigidity $\tilde{Y} = Y \cdot LA / B$ collapses to a single curve per stitch pattern across different yarn materials (source: Singal_NatureComm_2024.pdf).

**Poisson function**: yarn-length conservation per stitch constrains the course and wale cover factors during deformation. Peirce showed that in normalised form they satisfy:

$$x^2 + y^2 = 2, \qquad y = \sqrt{2 - x^2}$$

where $x = K_c / K_{c0}$ and $y = K_w / K_{w0}$. This quarter-circle relationship predicts the transverse contraction of a knitted fabric from pure geometry, and is the geometric origin of the near-incompressibility of knitted fabrics (Poisson ratio $\nu \approx 0.46$; see [[poisson-ratio]]).

The asymmetric version for real stockinette — where the loop aspect ratio $c/w \ne 1$ breaks the circular symmetry — is the yarn-conservation equation:

$$\langle c \rangle + \delta \langle w \rangle = \ell^* = \text{const}, \qquad \delta \approx 0.86$$

which is the experimentally measured form of Peirce's Poisson function (source: Poincloux_PRX_2018.pdf; see also [[peirce-1947]]).

## Related pages

- [[knitted-fabrics]]
- [[stitch-types]]
- [[yarn]]
- [[knit-elasticity]]
- [[poisson-ratio]]
- [[yarn-simulation]]
- [[poincloux-prx-2018]]
- [[jamshaid-mishra-2024]]
- [[dimitriyev-notes-2019]]
- [[peirce-1947]]
