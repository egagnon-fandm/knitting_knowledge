# Coleman et al. 1993 — Dynamics of Rods in the Theory of Kirchhoff and Clebsch

**Summary**: Coleman, Dill, Lembo, Lu & Tobias extend the Kirchhoff-Clebsch rod theory from planar pure-flexure to full 3D motions with bending, torsion, and twist. Key results include constitutive equations for naturally prismatic rods, five conservation laws including a new twist impulse, and explicit solitary-wave solutions whose localized curvature profile directly models a crease.

**Sources**: `raw/Coleman et al. - 1993 - On the dynamics of rods in the theory of Kirchhoff.pdf`

**Last updated**: 2026-04-20

---

## Setting

The paper works within the **Kirchhoff-Clebsch theory** of thin elastic rods: inextensible, dynamically symmetric (equal principal moments of inertia $I$), naturally prismatic (stress-free reference configuration $\kappa^u = 0$). It is a first-order theory, accurate to $O(\alpha^2)$ where $\alpha = \max\{|\kappa|h, h/L\}$.

The rod is described by:
- Axial curve $\mathscr{C}(t)$ with arc-length parameter $s$
- An orthonormal director triad $(d_1(s,t),\, d_2(s,t),\, d_3(s,t))$ with $d_3 = x'(s,t)$ tangent to the axis

## Kinematics

The **curvature vector** $\kappa(s,t)$ is defined by:

$$d_i' = \kappa \times d_i \quad (i = 1,2,3), \tag{2.4}$$

with components $(\kappa_1, \kappa_2, \kappa_3)$ in the basis $(d_1, d_2, d_3)$:
- $\kappa_1, \kappa_2$: bending curvature components
- $\kappa_3$: twist density

The **spin vector** $\omega(s,t)$ satisfies $\dot{d}_i = \omega \times d_i$, and the **compatibility relation** is:

$$\dot{\kappa} - \omega' = \omega \times \kappa. \tag{2.10}$$

Geometric curvature $k$ and torsion $\tau$ of the axial curve relate to the $\kappa_i$ and Euler angles via (3.11), (3.16):

$$k^2 = (\theta_{,s})^2 + (\psi_{,s})^2\sin^2\theta, \qquad \tau = \big[(\theta_{,s}\psi_{,ss} - \theta_{,ss}\psi_{,s})\sin\theta + ((\theta_{,s})^2 + k^2)\psi_{,s}\cos\theta\big]k^{-2}.$$

## Constitutive equations

For a naturally prismatic rod with dynamically symmetric cross-sections, the bending and twisting moments are:

$$M_1 = EI\kappa_1, \quad M_2 = EI\kappa_2, \quad M_3 = \mu J\kappa_3. \tag{2.25}$$

The dimensionless ratio of torsional to bending rigidity is:

$$\Omega = \frac{\mu J}{EI}. \tag{2.29}$$

For **circular cross-sections**: $J = 2I$ and $\Omega = 2\mu/E = (1+\nu)^{-1}$ — matching the result in [[landau-chap2]] §17.

## Dynamical equations

The six equations (3.7)–(3.8) govern $(F^x, F^y, F^z, \psi, \theta, \phi)$ — three Euler angles and three force components. For the planar case ($\psi = 0$, $\phi = 0$, $F^y = 0$) they reduce exactly to the classical system (1.2) of pure flexure.

## Conservation laws

For smooth solutions with pseudo-periodic boundary conditions, five quantities are conserved:

| Invariant | Expression |
|---|---|
| Energy $\mathscr{H}$ | $2\mathscr{H} = \int_0^L (M\cdot\kappa + \dot{x}\cdot\dot{x} + d_1\cdot\dot{d}_1 + d_2\cdot\dot{d}_2)\,ds$ |
| Momentum $\mathscr{M}$ | $\int_0^L \dot{x}\,ds$ |
| Angular momentum $\mathscr{L}$ | (3.31a) |
| Linear impulse $\mathscr{J}$ | $\int_0^L (\dot{x}\cdot\dot{x} + d_1\cdot\dot{d}_1' + d_2\cdot\dot{d}_2')\,ds$ |
| **Twist impulse** $\mathscr{W}$ | $\int_0^L \omega_3\,ds$ **(new — absent in planar theory)** |

The energy integrand expands as $M\cdot\kappa = \kappa_1^2 + \kappa_2^2 + \Omega\kappa_3^2$, i.e., the sum of squared bending and twist components weighted by their respective rigidities.

## Traveling waves and the torsion-curvature relation

For a traveling wave with speed $c$ ($\xi = s - ct$), the dynamical equations reduce. Coleman, Lu & Tobias [15] prove that:

1. **Torsion-curvature relation**: $[\tau^0 - \tau(\xi)]\,k^2(\xi) = N$ (constant). Near a crease where $k$ is large, the torsion $\tau$ is pulled toward $\tau^0$.

2. **Tension-curvature**: $F\cdot d_3 + \tfrac{1}{2}(1-c^2)k^2 = b$ (constant).

3. **Curvature ODE**:

$$k'' + \tfrac{1}{2}k^3 + [(\tau^0)^2 + C]k - \frac{N^2}{k^3} = 0 \tag{4.9}$$

where $C = (b - c^2)/(1-c^2)$. Solutions are expressible in terms of elliptic functions (Jacobi cn).

## Solitary waves — localized crease

A **solitary wave** has $k(\xi) \to 0$ as $|\xi| \to \infty$. This requires $N = 0$ (from (4.11c)) and torsion constant $\tau = \tau^0$. The curvature profile is:

$$k(\xi) = \frac{2}{\nu}\operatorname{sech}\!\left(\frac{\xi - s_0}{\nu}\right), \quad \nu = \left[C - (\tau^0)^2\right]^{-1/2}. \tag{4.14--4.15}$$

The axial curve in cylindrical coordinates $(r, \Phi, z)$:

$$r = 2a\operatorname{sech}\!\left(\tfrac{\xi-s_0}{\nu}\right), \quad \Phi = (\xi - s_0)\tau^0 + \delta, \quad z = s - 2a\tanh\!\left(\tfrac{\xi-s_0}{\nu}\right), \tag{4.16}$$

where $a = \nu[1 - \nu^2(\tau^0)^2C^{-1}]^{1/2}/(1 + \nu^2(\tau^0)^2)$.

The **bending energy density** near the crease is:

$$\tfrac{1}{2}EI\,k^2 \propto \operatorname{sech}^2\!\left(\tfrac{\xi - s_0}{\nu}\right),$$

which is localized around $s_0$ with half-width $\nu$. The total energy of one solitary wave (crease) is finite and scales as $EI/\nu$.

**Positive vs. negative solitary waves**: when $a > 0$, $d_3$ rotates counterclockwise along the loop (positive wave); when $a < 0$, clockwise (negative wave). For $\tau^0 = 0$ (pure flexure) these reduce to the planar Coleman-Dill solutions.

## Connections to knitting mechanics

| Result | Application |
|---|---|
| Constitutive eqs. (2.25); $\Omega = (1+\nu)^{-1}$ | Justifies $B = J$ in [[yarn-simulation]] (Dimitriyev/Singal) |
| Inextensibility assumption | Standard in all yarn simulation frameworks |
| Energy integrand $\tfrac{1}{2}EI\int\kappa^2\,dl$ | Euler-Bernoulli bending used in [[yarn-simulation]] |
| Solitary wave $k \sim \operatorname{sech}$ | Model for localized curvature bump / crease in a yarn loop |
| Torsion-curvature coupling | Relevant at yarn cross-overs where bending and twist interact |

## Related pages

- [[kirchhoff-rod]]
- [[landau-chap2]]
- [[yarn-simulation]]
- [[yarn]]
- [[yarn-contact]]
- [[dimitriyev-notes-2019]]
