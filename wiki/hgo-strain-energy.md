# HGO Strain Energy Model for Knitted Fabrics

**Summary**: A three-parameter homogenized strain energy model for weft-knitted fabrics, based on the anisotropic Holzapfel-Gasser-Ogden (HGO) framework. The parameters $a$ (initial stiffness), $b$ (stiffness growth rate), and $\theta_\text{HGO}$ (anisotropy direction) have direct physical interpretations and can be fitted in minutes from biaxial stress-strain data.

**Sources**: `raw/Chen_2025_Multilevel_Mechanical_Modeling_Weft_Knit.pdf`

**Last updated**: 2026-05-15

---

> **Notation warning**: The angle $\theta_\text{HGO}$ in this model denotes the fabric anisotropy direction (the angle between the preferred stiffness axis and the course direction). It is distinct from the Euler angles $\theta_1, \theta_2, \theta_3$ used in the [[yarn-simulation]] crossover parameterisation, and from the fiber twist angle $\theta(t)$ in [[crane-2023]].

---

## Strain energy density

$$\psi = \frac{a}{b}\left[\exp\!\left(b\,(I_4 - 1)^2\right) - 1\right]$$

where $I_4$ is the fourth pseudo-invariant of the deformation tensor $\mathbf{F}$:

$$I_4 = [\mathbf{F}^T \cdot \mathbf{F}] : \mathbf{N} = \lambda_1^2\cos^2\theta_\text{HGO} + \lambda_2^2\sin^2\theta_\text{HGO}$$

Here $\lambda_1$ is the course-direction stretch, $\lambda_2$ is the wale-direction stretch, and $\mathbf{N} = [\cos\theta_\text{HGO}, \sin\theta_\text{HGO}, 0]^T$ is the in-plane anisotropy direction.

## Stress (first Piola-Kirchhoff)

$$\mathbf{P} = \frac{\partial\psi}{\partial\mathbf{F}} = 2a(I_4 - 1)\exp\!\left(b\,(I_4-1)^2\right)\left[2\lambda_1\cos^2\theta_\text{HGO},\; 2\lambda_2\sin^2\theta_\text{HGO}\right]^T$$

In the low-stress limit ($I_4 \approx 1$), the exponential $\approx 1$ and $\psi \approx a(I_4 - 1)^2$, giving a quadratic (linear stress-stretch) regime. At higher stretch, the exponential drives rapid stiffening — consistent with the J-shaped fabric response (see [[stress-strain-curve]]).

## Parameters and physical meaning

| Parameter | Role | Primary design lever |
|---|---|---|
| $a > 0$ | Initial stiffness scale | Yarn material (cotton, nylon, PET) |
| $b > 0$ | Exponential stiffness growth rate | Stitch length (shorter → larger $b$) |
| $\theta_\text{HGO} \in (0°, 90°)$ | Angle of preferred stiffness axis from course direction | Stitch pattern (Jersey, Garter, Rib, Seed) |

Empirical rules from du Pasquier et al. 2025 (source: Chen_2025_Multilevel_Mechanical_Modeling_Weft_Knit.pdf):

- **Stitch length** primarily changes $b$: shorter stitches → denser fabric → larger $b$ (faster stiffening).
- **Pattern** primarily changes $\theta_\text{HGO}$: Rib and Seed shift the anisotropy angle substantially; Jersey is close to $\theta_\text{HGO} \approx 45°$ (nearly isotropic under equibiaxial loading).
- **Yarn material** changes both $a$ and $b$ by up to an order of magnitude, but has little effect on $\theta_\text{HGO}$.

## Fitting procedure

Parameters are fitted by minimizing the squared difference between model prediction and measured stress-strain data:

$$\underset{\mathbf{x} = [a,b,\theta_\text{HGO}]^T}{\operatorname{argmin}} \sum_{i=1}^n \|\mathbf{S}_i - \mathbf{P}_i(\mathbf{x})\|^2$$

Solved using the MADS (Mesh Adaptive Direct Search) algorithm (Audet & Le Digabel 2022). Under typical loading ranges, fitting requires only a few minutes on a laptop.

## Validation

- Normalized RMSE (NRMSE) against biaxial experiments: generally < 5% for SL11 and most patterns across all three yarn materials.
- Exceptions: SL10 (tight contact causes initial interference in FEA) and SL12 (long stitches have an initial slack / flat response that the exponential model misses).

## Relation to other constitutive models in the wiki

The Singal 2024 model ([[constitutive-model]]) uses an additive form $\sigma = Y\varepsilon + \beta(1-\alpha\varepsilon)^{-2}$ with 6 parameters (3 per direction). The HGO model:
- Is a stored-energy (hyperelastic) formulation — thermodynamically consistent
- Has only 3 parameters total, capturing both directions simultaneously via the coupling through $I_4$
- Treats both directions as coupled (the same $I_4$ mixes $\lambda_1$ and $\lambda_2$)
- Is already implemented in commercial FEA codes (ABAQUS)

Both reproduce the J-shaped curve (see [[knit-elasticity]], [[stress-strain-curve]]); the HGO model is better suited for integration into larger garment-scale FEA workflows.

## Related pages

- [[constitutive-model]]
- [[knit-elasticity]]
- [[stress-strain-curve]]
- [[stitch-types]]
- [[wale-and-course]]
- [[yarn]]
- [[du-pasquier-2025]]
- [[tangent-modulus]]
