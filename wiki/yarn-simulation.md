# Yarn Simulation

**Summary**: Yarn paths in knitted fabrics can be simulated using two complementary frameworks: (1) a static Bézier/energy-minimization approach (Dimitriyev 2019, Singal 2024) focused on unit-cell equilibria; and (2) a dynamic B-spline/Lagrangian approach (Ding et al. 2023) applied to full fabric assemblies. Both use Euler-Bernoulli bending energy and contact repulsion; they differ in extensibility assumption, dynamics, and scale.

**Sources**: `raw/notes_for_Tim.pdf`, `raw/Singal_NatureComm_2024.pdf`, `raw/Unravelling the Mechanics of Knitted Fabrics Through.pdf`, `raw/Kaldor et al. - Simulating Knitted Cloth at the Yarn Level.pdf`, `raw/Coleman et al. - 1993 - On the dynamics of rods in the theory of Kirchhoff.pdf`

**Last updated**: 2026-04-17

---

## Geometric framework

### Yarn path representation

Each row of yarn is a continuous curve $\Gamma_n(s)$, decomposed into segments:

$$\Gamma_n(s) = \gamma_{n,i}(s) \quad \text{for } s \in [s_i, s_{i+1})$$

Segments satisfy **first-order geometric continuity** (G1): matching positions and unit tangent vectors at junctions (source: notes_for_Tim.pdf).

Segments alternate between two types:
1. **Cross-overs (clasps)**: where two yarn strands twist around each other
2. **Connections**: curves joining free ends of cross-over segments

### Cross-overs

A cross-over between strands $\Gamma_n$ and $\Gamma_{n+1}$ is characterized by:
- Position $\mathbf{r}$ (3 DOF)
- Orientation $\{\hat{\eta}_1, \hat{\eta}_2, \hat{\eta}_3\}$ as Euler angles $\{\theta_1, \theta_2, \theta_3\}$ (3 DOF)
- Scale $\zeta > 0$ (1 DOF)
- Aspect angle $\phi$ (1 DOF)
- Terminal tangent direction $(\psi_1, \psi_2)$ in spherical coords (2 DOF)
- Midpoint offset $\mu$ (1 DOF)
- Parity $p \in \{0, 1\}$: handedness/chirality (static, not a DOF)

**Total: 11 DOF per cross-over** (source: notes_for_Tim.pdf).

The endpoint positions of yarn segments at a cross-over are prescribed by:

$$\gamma_{n,i}(s_0) = \mathbf{r} - \zeta(\hat{\eta}_3 \cos\phi + (-1)^p \hat{\eta}_2 \sin\phi)$$

and three analogous equations.

### Connections

Each connection segment has **2 additional DOF** ($\alpha_0, \alpha_1$) specifying the tangent magnitudes at its two endpoints.

### Bézier curve representation

Each segment $\gamma$ is expressed as a **cubic Bézier curve** (N=3) with 4 control points $\mathbf{k}_0, \ldots, \mathbf{k}_3$:

$$\gamma(t) = \sum_{n=0}^{3} \mathbf{k}_n \beta_n^3(t), \quad \beta_n^N(t) = \binom{N}{n}(1-t)^{N-n}t^n$$

Control points encode:
- $\mathbf{k}_0, \mathbf{k}_3$: endpoints (positions)
- $\mathbf{k}_1 = \mathbf{k}_0 + \frac{\alpha_0}{3}\hat{t}(0)$, $\mathbf{k}_2 = \mathbf{k}_3 - \frac{\alpha_1}{3}\hat{t}(1)$: tangent magnitudes

This gives analytic expressions for the curve length, curvature, and torsion.

## Energy model

### Bending and torsion energy (Euler-Bernoulli elastica)

$$E_\text{curve} = \frac{1}{2} \sum_\text{segments} \int_0^1 dt\, |\partial_t \gamma| \left[B\kappa^2(t) + J\tau^2(t)\right]$$

where $B$ = bending rigidity, $J$ = torsional rigidity (set equal to $B$ for simplicity), $\kappa$ = curvature, $\tau$ = torsion. All are computed analytically from Bézier derivatives (source: notes_for_Tim.pdf). The choice $B = J$ is justified by the Kirchhoff rod result $\mu J / EI = (1+\nu)^{-1} \approx 0.77$ for yarn-like materials (source: Coleman et al. 1993; see also [[kirchhoff-rod]] and [[landau-chap2]] §17).

### Contact (Hertz) energy

Yarn-yarn contacts at cross-overs are modeled by distributing $N_\text{sph} \approx 10$ spheres along each segment and penalizing overlap:

$$V_\text{int} = \frac{M}{5} \sum_{i,j} \Delta_{ij}^{5/2} \quad (\Delta_{ij} < 0)$$

where $\Delta_{ij} = |\gamma_m(i/N_\text{sph}) - \gamma_n(j/N_\text{sph})| - 2R$ and $M$ is the Hertz modulus (source: notes_for_Tim.pdf).

### Total energy with applied tension

$$E_\text{tot} = E_\text{curve} + V_\text{int} - f_1 a_1 - f_2 a_2$$

where $(f_1, f_2)$ are applied forces and $(a_1, a_2)$ are the unit cell dimensions. Minimizing with fixed total yarn length $L$ gives the equilibrium configuration under a specified applied tension.

## Stockinette unit cell

The stockinette unit cell contains 2 cross-overs (parities 0 and 1) and 4 connecting curves ($\gamma_{12}$, $\gamma_{21}$, $\gamma_{11}$, $\gamma_{22}$). Periodic boundary conditions are enforced by requiring terminal endpoints to satisfy lattice-translated joining conditions (source: notes_for_Tim.pdf).

Initial unit cell size: $(a_1, a_2) = (6.0, 3.5)$, total yarn length $L_0 \approx 14.177$ (in units of yarn radius).

## Simulation parameters (Dimitriyev 2019)

| Parameter | Symbol | Value |
|---|---|---|
| Bending modulus | $B$ | 1.0 |
| Twisting modulus | $J$ | 1.0 |
| Hertz modulus | $M$ | 8.0 |
| Spheres per segment | $N_\text{sph}$ | 10 |
| Cross-sectional radius | $R$ | 0.5 |

## Implementation

Minimization uses `scipy.optimize.minimize` with constrained optimization (fixed total yarn length). The framework also simulates garter, rib, and seed unit cells (source: notes_for_Tim.pdf).

In Singal 2024, the Bézier representation was upgraded to **degree-5 Bézier spline curves** for continuous curvature, with a hard-core soft-shell contact model informed by experiments (source: Singal_NatureComm_2024.pdf).

## Kaldor et al. 2008 (SIGGRAPH predecessor)

The first practical yarn-level simulation of knitted cloth was published by Kaldor, James, and Marschner (Cornell) at SIGGRAPH 2008. This work predates the physics-focused literature and introduced several ideas later adopted by the mechanics community:

- Yarn as **inextensible B-spline tube** with quadratic bending energy
- Stiff **penalty contact energy** f(d) ∝ 1/d² + d² − 2 (diverges at contact)
- **Non-rigid velocity filter** for damping relative yarn motion (friction proxy)
- **DAE integration** with constraint projection (ICD method)
- Initial configuration by B-spline fitting to template stitch curves

Key result: garter, stockinette, and rib patterns emerge from yarn topology without per-pattern parameter tuning. The elastic sheet model fails for garter and rib.

Limitation: no explicit Coulomb friction — contact damping is an approximation; acknowledged as causing over-curling of stockinette edges. See [[kaldor-2008]] for full details.

## Comparison of simulation frameworks

| Feature | Kaldor 2008 | Bézier / energy-min. | B-spline / Lagrangian |
|---|---|---|---|
| Source | Kaldor, James, Marschner | Dimitriyev 2019, Singal 2024 | Ding et al. 2023 |
| Curve type | Cubic B-spline | Cubic Bézier (degree-5) | Cubic B-spline |
| Dynamics | Full (DAE/ICD) | Static minimisation | Full Lagrangian ODE |
| Extensibility | Inextensible | Inextensible | Extensible |
| Contact | Stiff penalty (diverging) | Hertz (Δ^{5/2}) | Quadratic spring |
| Friction | Velocity filter (approx.) | None | Explicit k_{dt} |
| Scale | Full garment | Unit cell | Full fabric |
| Primary goal | Computer graphics | Physics/mechanics | Mechanics |

The B-spline framework (Ding) uses explicit RK4 with a precomputed banded mass matrix; the Bézier framework (Dimitriyev/Singal) uses scipy constrained optimization. Both reproduce J-shape stress-strain curves of the four canonical fabrics.

See [[ding-2023]], [[dimitriyev-notes-2019]], and [[kaldor-2008]] for full details of each framework.

## Related pages

- [[knitted-fabrics]]
- [[stitch-types]]
- [[yarn]]
- [[wale-and-course]]
- [[stitch-topology]]
- [[knit-elasticity]]
- [[dimitriyev-notes-2019]]
- [[singal-naturecomm-2024]]
- [[ding-2023]]
- [[kaldor-2008]]
- [[yarn-contact]]
- [[kirchhoff-rod]]
- [[coleman-1993]]
