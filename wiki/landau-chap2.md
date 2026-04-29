# Landau & Lifshitz — Theory of Elasticity, Chapter II

**Summary**: Chapter II of Landau & Lifshitz derives the equilibrium theory of thin plates and rods from first principles: the biharmonic plate equation, Föppl–von Kármán equations for large deflections, shell mechanics, and the bending/torsion theory of slender rods. The rod results are directly used in yarn simulation frameworks.

**Sources**: `raw/Landau and Lifshitz - Theory of Elasticity.pdf` (Chapter II, §11–§21, book pages 38–86)

**Last updated**: 2026-04-17

---

## §11 — Energy of a bent plate

For a thin plate of thickness $h$, the mid-plane (neutral surface) undergoes no stretching for small deflections. The transverse displacement $\zeta(x,y)$ induces a strain tensor that varies linearly with depth $z$ from the neutral surface:

$$u_{xx} = -z\frac{\partial^2\zeta}{\partial x^2}, \quad u_{yy} = -z\frac{\partial^2\zeta}{\partial y^2}, \quad u_{xy} = -z\frac{\partial^2\zeta}{\partial x\,\partial y}.$$

Integrating the elastic free energy through the thickness gives the **bending energy** of the plate:

$$F_\text{pl} = \frac{Eh^3}{24(1-\sigma^2)} \iint \left[ (\triangle\zeta)^2 + 2(1-\sigma)\left\{\left(\frac{\partial^2\zeta}{\partial x\,\partial y}\right)^2 - \frac{\partial^2\zeta}{\partial x^2}\frac{\partial^2\zeta}{\partial y^2}\right\} \right] dx\,dy.$$

The prefactor defines the **flexural rigidity**:

$$D = \frac{Eh^3}{12(1-\sigma^2)}.$$

This is the plate analogue of the rod bending rigidity $EI$. The second term in brackets is a surface divergence (Gauss–Bonnet term) that contributes only through boundary conditions.

## §12 — Equilibrium equation of a plate

Minimising $F_\text{pl}$ subject to an applied transverse pressure $P(x,y)$ per unit area gives the **biharmonic equilibrium equation**:

$$D\,\triangle^2\zeta = P.$$

**Boundary conditions** at an edge:

| Support type | Conditions |
|---|---|
| Clamped | $\zeta = 0$, $\partial\zeta/\partial n = 0$ |
| Simply supported | $\zeta = 0$, $\partial^2\zeta/\partial n^2 + \sigma(\mathrm{d}\theta/\mathrm{d}l)\,\partial\zeta/\partial n = 0$ |
| Free edge | $F = 0$, $M = 0$ |

Reaction force and bending moment at the edge:

$$F = -D\left[\frac{\partial^3\zeta}{\partial n^3} + \frac{\mathrm{d}\theta}{\mathrm{d}l}\frac{\partial^2\zeta}{\partial n^2}\right], \qquad M = D\frac{\partial^2\zeta}{\partial n^2}.$$

## §13 — Longitudinal deformations and the Airy stress function

For in-plane (longitudinal) deformations, the stress components are most efficiently described through the **Airy stress function** $\chi(x,y)$:

$$\sigma_{xx} = \frac{\partial^2\chi}{\partial y^2}, \quad \sigma_{xy} = -\frac{\partial^2\chi}{\partial x\,\partial y}, \quad \sigma_{yy} = \frac{\partial^2\chi}{\partial x^2}.$$

These identically satisfy the in-plane equilibrium equations $\partial\sigma_{\alpha\beta}/\partial x_\beta = 0$. Compatibility then requires:

$$\triangle^2\chi = 0 \quad \text{(biharmonic)}.$$

Key result from §13 (Problem 5): a circular hole of radius $R$ in a plate under uniform tension $T$ produces a **stress concentration factor of 3** at the hole equator — $\sigma_{\phi\phi} = 3T$ at $\phi = \pm\pi/2$ — a classical result in fracture mechanics.

## §14 — Large deflections: Föppl–von Kármán equations

For deflections $\zeta \gtrsim h$, the plate stretches as it bends; there is no longer a neutral surface. The two-dimensional strain tensor picks up a geometric (nonlinear) term:

$$u_{\alpha\beta} = \frac{1}{2}\left(\frac{\partial u_\alpha}{\partial x_\beta} + \frac{\partial u_\beta}{\partial x_\alpha}\right) + \frac{1}{2}\frac{\partial\zeta}{\partial x_\alpha}\frac{\partial\zeta}{\partial x_\beta}.$$

The total free energy is $F_\text{pl} = \int\{\Psi_1(\zeta) + \Psi_2(u_{\alpha\beta})\}\,\mathrm{d}f$, and variation gives the coupled **Föppl–von Kármán equations** (Föppl 1907):

$$D\,\triangle^2\zeta - h\left(\frac{\partial^2\chi}{\partial y^2}\frac{\partial^2\zeta}{\partial x^2} + \frac{\partial^2\chi}{\partial x^2}\frac{\partial^2\zeta}{\partial y^2} - 2\frac{\partial^2\chi}{\partial x\,\partial y}\frac{\partial^2\zeta}{\partial x\,\partial y}\right) = P, \tag{14.6}$$

$$\triangle^2\chi + E\left(\frac{\partial^2\zeta}{\partial x^2}\frac{\partial^2\zeta}{\partial y^2} - \left(\frac{\partial^2\zeta}{\partial x\,\partial y}\right)^2\right) = 0. \tag{14.7}$$

These are nonlinear and cannot be solved exactly in general. Note:
- For $\zeta \ll h$: the nonlinear (stretching) term in (14.6) is negligible → recovers $D\triangle^2\zeta = P$.
- For $\zeta \gg h$: bending term $D\triangle^2\zeta$ is negligible compared to stretching → deflection scales as $\zeta \sim (l^4 P/Eh)^{1/3}$.

**Membrane limit**: when a thin plate (membrane) is under large external tension $T$ with no bending stiffness:

$$T\,\triangle\zeta + P = 0.$$

This is a linear equation. See also [[witten-2007]] where these equations underpin d-cones and ridge mechanics.

## §15 — Deformations of shells

A **shell** is a plate that is curved in its undeformed state. The key difference from flat plates:

- In a flat plate, stretching accompanies bending only as a **second-order effect** (quadratic in $\zeta$).
- In a shell with radius of curvature $R$, a transverse displacement $\zeta$ causes a fractional extension $\sim \zeta/R$ — a **first-order effect**.

Therefore the stretching energy $\sim Eh(\zeta/R)^2$ greatly exceeds the bending energy $\sim Eh^3\zeta^2/R^4$ by a factor $(R/h)^2 \gg 1$. Shells are much stiffer than plates.

**Exceptions** (isometric bending without stretching): a cylindrical shell with open ends can be deformed without stretching; a closed sphere cannot.

**Concentrated force on a spherical shell**: bending is localised to a strip of width $d \sim \sqrt{hR}$ (15.3). Outside this strip the shell is effectively a membrane.

**Shell buckling under external pressure** (spherical shell):

$$p_\text{cr} \sim \frac{Eh^2}{R^2}. \tag{15.8}$$

This is relevant to pressure-loaded shells and to the analogy with fabric loop collapse under compression.

## §16 — Torsion of rods

A rod twisted with torsion angle per unit length $\tau$ has displacements:

$$u_x = -\tau z y, \quad u_y = \tau z x, \quad u_z = \tau\psi(x,y),$$

where $\psi(x,y)$ is the **torsion function**. Introducing the auxiliary function $\chi(x,y)$:

$$\triangle\chi = -1, \quad \chi = 0 \text{ on boundary (singly connected cross-section)}.$$

The **torsional rigidity** is:

$$C = 4\mu\int\chi\,\mathrm{d}A. \tag{16.16}$$

For a **circular cross-section** of radius $R$: $\chi = \frac{1}{2}(R^2 - x^2 - y^2)/2$, giving $C = \tfrac{1}{2}\mu\pi R^4$.

For a **thin rectangular** cross-section (width $d \gg$ thickness $h$): $C = \tfrac{1}{3}\mu d h^3$.

The torsion angle satisfies $\tau = M/C$ (torsion constant × moment = angle per unit length).

Note: the problem of finding $\chi$ is mathematically identical to finding the velocity profile of viscous fluid in a pipe of the same cross-section.

## §17 — Bending of rods

In a bent rod, only the axial stress $\sigma_{zz} = Ex/R$ is nonzero (all other components vanish for a thin rod in pure bending). The neutral surface passes through the **centroid** of the cross-section.

**Bending moment** about the $y$-axis:

$$M_y = \frac{EI_y}{R}, \quad I_y = \int x^2\,\mathrm{d}A \quad \text{(second moment of area)}.$$

For a **circular cross-section** of radius $R$: $I = \tfrac{1}{4}\pi R^4$, so $EI = E\pi R^4/4$.

**Ratio of torsional to bending rigidity** (circular cross-section):

$$\frac{C}{EI} = \frac{\tfrac{1}{2}\mu\pi R^4}{\tfrac{1}{4}E\pi R^4} = \frac{2\mu}{E} = \frac{1}{1+\sigma}.$$

For $\sigma \approx 0.3$: $C/(EI) \approx 0.77$. This justifies the common simulation choice of setting bending and torsion moduli equal (e.g. $B = J = 1.0$ in [[dimitriyev-notes-2019]]).

## §18 — Energy of a deformed rod

Characterise the deformation by the rotation vector $\boldsymbol\Omega = \mathrm{d}\boldsymbol\phi/\mathrm{d}l$ with components $(\Omega_\xi, \Omega_\eta, \Omega_\zeta)$:
- $\Omega_\zeta$: torsion angle per unit length
- $\Omega_\xi, \Omega_\eta$: bending curvatures about the two principal axes

**Elastic free energy of a bent rod**:

$$F_\text{rod} = \int\left\{\tfrac{1}{2}EI_1\Omega_\xi^2 + \tfrac{1}{2}EI_2\Omega_\eta^2 + \tfrac{1}{2}C\Omega_\zeta^2\right\}\mathrm{d}l. \tag{18.5}$$

Moments: $M_\xi = EI_1\Omega_\xi$, $M_\eta = EI_2\Omega_\eta$, $M_\zeta = C\Omega_\zeta$.

For a **slightly bent rod** (small departure from a reference curve with curvature $1/R_0$):

$$F_\text{rod} = \tfrac{1}{2}EI\int\left(\frac{1}{R} - \frac{1}{R_0}\right)^2\mathrm{d}z. \tag{18.11}$$

This is exactly the bending energy integrand used in [[yarn-simulation]] (Dimitriyev, Singal, Kaldor frameworks).

## §19 — Equations of equilibrium of rods

Vector equilibrium for a bent rod with internal force $\mathbf{F}$ and moment $\mathbf{M}$:

$$\frac{\mathrm{d}\mathbf{F}}{\mathrm{d}l} = -\mathbf{K}, \qquad \frac{\mathrm{d}\mathbf{M}}{\mathrm{d}l} = \mathbf{F}\times\mathbf{t}. \tag{19.2–19.3}$$

For concentrated external forces only (no distributed load, $\mathbf{K}=0$): $\mathbf{F}$ = constant between force application points.

**Boundary conditions**:

| End condition | Constraints |
|---|---|
| Clamped | Position and tangent direction fixed |
| Free end | $\mathbf{F} = 0$, $\mathbf{M} = 0$ |
| Hinged | Position fixed, moment $M_\zeta = 0$ |
| Supported | Transverse displacement fixed, $M = 0$, F perpendicular to rod |

For a rod with **circular cross-section** and no applied twisting moment: torsion is absent everywhere ($\Omega_\zeta = 0$). The pure-bending equation is:

$$EI\frac{\mathrm{d}\mathbf{r}}{\mathrm{d}l}\times\frac{\mathrm{d}^3\mathbf{r}}{\mathrm{d}l^3} = \mathbf{F}\times\frac{\mathrm{d}\mathbf{r}}{\mathrm{d}l}. \tag{19.10}$$

## §20 — Small deflections of rods

For small transverse deflections $X(z)$, $Y(z)$ about the $z$-axis:

$$EI_2\,X^{(iv)} = K_x, \qquad EI_1\,Y^{(iv)} = K_y. \tag{20.4}$$

This is the standard **Euler–Bernoulli beam equation**. Shearing force: $F_x = -EI_2 X'''$.

The **flexural rigidities** $EI_1$ and $EI_2$ determine the bending resistance in the two principal planes; the rod bends preferentially in the direction of lower flexural rigidity.

**Rod under combined bending and axial tension/compression** $T$ (longitudinal force):

$$EI_2\,X^{(iv)} - T\,X'' = K_x. \tag{20.14}$$

This is the stretched-beam (or "elastica under tension") equation. In knitting contexts, it is the governing equation for a yarn segment under pre-tension — explaining why pre-tension stiffens the fabric (see [[ding-2023]]).

- For strong tension ($T$ large, $EI$ small): string limit $TX'' + K = 0$.
- For rigid rod ($EI$ large, $T$ small): beam limit $EI\,\zeta^{(iv)} = K$.

Selected solutions:
- Cantilever (one end clamped, free end force $f$): $\zeta(l) = fl^3/3EI$
- Both ends clamped, central force $f$: $\zeta(\tfrac{1}{2}l) = fl^3/192EI$
- Both ends simply supported, central force $f$: $\zeta(\tfrac{1}{2}l) = fl^3/48EI$

## §21 — Stability of elastic systems (Euler buckling)

A rod under longitudinal compressive force $T$ (here $T < 0$) has a **critical load** $T_\text{cr}$ above which the straight configuration becomes unstable and the rod buckles. The critical load is found from the bifurcation condition (nontrivial solutions of the equilibrium equation):

$$EI\,X^{(iv)} + |T|\,X'' = 0.$$

**Euler buckling loads** for a rod of length $l$:

| Boundary conditions | $T_\text{cr}$ |
|---|---|
| Both ends hinged | $\pi^2 EI/l^2$ |
| Both ends clamped | $4\pi^2 EI/l^2$ |
| Clamped + free (cantilever) | $\pi^2 EI/4l^2$ |

**Critical torsion** (clamped ends): $\tau_\text{cr} \approx 8.98\,EI/Cl$.

**Self-weight buckling** of a vertical rod clamped at the base: $l_\text{cr} = 1.98(EI_2/q)^{1/3}$, where $q$ is the weight per unit length.

Physical significance for knitting: yarn loops and free segments can buckle if compressed; the loop geometry constrains the effective length $l$ and thus sets the compressive load at which a knitted stitch deforms irreversibly.

## Connections to knitting mechanics

| L&L result | Knitting application |
|---|---|
| Rod bending rigidity $EI = E\pi R^4/4$ | Yarn bending energy in [[yarn-simulation]] |
| Torsional rigidity $C = \tfrac{1}{2}\mu\pi R^4$; $C/EI = 1/(1+\sigma)$ | Justification for $B = J$ in Dimitriyev/Singal simulations |
| Energy $F = \tfrac{1}{2}EI\int\kappa^2\,\mathrm{d}l$ | Euler–Bernoulli bending used in all three simulation frameworks |
| Stretched-beam equation (20.14) | Pre-tension changes effective stiffness (Ding 2023) |
| Plate biharmonic $D\triangle^2\zeta = P$ | Continuum model of fabric as a thin plate |
| Föppl–von Kármán (large deflections) | Used in [[witten-2007]]; relevant for fabric crumpling and d-cones |
| Shell mechanics; $p_\text{cr} \sim Eh^2/R^2$ | Shaped knitwear under compression; loop collapse |
| Euler buckling | Yarn compression in stitches; loop instability |

## Related pages

- [[kirchhoff-rod]]
- [[coleman-1993]]
- [[yarn-simulation]]
- [[yarn]]
- [[yarn-contact]]
- [[knit-elasticity]]
- [[constitutive-model]]
- [[hookes-law]]
- [[likharev-chap7]]
- [[witten-2007]]
- [[dimitriyev-notes-2019]]
- [[singal-naturecomm-2024]]
- [[ding-2023]]
