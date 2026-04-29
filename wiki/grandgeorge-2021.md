# Grandgeorge et al. 2021 — Mechanics of Two Filaments in Tight Orthogonal Contact

**Summary**: PNAS 2021 (EPFL, Reis group). Performs a detailed experimental (μCT) and computational (FEM) study of two elastic rods brought into tight contact in orthogonal planes — the "elastic orthogonal clasp." Finds that even frictionless contact produces a diamond-shaped contact region with highly heterogeneous pressure ridges; friction breaks symmetry and produces a capstan-like tension ratio. Directly relevant to yarn-yarn crossings in knitting.

**Sources**: `raw/Grandgeorge et al. - 2021 - Mechanics of two filaments in tight orthogonal con.pdf`

**Last updated**: 2026-04-17

---

## The elastic orthogonal clasp

The **elastic orthogonal clasp** is the canonical contact problem for two flexible filaments: rod A and rod B lie in orthogonal planes, clamped at their ends, brought into contact by reducing the wall-to-wall distance H. The system is the simplest instance of filament–filament contact — a building block for knits, knots, and weaves.

Physical realisation: silicone elastomer rods (diameter D = 8.5 mm), imaged with μCT and simulated with FEM (ABAQUS, 3D brick elements with C3D8RH formulation).

---

## Contact geometry: the diamond contact region

### Frictionless case

Even without friction, the contact between the two rods is **not a point**. The contact region is a closed, curvilinear **diamond-shaped surface patch**, with an inner gap separating the rod tips near the centre.

Key geometric features:
- Four **pressure ridges** connecting four isolated pressure peaks near the diamond corners
- Low pressure in the interior (central valley surrounded by ridges)
- The ideal orthogonal clasp (inextensible, perfectly flexible tubes, circular cross-section) predicts the **contact lines** (a 1D skeleton) with good qualitative accuracy
- The four peaks arise close to the four apices (corners) of the ideal diamond

### Cross-section deformation

The elastic rod cross-sections deform significantly at the contact — flattening by up to 10%, centerline curvature up to ~10% of rod curvature, and shear strains up to ~10%. This means simplified Kirchhoff rod models (which assume indeformable cross-sections) are **quantitatively inadequate**, though geometrically qualitative.

### Load dependence

Local opening angles θ_A and θ_B (tangent angles at touch-down and lift-off points) decrease monotonically as the normalised vertical force f_z = F_z/EA increases — the clasp tightens. The Kirchhoff-capstan approximation (single rod around a rigid cylinder) predicts local opening angles poorly.

---

## Contact pressure distribution

FEM contact-pressure maps (normalised by EA/D²) show:

- **Static case (no friction)**: fourfold symmetric diamond; four pressure peaks at diamond apices; ridges concentrated along curvilinear diamond contact lines
- **Higher loading**: pressure becomes more uniform over the interior; ridges less visible
- All three cases (equal long rods, equal short rods, mixed) show diamond structure at moderate loading f_z ≈ 0.05

The ideal orthogonal clasp contact-line prediction (purely geometric, no mechanics) closely matches the FEM ridge locations and the experimentally measured contact boundaries — remarkably accurate given the 10% cross-section deformations.

---

## Effect of friction: the frictional sliding clasp

With friction (μ = 0.32 ± 0.03, Amontons–Coulomb), rod A is made to slide against static rod B. Key results:

- **Symmetry broken**: fourfold → twofold. Only three pressure peaks instead of four; one peak gains dominance at the high-tension (lift-off) corner of rod A
- **Tension ratio K = T₁/T₀** between the two ends of rod A increases monotonically with the normalised dead-load tension t₀ = T₀/EA
- Capstan equation (T₁/T₀ = e^{μφ}, where φ = global opening angle): gives correct order of magnitude but systematically misfits because K depends on both the local geometry of B and the winding configuration of A
- Correct description requires a **V-belt capstan analogy** using the ideal orthogonal clasp geometry of B as the effective drum shape

The FEM correctly predicts K(t₀) for all four configurations (mean difference ≈ 4.2%).

---

## Relevance to knitted fabrics

Each yarn crossing in a knitted stitch is an instance of the elastic orthogonal clasp. Implications:

1. **Contact geometry**: yarn contacts are extended diamond regions, not point contacts. Pressure is heterogeneous and ridge-dominated — important for models that assume Hertzian or point contact.
2. **Friction and hysteresis**: the asymmetric pressure distribution under sliding generates a capstan-like tension ratio. This is the microscopic origin of the hysteresis and stick-slip behaviour observed in [[crackling-dynamics]] and [[return-point-memory]].
3. **Hysterons in the Preisach model**: the bistable yarn contacts that Dresselhaus et al. 2025 model as hysterons are physically elastic orthogonal clasps with frictional switching.
4. **Tube radius matters**: even a small but nonzero filament radius qualitatively changes the contact topology (extended contact vs. point) — justifying the use of finite-radius yarn models in simulations.

The paper explicitly names knits, knots, and weaves as targets for future homogenisation, with the orthogonal clasp as the building block.

---

## Related pages

- [[yarn-contact]]
- [[return-point-memory]]
- [[crackling-dynamics]]
- [[yarn]]
- [[yarn-simulation]]
- [[stitch-topology]]
