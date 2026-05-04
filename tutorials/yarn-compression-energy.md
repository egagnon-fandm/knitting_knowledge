# Yarn Compression Energy

**Last updated**: 2026-04-30

---

At every stitch crossing in a knitted fabric, two yarn segments meet and press against each other. When the fabric is stretched to large strains, these inter-yarn contacts become increasingly compressed, and the energy stored in resisting this compression becomes the dominant mechanical contribution. **Yarn compression energy** is responsible for the strain-stiffening behaviour in the high-strain regime of a knitted fabric stress-strain curve.

## The contact geometry at a stitch crossing

In a knitted stitch, the yarn from one row passes through the loop of the row below, creating a contact where two yarn segments cross at approximately 90°. This geometry is called the **elastic orthogonal clasp**.

Even for perfectly flexible, inextensible tubes, the contact region at a right-angle crossing is not a point but a **closed diamond-shaped region** bounded by four pressure ridges. At each ridge, the two yarns press against each other and deform their cross-sections. The contact geometry and the material compliance of the yarn determine how much force is required to push the two segments closer — this is the compression potential.

In practice, simulation models approximate the contact with analytically tractable potentials:

| Model | Contact energy | Used in |
|---|---|---|
| Hertz (sphere–sphere) | $\propto \delta^{5/2}$ | Dimitriyev/Singal simulations |
| Quadratic spring | $\propto \delta^2$ | Ding et al. 2023 |
| Full orthogonal clasp (FEM) | Numerically computed | Grandgeorge et al. 2021 |

where $\delta$ is the overlap distance: $\delta = 2R - |\mathbf{r}_1 - \mathbf{r}_2|$ when two yarn centrelines of radius $R$ are closer than their combined radii.

## The Hertz contact model

The most widely used model for yarn compression is the **Hertz contact potential**, adapted for elastic spheres. For two elastic bodies pressed together by overlap $\delta$, the contact force and energy are:

$$F_\text{contact} = \frac{4}{3} E^* \sqrt{R_\text{eff}}\, \delta^{3/2}$$

$$U_\text{Hertz} = \frac{2}{5} F_\text{contact} \cdot \delta = \frac{8}{15} E^* \sqrt{R_\text{eff}}\, \delta^{5/2}$$

where $E^* = E/[2(1-\nu^2)]$ is an effective modulus (for two identical materials) and $R_\text{eff}$ is the effective contact radius. The force scales as $\delta^{3/2}$ (stiffer than a spring, which scales as $\delta^1$), and the energy as $\delta^{5/2}$.

In the Dimitriyev/Singal simulation framework, each yarn segment is discretised into spheres of radius $R$, and the total contact energy is:

$$V_\text{int} = \frac{M}{5}\sum_{i,j} |\Delta_{ij}|^{5/2}, \quad \Delta_{ij} = |\mathbf{r}_i - \mathbf{r}_j| - 2R < 0$$

where $M$ is a contact stiffness parameter calibrated against yarn compression experiments.

## Two-regime fabric mechanics

The fabric stress-strain response has two distinct phases driven by the competition between bending and compression energy.

**Low-strain regime** (bending-dominated): The yarn segments are curved but not in tight contact. The dominant energy cost is bending energy (see Tutorial: Yarn Bending Energy). The loops rearrange their shape, curvature redistributes, and the fabric extends by geometric reorientation. Stress is approximately linear in strain: $\sigma \approx Y\varepsilon$.

**High-strain regime** (compression-dominated): As the fabric stretches further, yarn segments within each stitch progressively straighten. Curvature migrates out of the open spans and concentrates at the entangled contact regions. At these crossings, the contact overlap $\delta$ grows rapidly — since the Hertz energy scales as $\delta^{5/2}$, the restoring force rises steeply. This produces the **strain-stiffening** (J-shaped) signature.

The full constitutive model (Singal 2024) captures both contributions:

$$\sigma(\varepsilon) = \underbrace{Y\varepsilon}_{\text{bending}} + \underbrace{\beta(1 - \alpha\varepsilon)^{-2}}_{\text{compression}}$$

The second term diverges as $\varepsilon \to 1/\alpha$, the **maximum extensibility** — when all yarn is taut and the contacts are fully jammed. The parameter $\alpha$ is set by stitch geometry (how much yarn can straighten), and $\beta$ by the contact stiffness. Parameters $Y$, $\alpha$, $\beta$ are independently fitted for the course ($x$) and wale ($y$) directions.

## Friction at contacts: the capstan effect

Every yarn contact involves not just normal compression but also **friction**. When one yarn slides over another, the tension is amplified by the capstan (Euler-Eytelwein) equation:

$$\frac{T_1}{T_0} = e^{\mu\varphi}$$

where $T_0$ is the incoming tension, $T_1$ is the outgoing tension, $\mu$ is the Coulomb coefficient of friction, and $\varphi$ is the effective winding angle of the contact.

This friction asymmetry has several major consequences for the fabric's mechanical behaviour:

- **Hysteresis**: during loading, contacts tighten and tension builds up; during unloading, they slip the other way following a different path. The loading curve lies above the unloading curve, and the enclosed area equals the energy dissipated per cycle. For stockinette nylon, the loading stiffness $\tilde{Y}^\uparrow$ is about 5× higher than the unloading stiffness $\tilde{Y}^\downarrow$.

- **Crackling**: each sudden contact slip releases a burst of acoustic energy. This is the macroscopic origin of the crackling sound when knitted fabric is quickly stretched.

- **Return point memory**: the fabric remembers the maximum strain reached in a prior loading cycle. On the next loading curve, it rejoins the prior unloading curve exactly at that maximum strain. This rate-independent memory arises because each yarn contact is a bistable element (a "hysteron") that switches irreversibly between locked and slipped states.

## Example problems

### Problem 1 — Hertz contact force and energy

Two soft elastic yarn segments (effective modulus $E^* = 50$ kPa, radius $R = 1.0$ mm) are pressed together to an overlap of $\delta = 20$ μm.

(a) Compute the contact force.

(b) Compute the stored contact energy.

**Solution:**

(a) Contact force:
$$F = \frac{4}{3} E^* \sqrt{R}\, \delta^{3/2} = \frac{4}{3} \times 5.0 \times 10^4 \times \sqrt{10^{-3}} \times (2.0 \times 10^{-5})^{3/2}$$

Evaluate each factor: $\sqrt{10^{-3}} = 3.16 \times 10^{-2}$ m$^{1/2}$ and $(2.0 \times 10^{-5})^{3/2} = 2.83 \times 3.16 \times 10^{-8} = 8.94 \times 10^{-8}$ m$^{3/2}$:

$$F = 1.333 \times 5.0 \times 10^4 \times 3.16 \times 10^{-2} \times 8.94 \times 10^{-8} = \mathbf{1.88 \times 10^{-4} \text{ N} \approx 0.19 \text{ mN}}$$

(b) Contact energy:
$$U = \frac{2}{5} F\delta = 0.4 \times 1.88 \times 10^{-4} \times 2.0 \times 10^{-5} = \mathbf{1.5 \times 10^{-9} \text{ J} \approx 1.5 \text{ nJ}}$$

This is comparable in magnitude to the bending energy per stitch arc ($\sim$nJ, from Tutorial: Yarn Bending Energy), consistent with both contributions being important in the crossover region between the two regimes.

---

### Problem 2 — Strain-stiffening contributions

A stockinette fabric in the wale direction has constitutive parameters $Y = 150$ N/m, $\beta = 6.0$ N/m, $\alpha = 1.5$.

At strains $\varepsilon = 0.30$ and $\varepsilon = 0.60$, compute the bending and compression contributions to the total stress, and the fraction from the compression term.

**Solution:**

**At $\varepsilon = 0.30$:**
$$\sigma_\text{bend} = Y\varepsilon = 150 \times 0.30 = 45 \text{ N/m}$$
$$\sigma_\text{comp} = \beta(1 - \alpha\varepsilon)^{-2} = 6.0 \times (1 - 1.5 \times 0.30)^{-2} = 6.0 \times (0.55)^{-2} = \frac{6.0}{0.3025} = 19.8 \text{ N/m}$$
$$\sigma = 45 + 19.8 = 64.8 \text{ N/m}, \qquad \text{compression fraction: } \frac{19.8}{64.8} = \mathbf{31\%}$$

**At $\varepsilon = 0.60$:**
$$\sigma_\text{bend} = 150 \times 0.60 = 90 \text{ N/m}$$
$$\sigma_\text{comp} = 6.0 \times (1 - 1.5 \times 0.60)^{-2} = 6.0 \times (0.10)^{-2} = 6.0 \times 100 = 600 \text{ N/m}$$
$$\sigma = 90 + 600 = 690 \text{ N/m}, \qquad \text{compression fraction: } \frac{600}{690} = \mathbf{87\%}$$

The maximum extensibility is $\varepsilon_\text{max} = 1/\alpha = 1/1.5 = 0.67$. At $\varepsilon = 0.60$ we are close to this limit, and the compression term exceeds the bending term by a factor of 6.7. The tangent modulus $E_t = Y + 2\alpha\beta/(1-\alpha\varepsilon)^3$ also diverges as $\varepsilon \to 1/\alpha$.

---

### Problem 3 — Capstan friction at a yarn crossing

A yarn wraps over another yarn at a contact that subtends an effective angle $\varphi = \pi/3$ rad (60°). The Coulomb coefficient of friction between the two yarns is $\mu = 0.35$.

(a) During loading, if the tension entering the contact is $T_0 = 10.0$ mN, what is the tension leaving it?

(b) During unloading, the tension ratio reverses. If the same contact now has incoming tension $T_1$ (the value from part a), what tension does it output?

(c) What does this imply about the ratio of loading to unloading stiffness in the fabric?

**Solution:**

(a) Loading — capstan amplification:
$$T_1 = T_0\, e^{\mu\varphi} = 0.010 \times e^{0.35 \times \pi/3} = 0.010 \times e^{0.366} = 0.010 \times 1.44 = \mathbf{14.4 \text{ mN}}$$

(b) Unloading — the friction now opposes release rather than loading, so the tension ratio reverses:
$$T_\text{out} = \frac{T_1}{e^{\mu\varphi}} = \frac{14.4 \text{ mN}}{1.44} = \mathbf{10.0 \text{ mN}}$$

The process at this single contact is reversible: the same 10 mN enters and 10 mN leaves, but the *path* is different. During loading the contact amplifies (10 → 14.4 mN); during unloading it attenuates (14.4 → 10 mN). The fabric must supply more tension during loading than unloading to achieve the same geometric deformation.

(c) Each contact contributes a factor $K = e^{\mu\varphi} = 1.44$ asymmetry. Many contacts act in series and parallel across the fabric. The effective loading stiffness exceeds the unloading stiffness approximately by a factor related to $K$. For stockinette nylon, experiments give loading stiffness $\tilde{Y}^\uparrow \approx 5\times$ unloading stiffness $\tilde{Y}^\downarrow$, consistent with multiple friction contacts each contributing a factor $K \gtrsim 1$.
