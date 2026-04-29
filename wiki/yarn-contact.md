# Yarn Contact Mechanics

**Summary**: At each stitch crossing, two yarn segments meet in near-orthogonal contact. The mechanics of this contact — contact geometry, pressure distribution, and friction — govern hysteresis, crackling, and memory in knitted fabrics. The canonical model is the elastic orthogonal clasp (Grandgeorge et al. 2021).

**Sources**: `raw/Grandgeorge et al. - 2021 - Mechanics of two filaments in tight orthogonal con.pdf`, `raw/notes_for_Tim.pdf`, `raw/Singal_NatureComm_2024.pdf`

**Last updated**: 2026-04-17

---

## The contact geometry at a stitch crossing

In a knitted stitch, the yarn from one course passes through the loop of the previous course, creating a contact where two yarn segments cross at approximately 90°. This is an instance of the **elastic orthogonal clasp**: two elastic rods in orthogonal planes forced into tight contact.

Key geometric result (Grandgeorge et al. 2021): the contact region is a **closed, curvilinear diamond** — not a point. Even without friction, four pressure ridges connect four high-pressure peaks near the diamond corners, with an inner gap and low central pressure.

The **ideal orthogonal clasp** (perfectly flexible, inextensible tubes) provides a 1D geometric skeleton that accurately predicts the shape and location of the pressure ridges, despite the significant cross-section deformation (~10% flattening) observed in real elastic rods.

---

## Hertz vs. clasp contact models

Different models used in the knitting simulation literature:

| Model | Used in | Assumption |
|---|---|---|
| Hertz potential ∝ Δ^(5/2) | Dimitriyev 2019 | Spherical indentation; symmetric; no friction |
| Quadratic spring | Ding et al. 2023 | Penalty force on overlap; no friction |
| Stiff penalty + contact damping | Kaldor et al. 2008 | Explicit friction via velocity filter |
| Full orthogonal clasp | Grandgeorge et al. 2021 | Elastic rods; FEM; measured friction μ |

The Hertz and quadratic spring models treat the contact as effectively point-like and symmetric — an approximation that misses the diamond structure and the tension asymmetry induced by friction. The full FEM treatment (Grandgeorge) is currently too expensive for fabric-scale simulation.

---

## Friction and the capstan effect

When one yarn slides against a crossed yarn, the tension ratio between the two ends obeys a capstan-like relation:

$$K = \frac{T_1}{T_0} = e^{\mu\varphi}$$

where μ is the Coulomb friction coefficient and φ is the effective winding angle. However, the simple capstan equation (which assumes a rigid cylindrical drum) systematically underestimates K because the actual drum shape (rod B) is itself deformable and the effective φ depends on the local opening angle — which changes with applied load.

Key consequence: **friction creates a tension asymmetry** at every yarn crossing. During loading, contacts lock and build up tension asymmetry; during unloading, contacts slip the other way. This is the microscopic origin of:

- **Hysteresis** in cyclic loading (loading stiffness ≠ unloading stiffness)
- **Crackling noise**: each slip is a sudden jump in the tension ratio (source: [[crackling-dynamics]])
- **Yarn contacts as hysterons**: bistable switching at a threshold — the physical basis of the Preisach model for [[return-point-memory]]

Measured friction coefficient for silicone elastomer rods: μ = 0.32 ± 0.03 (Grandgeorge 2021). Values for yarn materials (nylon, acrylic, wool) differ and are typically measured indirectly from hysteresis ratio.

---

## Contact damping in simulation

In dynamic simulations (Kaldor et al. 2008, [[kaldor-2008]]), friction is approximated by a contact damping term:

$$D^\text{collision}_{(i,j)} = \ell_i \ell_j \int_0^1\int_0^1 \left(k_{dt}|\Delta \mathbf{v}_{ij}|^2 - (k_{dt}-k_{dn})(\hat{\mathbf{n}}_{ij}^T \Delta \mathbf{v}_{ij})^2\right) ds\,ds'$$

where k_{dt} controls tangential damping (friction proxy) and k_{dn} controls normal damping (elastic rebound). This is not a Coulomb friction model but approximates the dissipative effect for dynamic simulation.

---

## Contact in the unit-cell model

In the Dimitriyev/Singal framework ([[yarn-simulation]]), contacts are distributed along yarn segments using ~10 spheres per segment. The Hertz potential penalises overlaps. This correctly captures the repulsion geometry but not the asymmetric friction effect.

The singal group used a hard-core soft-shell experimental contact model: measuring force-displacement curves for yarn-yarn compression and fitting a contact potential informed by those experiments (source: Singal_NatureComm_2024.pdf).

---

## Related pages

- [[grandgeorge-2021]]
- [[yarn]]
- [[yarn-simulation]]
- [[return-point-memory]]
- [[crackling-dynamics]]
- [[stitch-topology]]
- [[kaldor-2008]]
