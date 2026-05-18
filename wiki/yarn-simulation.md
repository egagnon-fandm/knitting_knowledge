# Yarn Simulation

**Summary**: Yarn paths in knitted fabrics can be simulated using two complementary frameworks: (1) a static Bézier/energy-minimization approach (Dimitriyev 2019, Singal 2024) focused on unit-cell equilibria; and (2) a dynamic B-spline/Lagrangian approach (Ding et al. 2023) applied to full fabric assemblies. Both use Euler-Bernoulli bending energy and contact repulsion; they differ in extensibility assumption, dynamics, and scale.

**Sources**: `raw/notes_for_Tim.pdf`, `raw/Singal_NatureComm_2024.pdf`, `raw/Unravelling the Mechanics of Knitted Fabrics Through.pdf`, `raw/Kaldor et al. - Simulating Knitted Cloth at the Yarn Level.pdf`, `raw/Coleman et al. - 1993 - On the dynamics of rods in the theory of Kirchhoff.pdf`, `raw/Demiroz and Dias - 2000 - ...pdf`, `raw/Wadekar et al. - 2020 - Geometric modeling of knitted fabrics using helico.pdf`, `raw/Yuksel - Stitch Meshes for Modeling Knitted Clothing with Yarn-level Detail.pdf`, `raw/Midha et al. - 2024 - Proceedings of the 50th Textile Research Symposium.pdf` (Ch. 1)

**Last updated**: 2026-05-04

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

## Geometric stitch models (non-energy-minimizing)

Three purely geometrical approaches construct stitch curves without minimizing a physical energy. They are useful for graphics rendering, pattern generation, and as initial configurations for mechanics simulations.

### Demiroz & Dias 2000 — cubic spline with five control points

Demiroz and Dias (J. Textile Institute 91(4):463–480, 2000) model the yarn centreline as a piecewise cubic spline with five named control points: **T** (top/head), **S** (shoulder), **A** (arch), **C** (crossover), **E** (end). The four segments TS, SA, AC, CE meet with C0/C1 continuity.

The critical unknown is the upper-right distance $b$ (horizontal extent from loop axis to lateral extreme), solved by Newton-Raphson iteration until the total arc length of the spline equals the prescribed yarn length per stitch $\ell^*$. Arc length is evaluated by Gaussian quadrature. See [[demiroz-2000]] for full details.

### Wadekar et al. 2020 — helicoid scaffold

Wadekar et al. (J. Engineered Fibers and Fabrics 15:1–15, 2020) constrain the yarn path to lie on a helicoid surface:

$$\mathbf{H}(r, \theta) = (r\cos\theta,\; r\sin\theta,\; c\theta)$$

parameterised by three geometric constants: $R_y$ (yarn radius contribution), $R_h$ (helicoid radius), and $c$ (pitch). The optimal curve on the helicoid is found by minimising:

$$E_\text{total}^i = \alpha E_\text{len}^i + \beta E_\text{dist}^i$$

where $E_\text{len}^i$ penalises deviation from natural stitch length and $E_\text{dist}^i$ penalises departure from the scaffold surface. The model was validated for seven weft-knit types (plain, rib, interlock, purl, and variants). The helicoid naturally captures yarn twist at crossings — a feature flat planar models miss. See [[wadekar-2020]] for full details.

### Yuksel et al. 2012 — stitch mesh + two-phase pipeline

Yuksel et al. (ACM TOG 31(3), SIGGRAPH 2012) introduce the **stitch mesh**: a polygon mesh where each face encodes one stitch and face connectivity encodes the knit topology. Stitch actions are specified as sequences of three symbols: **k** (knit), **p** (purl), **y** (yarn-over). The pipeline has two phases:

1. **Mesh relaxation**: the stitch mesh is simulated as a mass-spring system to find the rest shape of the garment.
2. **Yarn path extraction**: cubic B-splines are fitted to the relaxed mesh skeleton, incorporating stitch action type and yarn length per loop.

The stitch mesh is the design-intent representation; it can specify lace, cables, increases/decreases, and complex garment shaping that explicit template fitting (Kaldor 2008) cannot. See [[yuksel-2012]] for full details.

### Wakamatsu et al. 2024 — discrete quaternion model for two-ply yarn

Wakamatsu et al. (Midha proceedings Ch. 1, 2024) model yarn as a discrete chain of segments with orientations represented as unit quaternions. The potential energy has three terms — elongational $E_A$ (axial rigidity), flexural $E_I$ (bending rigidity), and torsional $E_{GJ}$ (twisting rigidity):

$$E_\text{total} = E_A + E_I + E_{GJ}$$

The model explicitly handles **two-ply yarn**: the composite torsional rigidity $GJ$ of two twisted plies is substantially higher than for a single ply, and this resists loop closure, producing larger, more rounded loop heads consistent with micro-CT measurements. See [[wakamatsu-2024]] for full details.

## du Pasquier et al. 2025 — volumetric FEA

Du Pasquier et al. 2025 introduce a **volumetric solid-element FEA** of the stitch rather than a 1D rod model. Each yarn is meshed as a 3D solid extruded along the Crane 2023 centerline (see [[crane-2023]]):

- **Unit cell**: 2×2 stitches (2 course × 2 wale); periodic boundary conditions match node/edge pairs.
- **Elements**: quadratic tetrahedral C3D10 with seed size R/3; captures radial deformation and contact over the full yarn cross-section.
- **Material**: cotton/nylon modeled as transversely isotropic (experimental data fed directly); PET as isotropic.
- **Pre-stress step**: thermal expansion inflates yarn from initial undersize to measured post-knit diameter $d_k$, establishing in-fabric contact state before any external loading.
- **Loading**: biaxial equibiaxial stretching in course and wale directions; validated against custom biaxial stage with DIC.
- **Validation**: NRMSE < 5% across most stitch lengths, patterns, and yarn materials.

This approach is the highest-fidelity framework in the comparison table: it resolves yarn cross-section deformation and can capture inter-yarn friction and contact area. However, it requires tens of hours of compute per configuration, which motivates the HGO surrogate model (see [[du-pasquier-2025]] and [[hgo-strain-energy]]).

See also [[crane-2023]] for the parametric centerline used to define the stitch geometry in this model.

## Comparison of simulation frameworks

| Feature | Kaldor 2008 | Bézier / energy-min. | B-spline / Lagrangian | du Pasquier 2025 | Demiroz 2000 | Wadekar 2020 | Yuksel 2012 | Wakamatsu 2024 |
|---|---|---|---|---|---|---|---|---|
| Source | Kaldor et al. | Dimitriyev/Singal | Ding et al. 2023 | du Pasquier et al. | Demiroz & Dias | Wadekar et al. | Yuksel et al. | Wakamatsu et al. |
| Curve type | Cubic B-spline | Cubic Bézier | Cubic B-spline | 3D solid (C3D10) | Cubic spline (5 CP) | Helicoid curve | Cubic B-spline | Discrete quaternion rod |
| Dynamics | Full (DAE/ICD) | Static min. | Full (RK4) | Static (ABAQUS) | None | None | Static (mass-spring) | Static min. |
| Extensibility | Inextensible | Inextensible | Extensible | Extensible | Inextensible | Not explicit | Not explicit | Extensible |
| Contact | Stiff penalty | Hertz (Δ^{5/2}) | Quadratic spring | Full contact/friction | Diameter constraint | Surface constraint | Contact avoidance | Hard-core |
| Cross-section | 1D rod | 1D rod | 1D rod | Full 3D solid | 1D rod | 1D rod | 1D rod | 1D rod |
| Yarn anisotropy | None | None | None | Transv. isotropic | None | None | None | None |
| Scale | Full garment | Unit cell | Full fabric | 2×2 unit cell | Unit cell | Unit cell | Full garment | Unit cell |
| Primary goal | CG animation | Physics/mechanics | Mechanics | Physics/design | Graphics geometry | Pattern geometry | CG animation | Stitch shape |

The B-spline framework (Ding) uses explicit RK4 with a precomputed banded mass matrix; the Bézier framework (Dimitriyev/Singal) uses scipy constrained optimization. The du Pasquier volumetric FEA is the highest-fidelity approach but requires tens of hours per configuration. The geometric models (Demiroz, Wadekar, Yuksel, Wakamatsu) do not produce mechanical constitutive data but serve as geometry generators for rendering and as initial configurations for mechanics simulations.

See [[ding-2023]], [[dimitriyev-notes-2019]], [[kaldor-2008]], [[du-pasquier-2025]], [[demiroz-2000]], [[wadekar-2020]], [[yuksel-2012]], and [[wakamatsu-2024]] for full details.

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
- [[demiroz-2000]]
- [[wadekar-2020]]
- [[yuksel-2012]]
- [[wakamatsu-2024]]
- [[du-pasquier-2025]]
- [[crane-2023]]
