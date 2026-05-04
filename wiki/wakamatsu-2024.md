# Wakamatsu et al. 2024 — Discrete Quaternion Model of Two-Ply Knitted Stitches

**Summary**: Chapter 1 of the Midha et al. 2024 proceedings volume, by H. Wakamatsu, S. Hirai, M. Nagumo, and J. Noda. Presents a discrete rod model using quaternion frame representations to predict the 3D equilibrium shape of two-ply yarn knitted stitches by potential energy minimization.

**Sources**: `raw/Midha et al. - 2024 - Proceedings of the 50th Textile Research Symposium.pdf` (Chapter 1 only; remaining chapters not ingested)

**Last updated**: 2026-05-04

---

## Context

H. Wakamatsu, S. Hirai, M. Nagumo, and J. Noda, "Modelling and Analysis of Knitted Stitch Shape", Chapter 1 in: V. Midha et al. (eds.), *Proceedings of the 50th Textile Research Symposium*, 2024. This chapter addresses a gap in stitch geometry models: most existing models (Demiroz & Dias, helicoid scaffold) focus on single-ply yarn, but real knitting yarns are typically two-ply or multi-ply — twisted composites where torsional rigidity contributes significantly to stitch shape.

---

## Discrete quaternion rod model

### Discretization

The yarn centreline is discretized into a chain of $N$ rigid segments. Each segment $i$ is characterized by:
- Its position vector $\mathbf{r}_i$ (location of its midpoint or endpoint)
- Its orientation represented as a **unit quaternion** $\mathbf{q}_i \in \mathbb{H}$ with $|\mathbf{q}_i| = 1$

The unit quaternion $\mathbf{q}_i = (q_0, q_1, q_2, q_3)$ encodes the full 3D rotation of the material frame attached to segment $i$ relative to a global frame. This avoids gimbal lock and provides a compact, continuous representation of orientation.

### Material frame

Each segment carries a material frame $(\hat{d}_1^i, \hat{d}_2^i, \hat{d}_3^i)$ derived from its quaternion, where $\hat{d}_3^i$ is the segment tangent and $(\hat{d}_1^i, \hat{d}_2^i)$ are cross-section directors. This is the discrete analogue of the Kirchhoff/Cosserat rod frame (see [[kirchhoff-rod]] and [[cosserat-rod]]).

---

## Potential energy and rigidities

The total potential energy of the yarn chain has three contributions:

$$E_\text{total} = E_A + E_I + E_{GJ}$$

### Elongational energy $E_A$

$$E_A = \frac{1}{2} E A \sum_i \left(\frac{|\mathbf{r}_{i+1} - \mathbf{r}_i|}{l_0} - 1\right)^2 l_0$$

where $EA$ is the axial rigidity (extensional stiffness) and $l_0$ is the natural segment length. This term is often small for nearly-inextensible yarn.

### Flexural energy $E_I$

$$E_I = \frac{1}{2} E I \sum_i |\Delta \hat{d}_3^i|^2 \cdot l_0^{-1}$$

where $EI$ is the flexural rigidity (bending stiffness) and $\Delta \hat{d}_3^i = \hat{d}_3^{i+1} - \hat{d}_3^i$ captures the change in tangent direction between adjacent segments (discrete curvature).

### Torsional energy $E_{GJ}$

$$E_{GJ} = \frac{1}{2} G J \sum_i \omega_i^2 \cdot l_0$$

where $GJ$ is the torsional rigidity and $\omega_i$ is the discrete twist (rotation of the material frame about the tangent axis). This term is particularly important for **two-ply yarn**, which has a strong tendency to untwist — the restoring torque from untwisting resists loop closure and modifies loop shape.

---

## Two-ply yarn model

The key novelty is modelling a **two-ply yarn** — two single-ply yarns twisted around each other. In a two-ply yarn:
- Each ply has its own bending rigidity $EI_\text{single}$.
- The two plies are bonded together by inter-ply friction, creating an effective composite rigidity.
- The ply angle (helix angle of the twist) determines the composite torsional rigidity $GJ_\text{composite}$.

For real two-ply yarns, the composite $GJ$ is substantially higher than for a single-ply yarn of equal diameter. This higher torsional stiffness affects loop closure: the yarn resists the twisting required to form a tight loop, producing larger, more open stitches compared to a single-ply model.

---

## Equilibrium computation

The equilibrium stitch shape is found by **potential energy minimization**:

$$\mathbf{q}^*, \mathbf{r}^* = \operatorname*{argmin}_{\mathbf{q}, \mathbf{r}} E_\text{total}(\mathbf{q}, \mathbf{r})$$

subject to:
- Boundary conditions at the stitch connections (where the current row interlocks with the row below).
- Yarn length constraint (total arc length = $\ell^*$).
- Interpenetration prevention (yarn centreline separation $\geq 2R$ at crossings).

The minimization is carried out numerically (gradient-based or quasi-Newton). The quaternion parameterization keeps the orientation constraint ($|\mathbf{q}_i| = 1$) on a smooth manifold, avoiding singularities in the gradient computation.

---

## Validation

The predicted 3D stitch shapes were compared against **micro-CT or 3D microscopy** measurements of physical knitted samples. The model correctly captures:
- The in-plane loop geometry (loop head radius, shank width).
- The out-of-plane excursions at stitch crossings.
- The systematic differences between single-ply and two-ply yarn stitches.

In particular, the higher torsional rigidity of two-ply yarn leads to larger, more rounded loop heads — a feature that single-ply or purely geometric models (Demiroz & Dias, helicoid) cannot predict without an explicit torsional term.

---

## Relationship to other rod models

| Model | Rod type | Frame | Twist | Application |
|---|---|---|---|---|
| Demiroz & Dias 2000 | Geometric spline | None | Not modelled | Single-ply stitch shape |
| Wadekar 2020 | Helicoid curve | None | Implicit in scaffold | Multi-fabric types |
| Dimitriyev 2019 | Bézier + Kirchhoff | Frenet (no material twist) | Equal $B = J$ | Mechanics/simulation |
| Wakamatsu 2024 | Discrete quaternion | Material frame | Explicit $GJ$ | Two-ply stitch shape |

Wakamatsu's model is closest in spirit to the [[kirchhoff-rod]] formulation but uses a discrete quaternion representation rather than a continuous director field, and explicitly treats the two-ply composite structure. It is the most complete geometric-mechanical model for predicting stitch shape from yarn properties.

---

## Note on source

Only Chapter 1 of the Midha et al. 2024 proceedings has been ingested. The remaining chapters cover a range of textile research topics unrelated to knit mechanics and have not been read or summarized.

---

## Related pages

- [[yarn-simulation]]
- [[yarn]]
- [[kirchhoff-rod]]
- [[cosserat-rod]]
- [[demiroz-2000]]
- [[wadekar-2020]]
- [[stitch-types]]
- [[knitted-fabrics]]
