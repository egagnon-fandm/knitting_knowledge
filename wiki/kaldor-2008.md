# Kaldor et al. 2008 — Simulating Knitted Cloth at the Yarn Level

**Summary**: ACM SIGGRAPH 2008 paper (Cornell, Kaldor/James/Marschner). First practical yarn-level simulation of knitted cloth for computer graphics. Models yarn as an inextensible B-spline tube with bending resistance and stiff contact penalties; friction via rigid-body velocity filters. Demonstrates that garter, stockinette, and rib patterns emerge from yarn topology without per-pattern tuning.

**Sources**: `raw/Kaldor et al. - Simulating Knitted Cloth at the Yarn Level.pdf`

**Last updated**: 2026-04-17

---

## Context and motivation

Prior cloth simulators approximated knitted fabric as a linear-elastic sheet — a model that is fundamentally wrong for knits because: (1) knit loops stretch freely in one direction while compressing in the other; (2) the coupling between the two directions is highly nonlinear; (3) the curling of stockinette and rib compression require yarn-level kinematics to capture correctly.

Kaldor et al. argue that a yarn-level model is both necessary for realism and practical at the scale of garments (scarves, leg warmers).

---

## Physical model

### Yarn kinematics

Each yarn is an **inextensible cubic B-spline** with constant radius r = 0.125 cm (for wool worsted size 8). Each spline segment i has:
- Arc length ℓ_i (fixed; inextensibility constraint C_i^len = 0)
- Mass per unit length m_unit
- 8 control points per knit loop (average)

The yarn velocity is v(s) = Σ b_k(s) q̇_k where b_k are B-spline basis functions.

### Energy and forces

**Bending energy** (quadratic in curvature):

$$E_i^\text{bend} = k_\text{bend}\,\ell_i \int_0^1 \kappa_i(s)^2\,ds$$

where κ_i(s) = ‖y_i'(s) × y_i''(s)‖ / ‖y_i'(s)‖³ is the unsigned curvature.

**Contact energy** between non-adjacent segments i, j (|i−j| > 1):

$$E^\text{contact}_{(i,j)} = k_\text{contact}\,\ell_i\ell_j \int_0^1\int_0^1 f\!\left(\frac{\|\mathbf{y}_i(s') - \mathbf{y}_j(s)\|}{2r}\right) ds\,ds'$$

with $f(d) = 1/d^2 + d^2 - 2$ for d < 1, zero otherwise. This diverges as yarns approach contact (d → 0), preventing interpenetration.

**Inextensibility constraint** (one per segment):

$$C_i^\text{len} = 1 - \frac{1}{\ell_i}\int_0^1 \|\mathbf{y}_i'(s)\|\,ds = 0$$

### Damping and friction

Three damping models are used:

1. **Mass-proportional (global)**: D_i^global = k_global ∫ v_i(s)^T v_i(s) ds — applied during relaxation to initial rest state
2. **Contact damping**: D^collision_{(i,j)} with tangential coefficient k_{dt} and normal coefficient k_{dn} — approximates friction at yarn crossings
3. **Non-rigid motion damping**: rigid-body velocity filter — damps relative motion of nearby yarn regions (models fuzz and stray fibre friction); uses two scales of overlapping regions (per row/column and per two rows/columns)

Explicit Coulomb friction is **not modelled** — the contact damping is an approximation. The authors acknowledge friction as a critical missing element for quantitative hysteresis.

### Integration

The system is a DAE (differential algebraic equation) stepped with the **Implicit Constraint Direction (ICD)** method. Each timestep:
1. Unconstrained step
2. satisfy_constraints (constraint projection)
3. filter_velocity (velocity filter for non-rigid damping)

Typically 4–5 linear solver iterations per timestep. Collision evaluation uses AABB spatial hierarchy and spatial culling (most segment pairs are non-contacting).

---

## Initial configuration generation

Given a knit pattern (stitch sequence), the algorithm:
1. Builds a stitch topology graph
2. Fits a cubic B-spline to template stitch curves, stitch by stitch
3. Shrinks the yarn by factor c = 0.935 (to compress the cloth and settle to rest state)
4. Relaxes with high damping to find equilibrium

The rest state is then used as initial condition for dynamic simulation.

---

## Results

**Knit patterns reproduced** (from identical yarn, without any pattern-specific tuning):
- Garter: same pattern on both sides; compresses in wale direction ✓
- Stockinette: front/back asymmetry; curls at edges ✓ (model over-curls slightly — lack of friction model)
- 2-2 Rib: short course direction; rib columns interdigitate ✓

**Stretch tests**: rib in course direction matches measured stress-strain curve qualitatively. Elastic sheet model gets garter wrong (uniform deformation instead of yarn rearrangement).

**Scenes**: 20×160 stitch scarf falling on a plane (64,690 segments; ~10.7 min/frame); 44×96 stitch leg warmer pulled over foot.

**Simulation statistics**: yarn collisions ~52–58% of total compute time; 6–11 min per frame on 4-core 2.66 GHz machine.

---

## Position in simulation literature

| Feature | Kaldor 2008 | Dimitriyev 2019 | Ding 2023 |
|---|---|---|---|
| Curve type | B-spline | Bézier | B-spline |
| Dynamics | Full (DAE/ICD) | Static minimisation | Full (RK4) |
| Friction | Velocity filter (approx.) | None | Explicit k_{dt} |
| Scale | Full garment | Unit cell | Full fabric |
| Primary goal | Computer graphics | Physics / mechanics | Mechanics |

Kaldor 2008 was the first to demonstrate yarn-level garment simulation at practical speeds. The physics-focused literature (Dimitriyev, Ding) later adopted similar yarn representations but prioritised quantitative mechanics over animation speed.

---

## Related pages

- [[yarn-simulation]]
- [[yarn]]
- [[yarn-contact]]
- [[stitch-types]]
- [[knitted-fabrics]]
- [[ding-2023]]
- [[dimitriyev-notes-2019]]
