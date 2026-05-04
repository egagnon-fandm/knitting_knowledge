# Peirce 1947 — Geometrical Principles Applicable to the Design of Functional Fabrics

**Summary**: Foundational 1947 paper by F.T. Peirce that introduces cover factor analysis, geometric similarity, and the Poisson function for weft-knitted fabrics. Derives dimensionless relationships between fabric structure and mechanical behaviour from pure geometry, without reference to material properties.

**Sources**: `raw/Peirce - 1947 - Geometrical Principles Applicable to the Design of Functional Fabrics.pdf`

**Last updated**: 2026-05-04

---

## Context

F.T. Peirce, Textile Research Journal XVII(3):123–147 (1947). A broad theoretical treatment of fabric geometry covering woven and knitted structures. For knits, it establishes the concept of the cover factor and derives the Poisson function relating course and wale dimensions during deformation. The approach is purely geometric — material properties enter only through the yarn diameter and the inextensibility assumption.

---

## Cover factor

The **cover factor** $K$ quantifies what fraction of the fabric area is occupied by yarn:

$$K = n \cdot d$$

where $n$ = thread density (threads per unit length) and $d$ = yarn diameter. $K = 1$ corresponds to yarns just touching (maximum cover); $K < 1$ means open fabric with gaps between yarns.

For weft-knitted fabrics, two cover factors are defined:

- **Course cover factor**: $K_c = n_c \cdot d$ where $n_c$ is courses per unit length
- **Wale cover factor**: $K_w = n_w \cdot d$ where $n_w$ is wales per unit length

These two numbers are the primary structural parameters that determine the fabric's mechanical state. Their product $K_c \cdot K_w$ is the **stitch density** in dimensionless form.

---

## Geometric similarity

Two knitted fabrics made from different yarns are **geometrically similar** if they have the same cover factors $K_c$ and $K_w$. A key result of Peirce's analysis is that all dimensionless mechanical properties — normalized stiffness, Poisson ratio, strain at maximum extensibility — are the same for geometrically similar fabrics, regardless of yarn size or material.

This is the geometric similarity principle: when mechanical quantities are expressed in appropriate reduced units (stress in $B/d^3$, length in $d$, etc.), the curves collapse to a single master curve for each stitch pattern. This principle was later confirmed numerically and experimentally by [[singal-naturecomm-2024]], where the normalised rigidity $\tilde{Y} = Y \cdot LA / B$ was shown to depend only on stitch topology across eight yarn materials.

---

## The Poisson function

When a knitted fabric is stretched in the course direction, the course cover factor $K_c$ decreases (loops spread apart in x) while the wale cover factor $K_w$ increases (loops compress in y) — this is the Poisson coupling. Peirce derives the geometric constraint relating these changes from **yarn-length conservation per stitch**.

In normalized form, letting $x = K_c / K_{c0}$ and $y = K_w / K_{w0}$ be the cover factors scaled by their reference values, the constraint takes the form:

$$x^2 + y^2 = 2$$

This is a quarter-circle in the $(x, y)$ plane, equivalently:

$$y = \sqrt{2 - x^2}$$

This is Peirce's **Poisson function**: it predicts the transverse contraction of a knitted fabric from purely geometrical reasoning. The relationship implies that a knitted fabric behaves nearly as an incompressible 2D material, with an effective Poisson ratio that depends on the current cover factors. The actual Poisson ratio observed experimentally for stockinette ($\nu \approx 0.46$, [[poincloux-prx-2018]]) is consistent with this geometric prediction.

---

## Lattice theory of fabric strain

Peirce models the deformed fabric as a **lattice** of yarn elements. Each yarn segment occupies a lattice site; extension is geometrically equivalent to a change in the lattice spacing parameters $c$ and $w$. In the small-strain limit, this gives linear relationships between applied force and lattice strain.

Key results from lattice theory:
- At low strains, the fabric behaves as an orthotropic elastic sheet.
- The anisotropy ratio $Y_x / Y_y$ depends on the ratio of course to wale cover factors.
- The lattice model breaks down at large strains when loops begin to jam (see [[yarn-contact]] for the contact-dominated high-strain regime).

---

## Crimp theory (woven fabrics)

For woven fabrics (less central to the knitting research but covered in the paper):
- **Crimp** = yarn undulation due to interlacing; measured by the fractional shortening of the straight-to-woven yarn length.
- Crimp interchange: when the fabric is stretched in one direction, the crimp in that direction decreases and the crimp in the perpendicular direction increases.
- This is the woven-fabric analogue of the knit Poisson function.

---

## Implications for the knitting research programme

Peirce's cover-factor framework provides the geometric underpinning for several results in [[singal-naturecomm-2024]] and [[poincloux-prx-2018]]:

1. The fabric geometry parameter $\delta \approx 0.86$ in the yarn-length conservation $\langle c \rangle + \delta \langle w \rangle = \ell^*$ is the asymmetric version of Peirce's cover-factor constraint (with the aspect ratio $c/w \ne 1$ of real stockinette breaking the circular symmetry).
2. The normalised rigidity collapse onto fabric-type master curves is the experimental confirmation of geometric similarity.
3. The Poisson ratio $\nu \approx 0.46$ of stockinette has its origin in the quarter-circle Poisson function.

---

## Related pages

- [[wale-and-course]]
- [[knitted-fabrics]]
- [[stitch-topology]]
- [[knit-elasticity]]
- [[poisson-ratio]]
- [[poincloux-prx-2018]]
- [[singal-naturecomm-2024]]
- [[yarn]]
