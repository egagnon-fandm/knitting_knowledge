# du Pasquier, Jeong et al. 2025 — Multi-Level Mechanical Modeling of Weft Knitted Fabrics

**Summary**: A three-level framework for weft-knitted fabrics: experimental yarn characterization feeds a volumetric FEA model, which is then homogenized into a fast HGO strain energy surrogate with only three parameters. The framework scales to heterogeneous fabrics (springs in series/parallel) and was used to design a compression sleeve with spatially uniform stress.

**Sources**: `raw/Chen_2025_Multilevel_Mechanical_Modeling_Weft_Knit.pdf`

**Last updated**: 2026-05-17

---

## Citation

du Pasquier, C.\*, Jeong, S.\*, Liu, P., Williams, S., Mnejja, N., Okamura, A. M., Tibbits, S., Chen, T. (2025). Multi-level mechanical modeling and computational design framework for weft knitted fabrics. arXiv:2501.07567v3. (\*equal contribution)

Stanford CHARM Lab (Mechanical Engineering) · MIT Self-Assembly Lab · University of Houston (Architected Intelligent Matter Lab).

## Overview

The framework has three levels:

1. **Yarn level** — experimental characterization of anisotropic yarn mechanics
2. **Stitch level** — volumetric FEA of a 2×2 representative unit cell
3. **Fabric level** — HGO strain energy surrogate fitted from FEA/experiment; extended to heterogeneous fabrics via spring analogies

The key design knobs are three **knitting variables**: stitch length (SL), stitch pattern (Jersey / Garter / Rib / Seed), and yarn material.

## Yarn characterization

Three yarns were tested to span a wide mechanical range:

| Yarn | Type | Tensile range |
|---|---|---|
| Cotton 20/2 (Supreme Corp.) | Staple, 2-ply | Low elongation (<10%) |
| Nylon HT 70-denier 24-fil 2-ply (Hickory) | Textured multi-filament | High elongation (>120%) |
| PET monofilament 0.178 mm (Thread Exchange) | Extruded monofilament | Intermediate, elastic |

Cotton and nylon are **transversely isotropic**: transverse (compressive) stiffness is orders of magnitude below longitudinal tensile stiffness. PET is isotropic. The **free-standing diameter $d_0$** is distinguished from the **post-knit diameter $d_k$** (compressed by contact forces during knitting); the difference quantifies yarn pre-stress. Compression tests use yarns pre-tensioned to $d_k$ to match the in-fabric state (source: Chen_2025_Multilevel_Mechanical_Modeling_Weft_Knit.pdf §2).

## FEA model

- **Geometry**: yarn centerline from Crane 2023 parametric model (see [[crane-2023]]); stitch arc lengths measured from 16× microscopy images: SL10 → 3.9 mm, SL11 → 4.7 mm, SL12 → 5.9 mm.
- **Unit cell**: 2×2 stitches (2 course × 2 wale); periodic boundary conditions match node/edge pairs.
- **Mesh**: quadratic tetrahedral elements (C3D10), seed size = R/3.
- **Pre-stress step**: yarn started with reduced diameter; thermal expansion gradually inflates it to $d_k$ without changing length — replicates contact-induced compression during manufacture.
- **Loading**: biaxial prescribed displacements in course (X) and wale (Y) directions.
- **Solver**: ABAQUS/Standard 2022.
- **Validation**: NRMSE < 5% in most cases. Exceptions: SL10 (tight contact causes interference) and SL12 (initial slack produces a flat low-strain regime the exponential model misses).

## HGO strain energy model

The FEA is computationally expensive (~tens of hours). The surrogate is based on the **Holzapfel-Gasser-Ogden (HGO)** model, already built into ABAQUS:

$$\psi = \frac{a}{b}\!\left[\exp\!\left(b(I_4-1)^2\right) - 1\right]$$

$$I_4 = \lambda_1^2\cos^2\theta + \lambda_2^2\sin^2\theta$$

where $\lambda_1$ = course stretch, $\lambda_2$ = wale stretch, and $\mathbf{N} = [\cos\theta,\sin\theta,0]^T$ is the anisotropy direction. The first Piola-Kirchhoff stress:

$$\mathbf{P} = 2a(I_4-1)\exp\!\left(b(I_4-1)^2\right)\!\left[2\lambda_1\cos^2\theta,\, 2\lambda_2\sin^2\theta\right]^T$$

Parameters are fitted by minimizing squared residuals using the MADS algorithm (a few minutes on a laptop). See [[hgo-strain-energy]] for the full model description.

**Physical interpretation of parameters:**

| Parameter | Primary driver | Effect |
|---|---|---|
| $a > 0$ | Yarn material | Sets initial stiffness scale |
| $b > 0$ | Stitch length | Controls exponential stiffening rate; shorter SL → larger $b$ |
| $\theta \in (0°,90°)$ | Stitch pattern | Anisotropy direction; Rib/Seed shift $\theta$ substantially; Jersey ≈ 45° (near-isotropic biaxial) |

Material changes $a$ and $b$ by up to an order of magnitude but barely affects $\theta$.

## Heterogeneous fabrics

Industrial fabrics routinely mix yarns or patterns across regions. This paper shows that **material transitions obey simple mechanical analogies**:

- **Parallel** (interface parallel to load axis, e.g., intarsia column transitions): response is the weighted average of the two homogeneous regions — no interface correction needed.
- **Series** (interface perpendicular to load axis, e.g., row transitions): each region deforms independently according to its homogeneous behavior.

Digital Image Correlation (DIC) confirms the interface itself does not redistribute load. This lets the full framework scale to heterogeneous garments by treating each patch as a homogeneous element. The current model covers classic row/column transitions; slanted or multi-layer transitions are future work.

## Compression sleeve application

A compression sleeve was designed to deliver spatially uniform stress on a muscular arm:

1. 3D arm scan → quadrilateral mesh; wrist-circumference cylinder as reference.
2. Estimated strain field at each mesh element from geometry difference.
3. HGO model inverted to find knit parameters $(a, b, \theta)$ minimizing stress variance across the sleeve.
4. High-strain regions replaced with nylon in rib pattern (most compliant option).
5. Fabricated on a Stoll CMS 330 machine; validated with Tekscan FlexiForce sensors pre/post exercise.

Result: uniform compression maintained under varying physiological conditions (muscle flexion). Demonstrated concept for garments for pregnancy support or heavy-load carrying.

## Relation to other constitutive models

| Model | Source | Parameters | Coupling | Thermodynamic consistency |
|---|---|---|---|---|
| Singal 2024 | [[constitutive-model]] | 6 (3 per direction) | None (directions independent) | No (phenomenological) |
| HGO | [[hgo-strain-energy]] | 3 (shared) | Via $I_4$ | Yes (stored energy) |

## Related pages

- [[hgo-strain-energy]]
- [[crane-2023]]
- [[constitutive-model]]
- [[knit-elasticity]]
- [[stitch-types]]
- [[knitted-fabrics]]
- [[yarn]]
- [[yarn-simulation]]
- [[wale-and-course]]
- [[tangent-modulus]]
