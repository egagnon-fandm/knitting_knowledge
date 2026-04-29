# Dimitriyev — Fabric Simulation Notes (2019)

**Summary**: Internal technical notes describing a geometric framework for yarn-path simulation of knitted fabrics using Bézier curves, with a bending+contact energy model and energy minimization via scipy, applied to stockinette unit cells.

**Sources**: `raw/notes_for_Tim.pdf`

**Last updated**: 2026-04-13

---

## Reference

Dimitriyev, M. S. (2019). Fabric simulation notes. Dated March 19, 2019.

## Purpose

These notes lay out the geometric and computational framework for simulating the equilibrium shape of different knitting patterns. They appear to be working notes written for a collaborator (Tim), introducing the Bézier curve approach that later underpins the simulations in [[singal-naturecomm-2024]].

## Geometric framework

See [[yarn-simulation]] for the full technical description. Summary:

- Yarn path: collection of curves $\{\Gamma_n\}$, one per row, each decomposed into cross-overs (clasps) and connections
- G1 (geometric) continuity at segment joints
- Cubic Bézier curves (4 control points) for each segment
- Cross-overs: 11 DOF (position, orientation, scale, aspect, tangent direction, midpoint offset, parity)
- Connections: 2 DOF (tangent magnitudes at endpoints)

## Energy model

$$E_\text{tot} = E_\text{curve} + V_\text{int} - f_1 a_1 - f_2 a_2$$

- $E_\text{curve}$: Euler-Bernoulli bending + torsion energy, integrated along each Bézier segment
- $V_\text{int}$: Hertzian sphere-sphere contact repulsion at cross-overs
- $f_1 a_1 + f_2 a_2$: work done by applied tension in course and wale directions

Yarn is inextensible (total length $L$ fixed as a constraint).

## Stockinette unit cell details

Two cross-overs (parities 0 and 1), 4 connecting curves. Initial parameters provided for both cross-overs. Initial unit cell $(a_1, a_2) = (6.0, 3.5)$, total yarn length $L_0 \approx 14.177$.

Periodic boundary conditions: terminal curve endpoints satisfy lattice-translated joining conditions (e.g. $\gamma_{11}(1) = \gamma_1(0) + \mathbf{a}_2$).

Test case: $f_1 = 0.5$, $f_2 = 0$, $L = 14.0$.

## Implementation

Uses `scipy.optimize.minimize` for constrained minimization. The notes describe simulations of stockinette, garter, rib, and seed fabrics.

## Relationship to Singal 2024

This framework is the direct precursor to the stitch-level simulations in [[singal-naturecomm-2024]], which extended it to:
- Degree-5 Bézier splines (for continuous curvature)
- A contact model calibrated against yarn compression experiments
- All four fabric types
- Comparison with uniaxial stress-strain experiments

## Related pages

- [[yarn-simulation]]
- [[singal-naturecomm-2024]]
- [[yarn]]
- [[stitch-types]]
- [[knit-elasticity]]
