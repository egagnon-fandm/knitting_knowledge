# Wadekar et al. 2020 — Helicoid Geometric Model of Knitted Fabrics

**Summary**: A 2020 paper by Wadekar, Amanatides, Dion, King, Bhattacharya, and Brun that models yarn paths in knitted fabrics by constraining them to lie on a helicoid surface. The model uses energy minimization over three geometric parameters and has been validated against multiple fabric types.

**Sources**: `raw/Wadekar et al. - 2020 - Geometric modeling of knitted fabrics using helico.pdf`

**Last updated**: 2026-05-04

---

## Context

P. Wadekar, C. Amanatides, G. Dion, Y. King, K. Bhattacharya, and D. Brun, Journal of Engineered Fibers and Fabrics 15:1–15 (2020). The paper proposes that the complex 3D path of yarn in a stitch can be efficiently parameterized by a helicoid scaffold — a minimal surface naturally suited to the helical winding of yarn as it passes through an adjacent loop.

---

## The helicoid scaffold

A **helicoid** is the minimal surface swept by a line rotating about and translating along an axis simultaneously. In cylindrical form:

$$\mathbf{H}(r, \theta) = \begin{pmatrix} r\cos\theta \\ r\sin\theta \\ c\theta \end{pmatrix}$$

where $r$ is the radial distance from the axis, $\theta$ is the azimuthal angle, and $c$ is the pitch (axial rise per radian).

The yarn centreline is constrained to a curve on this surface. This approximation captures the key qualitative feature of stitch geometry: as the yarn passes through the previous loop, it wraps helically around the interlocking region.

---

## Three geometric parameters

The helicoid model has three parameters characterizing the scaffold geometry:

| Parameter | Symbol | Physical meaning |
|---|---|---|
| Yarn radius contribution | $R_y$ | effective lateral radius of the yarn segment within the stitch |
| Helicoid radius | $R_h$ | radial extent of the helicoid scaffold |
| Pitch | $c$ | axial rise per unit twist |

Together with the stitch dimensions $a$ (course direction) and $b$ (wale direction), the model has five parameters per fabric and stitch type. Parameters are fitted to experimental or simulation data using energy minimization.

---

## Energy minimization

The optimal yarn path is found by minimizing a total energy over possible curves on the helicoid:

$$E_\text{total}^i = \alpha E_\text{len}^i + \beta E_\text{dist}^i$$

where:
- $E_\text{len}^i$ = deviation of the arc length from the natural yarn length per stitch $\ell^*$; penalizes paths that are too long or too short
- $E_\text{dist}^i$ = deviation from the helicoid surface; penalizes departures from the scaffold geometry
- $\alpha$ and $\beta$ are weighting coefficients that set the relative importance of arc-length fidelity vs. surface constraint

The minimization is performed per stitch unit cell and yields the 3D curve $\mathbf{r}(t)$ for each yarn segment.

---

## Fabric types tested

The model was validated against seven weft-knit fabric types:
- Plain (stockinette)
- 1×1 Rib
- Interlock
- Purl
- Purl rib
- Purl interlock
- Cardigan variations

For each fabric type, the five parameters ($R_y, R_h, c, a, b$) were independently fitted. The model reproduces the key 3D features of the stitch geometry in all cases.

---

## Comparison with other geometric stitch models

| Feature | Demiroz & Dias 2000 | Wadekar et al. 2020 | Dimitriyev / Singal |
|---|---|---|---|
| Scaffold geometry | Piecewise cubic spline | Helicoid surface | Bézier curve (free) |
| Parameters | 1 (upper-right distance $b$) | 5 per fabric type | 11 per cross-over + 2 per connection |
| Solution method | Newton-Raphson (arc length) | Energy minimization | Energy minimization (full mechanics) |
| Fabric types | Plain only | 7 weft-knit types | Stockinette, garter, rib, seed |
| Mechanics | None | None | Bending + contact energy |

The helicoid scaffold is a stronger geometric prior than the free spline of Demiroz & Dias and handles the 3D twist of yarn crossing more naturally. It is less general than the Bézier/energy-minimization approach of [[yarn-simulation]], which adds mechanics; the helicoid model is purely geometric.

---

## Significance for stitch geometry research

The helicoid model makes a specific geometric claim: yarn in a stitch traces a path on a minimal surface. This is physically plausible because:
1. Minimal surfaces arise naturally from surface-tension or elastic-energy minimization in thin structures.
2. The helicoid is the simplest surface consistent with the helical symmetry of a yarn wrapping through a loop.
3. The model predicts the **twist** of the yarn cross-section — a feature that flat planar models (e.g. Demiroz & Dias) cannot capture.

The three-parameter form also provides a compact design space for inverse design: given a target loop shape (from microscopy or simulation), one can fit $R_y, R_h, c$ and then manufacture a fabric with those properties.

---

## Related pages

- [[yarn-simulation]]
- [[yarn]]
- [[demiroz-2000]]
- [[stitch-types]]
- [[knitted-fabrics]]
- [[wale-and-course]]
