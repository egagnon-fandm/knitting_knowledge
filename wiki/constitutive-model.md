# Constitutive Model

**Summary**: The stress-strain behavior of knitted fabrics is captured by a two-term constitutive model combining a linear elastic term (low stress, bending-dominated) and a strain-stiffening term (high stress, contact-dominated), with parameters that depend on stitch type and extension direction.

**Sources**: `raw/Singal_NatureComm_2024.pdf`, `raw/Poincloux_PRX_2018.pdf`, `raw/Chap7.pdf`, `raw/Nonlinear_Problems_of_Elasticity.pdf`

**Last updated**: 2026-04-21

---

## Full constitutive relation (Singal 2024)

$$\sigma(\varepsilon) = \sigma_\text{low}(\varepsilon) + \sigma_\text{high}(\varepsilon)$$

### Low-stress term
$$\sigma_\text{low}(\varepsilon) \approx Y \varepsilon$$

Linear, with $Y$ the Young's modulus set by [[stitch-topology]] and [[yarn]] bending modulus. Different for each fabric type and direction.

### High-stress term
$$\sigma_\text{high}(\varepsilon) \approx \beta(1 - \alpha\varepsilon)^{-2}$$

A diverging term as $\varepsilon \to 1/\alpha$, representing the maximum extensibility of the stitch. Parameters $\beta$ and $\alpha$ depend on the extension direction. The form resembles the worm-like chain force-extension relationship for stiff polymers (Marko & Siggia, cited in Singal 2024) and amorphous fiber network models.

Parameters $Y$, $\alpha$, $\beta$ are independently determined for both x and y directions, giving 6 parameters per fabric type.

## First-principles model (Poincloux PRX 2018)

For homogeneously deformed stockinette under wale-direction strain $\varepsilon_h$:

$$F(\varepsilon_h) = \tilde{Y} N_c \delta_{w^*}^2 \left[\frac{1}{(1+\varepsilon_h)^2} - \frac{1}{(1-\delta\frac{w^*}{c^*}\varepsilon_h)^2}\right]$$

Key features:
- Derived from minimizing bending energy subject to yarn length conservation and topological constraints — no phenomenology
- The parameter $\tilde{Y} = \tilde{B}/(c^* w^*)$ is the only adjustable parameter (effective stretching modulus); determined by fitting one cycle
- Predicts the stiffening behavior and catenary shape quantitatively
- Valid for strains up to ~15% in wale direction (clamped boundary conditions); model extended to ~100% for free boundary conditions (source: Poincloux_PRX_2018.pdf)

## Lagrangian formulation for inhomogeneous deformations

For non-uniform applied loading, Poincloux PRX 2018 derives a Lagrangian:

$$\mathcal{L}(\vec{c}, \vec{w}) = \tilde{Y} \iint_{x,y} dxdy \left(\frac{1}{c} + \frac{\beta}{w}\right) + \alpha \iint_{x,y} dxdy\,(c + \delta w) - \iint_{x,y} dxdy\, \mathcal{T}(x,y) \cdot \partial_y \vec{w} - \iint_{x,y} dxdy\, \mathcal{T}(x) \vec{e}_z \cdot \vec{w}$$

where $\vec{c}$ and $\vec{w}$ are vector fields encoding stitch deformation. Minimizing yields Euler-Lagrange equations predicting the full displacement field, which matches experiment up to ~$\varepsilon = 15\%$ (source: Poincloux_PRX_2018.pdf).

## Finite element analysis (FEA) application

The constitutive model from Singal 2024 was implemented in FEA (2D elastic sheet with appropriate boundary conditions) and applied to predict:
- Non-affine displacement fields under uniaxial loading
- Deformation of a therapeutic glove

FEA predictions match DIC measurements quantitatively, including the non-affine deformation near free corners (source: Singal_NatureComm_2024.pdf).

## Hysteresis

In reality, the loading and unloading stress-strain curves differ. The effective stretching modulus is larger during loading ($\tilde{Y}^\uparrow$) than unloading ($\tilde{Y}^\downarrow$) due to friction at yarn contacts — a factor of ~5× for stockinette nylon (source: Poincloux_PRX_2018.pdf). For the full treatment of hysteresis and memory, see [[return-point-memory]].

## Rod constitutive equations (Cosserat/Kirchhoff rods)

For a 1D elastic rod, the constitutive equations relate the three **resultants** $(N, H, M)$ — tension, shear force, bending couple — to the three **strain variables** $(\nu, \eta, \mu)$ — stretch, shear, bending (source: Nonlinear_Problems_of_Elasticity.pdf §4.1):

$$N = \hat{N}(\nu,\eta,\mu,s), \quad H = \hat{H}(\nu,\eta,\mu,s), \quad M = \hat{M}(\nu,\eta,\mu,s).$$

The **monotonicity condition** requires the Jacobian $\partial(\hat{N},\hat{H},\hat{M})/\partial(\nu,\eta,\mu)$ to be positive-definite — the rod-mechanics analog of positive-definiteness of the elasticity tensor. For a **hyperelastic** rod, a stored-energy function $W(\nu,\eta,\mu,s)$ exists with $\hat{N} = W_\nu$, $\hat{H} = W_\eta$, $\hat{M} = W_\mu$.

The **elastica** (Bernoulli-Euler) is the classical special case with $\nu = 1$, $\eta = 0$, and $M = (EI)[\mu - \mu^\circ]$ — the bending couple linear in curvature change. This is the constitutive law used in Kirchhoff rod simulations of yarn (see [[kirchhoff-rod]], [[cosserat-rod]]).

## Tensor mechanics background

The models above are phenomenological or first-principles in the knitting sense, but they sit within the broader continuum mechanics framework of [[likharev-chap7]]. The general isotropic Hooke's law:

$$\sigma_{jj'} = 2\mu\!\left(s_{jj'} - \tfrac{1}{3}\delta_{jj'}\,\text{Tr}(\mathbf{s})\right) + 3K\!\left(\tfrac{1}{3}\delta_{jj'}\,\text{Tr}(\mathbf{s})\right)$$

does **not** apply directly to knitted fabrics because:
1. Fabrics are anisotropic (different E and ν along wale vs. course — see [[wale-and-course]])
2. The strain–stress relation is nonlinear and history-dependent (non-Hookean) — see [[hookes-law]]

The fabric constitutive model is therefore a **structural** (not material) relation derived from the topology and geometry of the stitch network. See [[stitch-topology]] and [[knit-elasticity]].

## Related pages

- [[knit-elasticity]]
- [[stitch-topology]]
- [[stitch-types]]
- [[yarn]]
- [[return-point-memory]]
- [[singal-naturecomm-2024]]
- [[poincloux-prx-2018]]
- [[hookes-law]]
- [[likharev-chap7]]
- [[witten-2007]]
- [[cosserat-rod]]
- [[kirchhoff-rod]]
- [[antman-chap4]]
