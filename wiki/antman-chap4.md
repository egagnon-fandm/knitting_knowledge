# Antman — Nonlinear Problems of Elasticity, Chapter 4

**Summary**: Chapter 4 of Antman (2005) develops the special Cosserat theory of rods for planar deformations and applies it to equilibrium problems, including buckling of straight rods and ring inflation under pressure.

**Sources**: `raw/Nonlinear_Problems_of_Elasticity.pdf`

**Last updated**: 2026-04-21

---

## Chapter overview

Chapter 4 ("Planar Steady-State Problems for Elastic Rods") formulates and analyzes equilibrium problems for the planar deformation of elastic rods using the **special Cosserat theory of rods** — an intrinsically 1-dimensional, geometrically exact theory that is more general than standard structural mechanics models (Kirchhoff, Timoshenko, Euler-Bernoulli). It does not rely on ad hoc geometrical approximations.

Sections 1 and 2 are ingested here. Sections 3–6 cover rings under hydrostatic pressure, asymptotic shape of inflated rings, whirling rods, and simultaneous whirling/breathing oscillations.

---

## Section 1: Formulation of the Governing Equations (pp. 95–105)

### Geometry of deformation

A **planar Cosserat rod** is defined by two functions of the arc-length parameter $s \in [s_1, s_2]$:

$$[s_1, s_2] \ni s \mapsto \boldsymbol{r}(s), \quad \boldsymbol{b}(s) \in \operatorname{span}\{\boldsymbol{i}, \boldsymbol{j}\}$$

where $\boldsymbol{b}(s)$ is the **director** — a unit vector encoding the average orientation of the cross-section. The complementary vector $\boldsymbol{a} = -\boldsymbol{k} \times \boldsymbol{b}$ completes the frame:

$$\boldsymbol{a} = \cos\theta\,\boldsymbol{i} + \sin\theta\,\boldsymbol{j}, \qquad \boldsymbol{b} = -\sin\theta\,\boldsymbol{i} + \cos\theta\,\boldsymbol{j}.$$

The tangent vector is decomposed as $\boldsymbol{r}' = \nu\boldsymbol{a} + \eta\boldsymbol{b}$, giving the three **strain variables**:

| Symbol | Name | Physical meaning |
|---|---|---|
| $\nu$ | stretch | local ratio of deformed to reference arc-length (in the $\boldsymbol{a}$ direction) |
| $\eta$ | shear strain | projection of $\boldsymbol{r}'$ onto the director $\boldsymbol{b}$; proportional to $\sin\beta$ where $\beta$ is the shear angle |
| $\mu = \theta'$ | bending strain | rate of change of director angle; plays the role of curvature |

The non-interpenetration requirement is $\nu > 0$; a more restrictive condition is $\nu > V(\theta', s)$ for a convex function $V$ with $V(0,s) = 0$ (source: Nonlinear_Problems_of_Elasticity.pdf §1.8–1.9).

### Equations of equilibrium

For a material segment $[c, s]$, the resultant contact force $\boldsymbol{n}^+(s)$ and contact couple $\boldsymbol{m}^+(s) = M(s)\boldsymbol{k}$ must balance applied body forces $\boldsymbol{f}(s)$ (per unit reference length) and body couples $l(s)\boldsymbol{k}$. Differentiating the integral balance laws gives the differential equilibrium equations:

$$\boldsymbol{n}' + \boldsymbol{f} = \boldsymbol{o} \tag{1.15}$$
$$M' + \boldsymbol{r}' \times \boldsymbol{n} + l\boldsymbol{k} = \boldsymbol{o} \tag{1.17 reduced}$$

In the planar frame $\boldsymbol{n} = N\boldsymbol{a} + H\boldsymbol{b}$, these become the component equations:

$$N' - \mu H + \boldsymbol{f}\cdot\boldsymbol{a} = 0, \quad H' + \mu N + \boldsymbol{f}\cdot\boldsymbol{b} = 0, \quad M' + \nu H - \eta N + l = 0. \tag{1.20}$$

Here $N$ is the **tension**, $H$ is the **shear force**, and $M$ is the **bending couple** (or moment).

### Constitutive equations

The rod is **elastic** if there exist constitutive functions $\hat{N}, \hat{H}, \hat{M}$ such that:

$$N(s) = \hat{N}(\nu, \eta, \mu, s), \quad H(s) = \hat{H}(\nu, \eta, \mu, s), \quad M(s) = \hat{M}(\nu, \eta, \mu, s). \tag{1.21}$$

Physical requirements on these functions:

1. **Monotonicity condition**: the matrix $\partial(\hat{N}, \hat{H}, \hat{M})/\partial(\nu, \eta, \mu)$ is positive-definite. This ensures the rod resists increases in each strain with corresponding increases in resultant (source: Nonlinear_Problems_of_Elasticity.pdf §1.23).

2. **Growth conditions**: $\hat{N} \to +\infty$ as $\nu \to +\infty$, $\hat{N} \to -\infty$ as $\nu \to V(\mu,s)$; $\hat{H} \to \pm\infty$ as $\eta \to \pm\infty$; $\hat{M} \to \pm\infty$ as $\mu \to \sup/\inf$.

3. **Symmetry**: $\hat{\nu}$ even in $H$ and $M$; $\hat{\eta}$ odd in $H$, even in $M$; $\hat{\mu}$ even in $H$, odd in $M$ — it is no harder to shear or bend the rod in one direction than the other (source: §1.27).

4. **Reference configuration**: $\hat{N}(1, 0, \mu^\circ, s) = 0$ and $\hat{M}(1, 0, \mu^\circ, s) = 0$ — forces vanish in the natural state.

The constitutive system is invertible (by an implicit function theorem using the monotonicity condition), giving the dual form $\nu = \hat{\nu}(N, H, M, s)$, etc. (source: §1.29).

### Hyperelastic rods and stored energy

If the constitutive matrix is symmetric, a **stored-energy function** $W(\nu, \eta, \mu, s)$ exists with:

$$\hat{N} = W_\nu, \quad \hat{H} = W_\eta, \quad \hat{M} = W_\mu. \tag{1.33a}$$

The Legendre transform $W^*(N, H, M, s)$ is the **conjugate stored-energy function** with $\hat{\nu} = W^*_N$, etc. (source: §1.33).

### Classical special cases

- **Elastica** (Bernoulli-Euler): inextensible ($\nu = 1$), unshearable ($\eta = 0$), with $M = (EI)(s)[\mu - \mu^\circ(s)]$ — bending couple linear in curvature change.
- **Kirchhoff rod**: same constraints extended to 3D (see [[kirchhoff-rod]]).
- **Unshearable rod**: $\eta = 0$ always; $H$ becomes a Lagrange multiplier.
- **Inextensible rod**: $\nu = 1$ always; $N$ becomes a Lagrange multiplier.

### Boundary conditions

At each end, exactly one condition from each conjugate pair must be prescribed:

| Geometric (kinematic) | Force (natural) |
|---|---|
| $\boldsymbol{r}(s_1) = \boldsymbol{r}_1$ (position) | $\boldsymbol{n}(s_1) = \boldsymbol{n}_1$ (force) |
| $\theta(s_1) = \theta_1$ (orientation) | $M(s_1) = M_1$ (couple) |
| Groove condition (1.38) | — |

The **clamping** condition $\phi(s_1) = \phi_1$ (fixing the angle of $\boldsymbol{r}'$, not just $\boldsymbol{b}$) is an approximation that can be unnatural for shearable rods and must be maintained by a feedback couple (source: §1.42, Antman & Lanza de Cristoforis 1997).

### Equations of motion

For dynamical problems, the right-hand sides of (1.15) and (1.17) are replaced by time derivatives of the linear and angular momenta, yielding:

$$\boldsymbol{n}_s + \boldsymbol{f} = \rho A\,\boldsymbol{r}_{tt} + \rho I\,\boldsymbol{b}_{tt}, \tag{1.45}$$

where $\rho A$, $\rho I$, $\rho J$ are mass, first moment, and second moment of cross-section mass per unit reference length. The full treatment is in Chapter 8; the steady-state ($\boldsymbol{r}_{tt} = 0$) limit recovers the equilibrium equations.

---

## Section 2: Planar Equilibrium of Straight Rods under Terminal Loads (pp. 106–110)

### Setup

No body forces ($\boldsymbol{f} = \boldsymbol{o}$, $l = 0$), $s \in [0,1]$. A compressive terminal force:

$$\boldsymbol{n}(1) = -\Lambda(\cos\alpha\,\boldsymbol{i} + \sin\alpha\,\boldsymbol{j}), \quad \Lambda \geq 0.$$

Since $\boldsymbol{n}' = \boldsymbol{o}$, the contact force is constant: $\boldsymbol{n}(s) = -\Lambda(\cos\alpha\,\boldsymbol{i} + \sin\alpha\,\boldsymbol{j})$ for all $s$. Setting $\gamma := \theta - \alpha$ (angle of director relative to load direction), the bending equation becomes:

$$M' = -\Lambda[\nu\sin\gamma + \eta\cos\gamma]. \tag{2.2b}$$

### Autonomous system

For a **uniform** rod (constitutive functions independent of $s$), the equations reduce to an autonomous system in $(\gamma, M)$:

$$\gamma' = \hat{\mu}(-\Lambda\cos\gamma, \Lambda\sin\gamma, M), \tag{2.10a}$$
$$M' = -\Lambda[\hat{\nu}(\cdot)\sin\gamma + \hat{\eta}(\cdot)\cos\gamma]. \tag{2.10b}$$

### Phase portrait and buckling

The symmetry conditions (1.27)/(2.9) ensure the phase portrait in the $(\gamma, M)$-plane is symmetric about the $M$-axis and periodic in $\gamma$ with period $2\pi$.

**Singular points** occur at $(\gamma, M) = (k\pi, 0)$ for integers $k$ (straight rod, $\gamma = $ const). For an **unshearable** rod these are the only singular points. For a **shearable** rod, additional singular points appear when $\Lambda$ exceeds a threshold $\Lambda^+$:

- $\Lambda < \Lambda^+$: only straight configurations (Fig. 2.14a — centers and saddles at $k\pi$)
- $\Lambda > \Lambda^+$: new singular points at noninteger multiples of $\pi$ (Figs. 2.14b,c)

The transition at $\Lambda = \Lambda^+$ is the onset of buckling (continued in Chapter 5).

### Rod shapes from phase portrait

Integrating $\boldsymbol{r}' = \nu\boldsymbol{a} + \eta\boldsymbol{b}$ with the phase-portrait trajectories gives the rod shapes:

- **Closed orbits** around the origin → **inflexional** configurations (S-curves, loop-on-loop shapes, Fig. 2.15a)
- **Unbounded trajectories** (outside the separatrix) → **noninflexional** configurations (Fig. 2.15b)
- Closed orbits around non-origin singular points (when $\Lambda > \Lambda^+$) → shapes in persistent tension with non-integer shear (Fig. 2.16)

### Elastica special case

Constraining $\nu = 1$, $\eta = 0$, with $M = (EI)(s)\gamma'$, reduces to **Euler's elastica** equation:

$$\frac{d}{ds}\bigl[(EI)(s)\,\gamma'(s)\bigr] + \Lambda\sin\gamma(s) = 0. \tag{2.8}$$

For uniform $(EI)$, this is solved in terms of elliptic functions. Euler (1744) catalogued all possible equilibrium states. The treatment here generalizes Euler's by admitting stretch and shear (source: Nonlinear_Problems_of_Elasticity.pdf §2, historical note).

---

## Connections to yarn mechanics

- The special Cosserat theory is the **generalization of the Kirchhoff rod** ([[kirchhoff-rod]]) that allows extensibility and shear — relevant when yarn compressibility or cross-section shear cannot be neglected.
- The monotonicity condition (§1.23) is the rod-level analog of **positive-definiteness of the elasticity tensor** in 3D continuum theory.
- The stored-energy function $W(\nu, \eta, \mu)$ is the 1D analog of the strain-energy density used in hyperelastic fabric models (see [[constitutive-model]]).
- The phase-portrait analysis of Section 2 underpins the buckling bifurcation theory of Chapter 5 (see [[kirchhoff-rod]] and [[landau-chap2]] for Euler buckling).

---

## Related pages

- [[cosserat-rod]]
- [[kirchhoff-rod]]
- [[constitutive-model]]
- [[landau-chap2]]
- [[coleman-1993]]
- [[yarn-simulation]]
