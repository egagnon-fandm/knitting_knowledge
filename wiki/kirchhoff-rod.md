# Kirchhoff Rod

**Summary**: The Kirchhoff rod model describes a slender elastic rod as an inextensible curve with an attached director frame. It captures bending and torsion through a curvature vector, and is the theoretical foundation for all yarn simulation frameworks in the knitting mechanics literature.

**Sources**: `raw/Coleman et al. - 1993 - On the dynamics of rods in the theory of Kirchhoff.pdf`, `raw/Landau and Lifshitz - Theory of Elasticity.pdf`

**Last updated**: 2026-04-21

---

## Core assumptions

1. **Inextensibility**: arc-length $s$ is a material coordinate — the rod does not stretch.
2. **Slenderness**: cross-section size $h \ll$ length $L$; theory is first-order in $\alpha = \max\{|\kappa|h,\, h/L\}$.
3. **Dynamic symmetry**: the two principal moments of inertia of the cross-section are equal ($I_1 = I_2 = I$).
4. **Natural prismaticity**: the reference (stress-free) curvature $\kappa^u = 0$.

## Kinematics

At each point $s$ along the rod, an orthonormal **director triad** $(d_1, d_2, d_3)$ is attached with $d_3 = dx/ds$ tangent to the axial curve. The triad evolves along the rod according to:

$$d_i' = \kappa \times d_i, \qquad \dot{d}_i = \omega \times d_i,$$

where $\kappa(s,t)$ is the **curvature vector** and $\omega(s,t)$ is the **spin vector**. In components relative to $(d_1, d_2, d_3)$:

- $\kappa_1, \kappa_2$: bending curvature components (flexure in the two cross-section planes)
- $\kappa_3$: twist density (torsion of the director frame about the axis)

The geometric curvature and torsion of the axial curve are related to $\kappa_i$ and the Euler angles $(\psi, \theta, \phi)$ by (source: coleman-1993):

$$k^2 = \kappa_1^2 + \kappa_2^2, \qquad \tau = \kappa_3 + \zeta_{,s},$$

where $\zeta$ is the angle from the Frenet normal to $d_1$.

The compatibility relation linking spatial and temporal changes is:

$$\dot{\kappa} - \omega' = \omega \times \kappa.$$

## Constitutive equations

For a naturally prismatic rod made of a homogeneous isotropic elastic material, the bending and twisting moments are linear in the curvature components (source: coleman-1993, landau-chap2 §17–18):

$$M_1 = EI\kappa_1, \quad M_2 = EI\kappa_2, \quad M_3 = \mu J\kappa_3.$$

Here $EI$ is the **bending rigidity** and $\mu J$ is the **torsional rigidity**. For a circular cross-section of radius $R$:

$$EI = \tfrac{1}{4}E\pi R^4, \qquad \mu J = \tfrac{1}{2}\mu\pi R^4, \qquad \frac{\mu J}{EI} = \frac{2\mu}{E} = \frac{1}{1+\nu}.$$

This ratio $\Omega = (1+\nu)^{-1} \approx 0.77$ for $\nu \approx 0.3$ justifies the common simulation choice of equal bending and torsion moduli ($B = J$).

## Elastic energy

The total elastic energy of a deformed rod is:

$$F_\text{rod} = \frac{1}{2}\int_0^L \left[EI(\kappa_1^2 + \kappa_2^2) + \mu J\kappa_3^2\right] dl. \tag{L\&L 18.5}$$

For small departures from a reference shape with curvature $\kappa_0$:

$$F_\text{rod} = \frac{1}{2}EI\int_0^L \left(\kappa - \kappa_0\right)^2 dl. \tag{L\&L 18.11}$$

This is the bending energy used in all three yarn simulation frameworks ([[yarn-simulation]]).

## Equilibrium equations

The balance of linear and angular momentum for a rod segment gives:

$$F' = -K, \qquad M' + d_3 \times F = 0,$$

where $F(s)$ is the resultant force and $K$ the distributed body force per unit length. This is the static limit of the full dynamical system (source: landau-chap2 §19).

## Relationship to other rod models

| Model | Extensible? | Shear? | Scope |
|---|---|---|---|
| **Kirchhoff rod** | No | No | Thin rods, large rotations |
| Euler-Bernoulli beam | No | No | Small deflections (linearized Kirchhoff) |
| Timoshenko beam | No | Yes | Thick rods (shear significant) |
| Cosserat rod | Yes | Yes | Most general; first-principles |

Kirchhoff rods are the standard model in yarn mechanics because yarns are nearly inextensible and slender.

The Kirchhoff rod is the inextensible, unshearable special case of the **special Cosserat rod** (Antman 2005, Chap. 4). In the Cosserat framework, $\nu = 1$ and $\eta = 0$ are imposed as constraints, making $N$ (tension) and $H$ (shear force) Lagrange multipliers rather than constitutively determined quantities. The Cosserat model additionally defines a **bending strain** $\mu = \theta'$ that isolates bending from stretching-induced curvature — an advantage when stretch is non-negligible. See [[cosserat-rod]] for the full Cosserat theory and [[antman-chap4]] for the planar equilibrium analysis.

## Solitary wave (crease) solution

For a **traveling wave** ($\xi = s - ct$) on a naturally prismatic rod, the curvature obeys a nonlinear ODE (4.9 in [[coleman-1993]]). The **solitary wave** solution — localized curvature bump with $k \to 0$ at infinity — is:

$$k(\xi) = \frac{2}{\nu}\operatorname{sech}\!\left(\frac{\xi - s_0}{\nu}\right),$$

with width $\nu = [C - (\tau^0)^2]^{-1/2}$ set by the background tension and torsion. This is a smooth model for a **crease**: the bending energy density $\tfrac{1}{2}EIk^2 \propto \operatorname{sech}^2$ is localized around $s_0$. A sharper crease corresponds to smaller $\nu$.

## Related pages

- [[cosserat-rod]]
- [[antman-chap4]]
- [[coleman-1993]]
- [[landau-chap2]]
- [[yarn-simulation]]
- [[yarn]]
- [[hookes-law]]
- [[likharev-chap7]]
