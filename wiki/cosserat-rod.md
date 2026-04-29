# Cosserat Rod

**Summary**: The special Cosserat theory of rods is a geometrically exact 1D model for slender elastic bodies that allows stretch, shear, and bending without ad hoc approximations, strictly generalizing the Kirchhoff and Euler-Bernoulli models.

**Sources**: `raw/Nonlinear_Problems_of_Elasticity.pdf`

**Last updated**: 2026-04-21

---

## What is a Cosserat rod?

A **special Cosserat rod** describes a slender body by two vector-valued functions of the arc-length parameter $s$:

- $\boldsymbol{r}(s)$: position of the base curve (centroid curve)
- $\boldsymbol{b}(s)$: unit **director** vector, encoding the average orientation of the cross-section

The theory is called *special* because it uses a single director per cross-section rather than a full director frame (the "general" Cosserat rod uses two directors). It is called *exact* because no geometric approximations are made — large deflections, large rotations, and finite strains are all admissible. (source: Antman 2005, Chap. 4 intro)

In 2D (planar case), the director is characterized by a single angle $\theta(s)$:

$$\boldsymbol{a} = \cos\theta\,\boldsymbol{i} + \sin\theta\,\boldsymbol{j}, \qquad \boldsymbol{b} = -\sin\theta\,\boldsymbol{i} + \cos\theta\,\boldsymbol{j}.$$

The tangent vector decomposes as $\boldsymbol{r}' = \nu\boldsymbol{a} + \eta\boldsymbol{b}$.

## Strain variables

| Symbol | Name | Definition | Physical meaning |
|---|---|---|---|
| $\nu$ | stretch | $\boldsymbol{r}'\cdot\boldsymbol{a}$ | Local ratio of deformed to reference length; reduces to $|\boldsymbol{r}'|$ for zero shear |
| $\eta$ | shear strain | $\boldsymbol{r}'\cdot\boldsymbol{b}$ | Reduction of right angle between $\boldsymbol{r}^\circ_\circ$ and $\boldsymbol{b}^\circ$; $\approx \sin\beta$ where $\beta$ is shear angle |
| $\mu = \theta'$ | bending strain | $d\theta/ds$ | Rate of rotation of director; the curvature of the director field (not the curve) |

Note that $\mu = \theta'$ isolates pure bending from stretching-induced curvature changes — a key advantage over using the geometric curvature of $\boldsymbol{r}$.

## Constitutive equations

The rod is **elastic** if forces and couple are functions of the strains:

$$N = \hat{N}(\nu,\eta,\mu,s), \quad H = \hat{H}(\nu,\eta,\mu,s), \quad M = \hat{M}(\nu,\eta,\mu,s).$$

Required properties (source: Antman 2005, §4.1):

- **Monotonicity**: $\partial(\hat{N},\hat{H},\hat{M})/\partial(\nu,\eta,\mu)$ positive-definite — strains and resultants covary monotonically
- **Growth conditions**: resultants diverge to $\pm\infty$ as strains approach their physical limits
- **Symmetry**: even/odd parity conditions ensuring no directional bias in shear or bending
- **Natural state**: $\hat{N} = 0$, $\hat{M} = 0$ in the reference configuration

For a **hyperelastic** rod, a stored-energy function $W(\nu,\eta,\mu,s)$ exists with $\hat{N} = W_\nu$, $\hat{H} = W_\eta$, $\hat{M} = W_\mu$.

## Equilibrium equations (planar)

$$N' - \mu H + f_a = 0$$
$$H' + \mu N + f_b = 0$$
$$M' + \nu H - \eta N + l = 0$$

where $f_a, f_b$ are components of the distributed body force and $l$ is the body couple per unit reference length. The first two equations follow from $\boldsymbol{n}' + \boldsymbol{f} = \boldsymbol{o}$; the third from the moment balance $M' + \boldsymbol{r}'\times\boldsymbol{n} + l\boldsymbol{k} = \boldsymbol{o}$.

## Relationship to simpler models

The Cosserat rod is the most general model; all others are special cases obtained by imposing constraints:

| Model | Constraint | $\nu$ | $\eta$ | Constitutive for $M$ |
|---|---|---|---|---|
| **Cosserat rod** | none | free | free | $\hat{M}(\nu,\eta,\mu,s)$ — nonlinear |
| Timoshenko beam | small deflections linearization | $\approx 1$ | small | linear in $\mu$ |
| **Kirchhoff rod** | inextensible + unshearable | $= 1$ | $= 0$ | $\hat{M}(\mu,s)$; $N,H$ Lagrange multipliers |
| Euler-Bernoulli | Kirchhoff + linearized | $= 1$ | $= 0$ | $M = EI\mu$ |
| Elastica | Kirchhoff + $M = EI\mu$ (nonlinear) | $= 1$ | $= 0$ | $M = (EI)\mu$ |

See [[kirchhoff-rod]] for the Kirchhoff model in 3D.

## Why it matters for yarn mechanics

Yarns are not perfectly inextensible or unshearable — cross-section deformation, inter-fiber sliding, and compressibility all matter. The Cosserat framework:

1. Provides the **first-principles basis** for constitutive equations beyond Kirchhoff
2. Makes clear which constraints (ν=1, η=0) introduce Lagrange multipliers vs. genuine constitutive response
3. Enables analysis of **shear instabilities** — new equilibrium branches that do not exist in the inextensible-unshearable theory (Fig. 2.14c in [[antman-chap4]])
4. Is the foundation for the full 3D rod theory in Antman Chapter 8, which Coleman et al. (1993) build on (see [[coleman-1993]])

## Related pages

- [[kirchhoff-rod]]
- [[antman-chap4]]
- [[coleman-1993]]
- [[constitutive-model]]
- [[yarn]]
- [[yarn-simulation]]
- [[landau-chap2]]
