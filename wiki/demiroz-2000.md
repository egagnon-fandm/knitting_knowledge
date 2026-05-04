# Demiroz & Dias 2000 — Cubic Spline Stitch Model

**Summary**: A 2000 paper by Demiroz and Dias that constructs a 3D geometrical model of plain-knitted stitch centrelines using piecewise cubic splines with five named control points. The model solves for stitch geometry via Newton-Raphson iteration on a yarn-length constraint and evaluates stitch length by Gaussian quadrature.

**Sources**: `raw/Demiroz and Dias - 2000 - A Study of the Graphical Representation of Plain-knitted Structures Part I Stitch Model for the Gra.pdf`

**Last updated**: 2026-05-04

---

## Context

I. Demiroz and D. Dias, Journal of the Textile Institute 91(4):463–480 (2000). Part I of a two-part series on the graphical representation of plain-knitted structures. The paper develops a piecewise cubic spline model for the yarn centreline that is geometrically consistent with yarn cross-section and stitch topology. This was an early systematic attempt to produce a smooth, physically plausible 3D stitch model for use in computer graphics and engineering analysis of knitted fabrics.

---

## Five-control-point stitch model

Each stitch is described by a yarn centreline built from **five named control points** and four cubic spline segments connecting them. The five points are:

| Label | Description | Position |
|---|---|---|
| T | Top (head) | apex of the stitch loop |
| S | Shoulder | lateral transition below the head |
| A | Arch | the midpoint where the yarn crosses |
| C | Crossover | the interlocking crossing region |
| E | End | bottom of the stitch, connecting to the row below |

The four spline segments are TS, SA, AC, and CE. Each segment is a **cubic polynomial** in a parametric variable, so the curve is piecewise cubic with continuity enforced at each control point.

The segment endpoints impose:
- **Positional continuity** (C0): the endpoint of segment $k$ equals the start of segment $k+1$.
- **Tangent continuity** (C1): first derivatives match at junctions, giving a smooth curve with no corners.

---

## Key geometric parameter: the upper-right distance $b$

The critical unknown in the model is the **upper-right distance** $b$ — the horizontal half-spacing between control points T and E (from the stitch axis to the outer lateral extent). The physical constraint is that the **total arc length of the spline must equal the known yarn length per stitch** $\ell^*$.

This constraint is nonlinear: $b$ appears in the control point coordinates, which determine the spline, whose arc length is a nonlinear functional of $b$. Demiroz and Dias solve for $b$ using **Newton-Raphson iteration**:

$$b_{k+1} = b_k - \frac{f(b_k)}{f'(b_k)}, \qquad f(b) = L_\text{spline}(b) - \ell^*$$

where $L_\text{spline}(b)$ is the spline arc length as a function of $b$.

---

## Arc length computation by Gaussian quadrature

The arc length of each cubic spline segment cannot be evaluated analytically (it involves $\sqrt{1 + (dy/dx)^2 + (dz/dx)^2}$, an elliptic integral for cubic curves). Demiroz and Dias evaluate it by **Gaussian quadrature** — a weighted sum of integrand values at predetermined abscissae:

$$L_\text{segment} = \int_0^1 \left|\frac{d\mathbf{r}}{dt}\right| dt \approx \sum_{i=1}^n w_i \left|\frac{d\mathbf{r}}{dt}\Big|_{t_i}\right|$$

For each Newton-Raphson iteration, the arc length is re-evaluated to update $f(b)$. The spline derivative $d\mathbf{r}/dt$ is a quadratic polynomial, so each evaluation is cheap.

---

## 3D geometry of the result

The model produces a smooth closed loop in 3D space. Key geometric features captured:
- The **loop head** at the top (control point T) bends sharply in the plane of the fabric.
- The **shanks** (SA and CE segments) run approximately parallel, connecting the head to the interlocking region.
- The **crossing region** (near A and C) passes through the loop from the previous row, producing the out-of-plane excursion characteristic of plain stockinette.
- The **yarn diameter** is incorporated through the boundary conditions at each crossing: centreline separation equals $2R$ at contact points.

The resulting 3D curves are visually consistent with photographs of real knitted fabric and with the unit-cell geometries produced by energy-minimization simulations (see [[yarn-simulation]]).

---

## Comparison with energy-minimization models

| Feature | Demiroz & Dias 2000 | Dimitriyev 2019 / Singal 2024 |
|---|---|---|
| Curve type | Piecewise cubic spline (5 CP) | Cubic Bézier (or degree-5) |
| Solution method | Newton-Raphson on arc-length constraint | scipy constrained energy minimization |
| Constraint | Total yarn length = $\ell^*$ | Total yarn length fixed; force balance |
| Output | Geometric shape | Equilibrium configuration at given tension |
| Mechanics | None (geometric only) | Full bending + contact energy |

Demiroz & Dias is a purely geometrical model — it constructs a plausible stitch shape but does not minimize any physical energy. The Dimitriyev/Singal framework adds mechanics (bending rigidity, Hertz contact) on top of a similar curve representation. The control point structure (T, S, A, C, E) corresponds roughly to the cross-over and connection segment endpoints of [[yarn-simulation]], though the parameterizations differ.

---

## Related pages

- [[yarn-simulation]]
- [[yarn]]
- [[wale-and-course]]
- [[stitch-types]]
- [[knitted-fabrics]]
- [[dimitriyev-notes-2019]]
- [[kaldor-2008]]
