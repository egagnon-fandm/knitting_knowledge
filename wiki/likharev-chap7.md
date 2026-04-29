# Likharev Chapter 7: Deformations and Elasticity

**Summary**: LibreTexts Chapter 7 (Konstantin Likharev, CC BY-NC-SA) gives a rigorous physics-textbook treatment of 3D continuum mechanics: the strain tensor, stress tensor, Hooke's law in full tensor form, static equilibrium, rod bending, rod torsion, and elastic wave propagation.

**Sources**: `raw/Chap7.pdf`

**Last updated**: 2026-04-16

---

## Scope

Sections covered: 7.1 Strain, 7.2 Stress, 7.3 Hooke's Law, 7.4 Equilibrium, 7.5 Rod Bending, 7.6 Rod Torsion, 7.7 3D Acoustic Waves, 7.8 Elastic Waves in Thin Rods.

This chapter provides the continuum-mechanics foundation implicitly assumed by the knitting elasticity literature (particularly [[poincloux-prx-2018]] and [[constitutive-model]]).

---

## 7.1 Strain tensor

The symmetrized strain tensor is:

$$s_{jj'} = \frac{1}{2}\left(\frac{\partial q_j}{\partial r_{j'}} + \frac{\partial q_{j'}}{\partial r_j}\right)$$

where **q**(**r**) is the displacement vector. Diagonal elements describe compression/extension; off-diagonal elements describe shear. The trace Tr(**s**) = ∑s_jj gives the fractional volume change ΔV/V.

Curvilinear forms: cylindrical and spherical coordinate expressions are given (Eqs. 7.1.17–7.1.18).

---

## 7.2 Stress tensor

The stress tensor σ_ij relates force **dF** to area element **dA** via:

$$dF_j = \sum_{j'} \sigma_{jj'} dA_{j'}$$

The Euler-Cauchy stress principle gives an effective body force density:

$$(f_\text{ef})_j = \sum_{j'} \frac{\partial \sigma_{jj'}}{\partial r_{j'}}$$

Newton's law for a continuum element:

$$\rho \frac{\partial^2 q_j}{\partial t^2} = \sum_{j'} \frac{\partial \sigma_{jj'}}{\partial r_{j'}} + f_j$$

Elastic strain energy density: $u(\mathbf{r}) = \frac{1}{2}\sum_{j,j'} \sigma_{jj'} s_{jj'}$.

---

## 7.3 Hooke's Law

For a linear elastic isotropic medium, Hooke's law decomposes the strain tensor into a shear part (traceless) and a volumetric part:

$$\sigma_{jj'} = 2\mu\left(s_{jj'} - \frac{1}{3}\delta_{jj'}\,\text{Tr}(\mathbf{s})\right) + 3K\left(\frac{1}{3}\delta_{jj'}\,\text{Tr}(\mathbf{s})\right)$$

- **μ** (shear modulus): resistance to shape change at constant volume
- **K** (bulk modulus): resistance to volume change

These relate to the more common pair (E, ν) via:

$$E = \frac{9K\mu}{3K+\mu}, \qquad \nu = \frac{3K - 2\mu}{2(3K+\mu)}$$

Table 7.1 values (approximate):

| Material | K (GPa) | μ (GPa) | E (GPa) | ν |
|---|---|---|---|---|
| Diamond | 600 | 450 | 1100 | 0.20 |
| Hardened steel | 170 | 75 | 200 | 0.30 |
| Water | 2.1 | 0 | 0 | 0.5 |

Note that rubber and soft polymers are not listed — they are non-Hookean (see [[hookes-law]]).

---

## 7.4 Equilibrium

Static equilibrium (no body forces) reduces to:

$$\nabla^4(\nabla \cdot \mathbf{q}) = 0$$

For force-free boundary conditions, Young's modulus E drops out entirely; only Poisson's ratio ν appears in the deformation distribution.

Worked example: thick spherical shell under internal/external pressure — full analytic solution for displacement and stress fields.

---

## 7.5 Rod Bending

For a quasi-uniform rod bent by torque τ_y, the longitudinal stress is:

$$\sigma_{zz} = -E\frac{x}{R}$$

where x is measured from the neutral line and R is the radius of curvature. The torque–curvature relation is:

$$\frac{1}{R} = \frac{\tau_y}{EI_y}, \qquad I_y \equiv \int_S x^2\,dx\,dy$$

I_y is the **moment of inertia** of the rod's cross-section about the neutral axis, and scales as a^4 with the linear size a. Bending rigidity therefore grows as a^4.

Global bending law (small transverse displacement q_x(z)):

$$\frac{d\tau_y}{dz} = -F_x, \qquad \frac{d^2 q_x}{dz^2} \approx \frac{\tau_y}{EI_y}$$

Example: cantilever under distributed load q = ρgA gives end deflection q_x(l) = ρgAl^4/(8EI_y).

**Relevance**: the Cornelissen 2009 cantilever protocol for measuring yarn bending stiffness uses exactly this result (see [[cornelissen-2009]] and [[yarn]]).

---

## 7.6 Rod Torsion

For a rod twisted by torques ±τ_z, the torsional rigidity is:

$$C = \mu I_z, \qquad I_z \equiv \int_A (x^2 + y^2)\,dx\,dy$$

for axisymmetric cross-sections. For a solid round rod of radius R: C = (π/2)μR^4. For a thin hollow pipe: C = 2πμR^3t.

For non-axisymmetric cross-sections, the deformation function ψ(x,y) satisfies a Poisson equation, and the naïve I_z formula gives wrong results. A narrow rectangular bar (w × t, t ≪ w) gives C = (1/6)μwt^3.

---

## 7.7–7.8 Elastic Waves

Two wave modes in 3D isotropic solids:

- **Longitudinal** (compressional): $v_l^2 = (K + 4\mu/3)/\rho$
- **Transverse** (shear): $v_t^2 = \mu/\rho$

In fluids (μ = 0): only longitudinal waves survive, with $v_l = \sqrt{K/\rho}$.

---

## Related pages

- [[stress]]
- [[constitutive-model]]
- [[hookes-law]]
- [[deformation]]
- [[strain]]
- [[yarn]]
- [[cornelissen-2009]]
- [[poisson-ratio]]
