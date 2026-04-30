# Yarn Bending Energy

**Last updated**: 2026-04-30

---

Knitted fabrics are extraordinarily extensible — a stockinette swatch can stretch to twice its resting size without permanently deforming. This extensibility does not come from the yarn itself stretching; it comes from the yarn *bending* as the stitch loop changes shape. Understanding yarn bending energy is therefore the key to understanding the low-stress mechanical behaviour of knitted fabrics.

## What is bending energy?

When a slender elastic rod is bent, the fibres on the outside of the curve are stretched and those on the inside are compressed. This internal deformation stores elastic potential energy. For a segment of yarn at arc-length coordinate $s$, the **local curvature** $\kappa(s)$ measures how sharply the yarn turns:

$$\kappa = \left|\frac{d\hat{t}}{ds}\right|$$

where $\hat{t} = d\mathbf{r}/ds$ is the unit tangent vector and $\mathbf{r}(s)$ is the yarn centreline. For a circular arc of radius $\rho$, the curvature is constant: $\kappa = 1/\rho$.

The elastic energy per unit length stored in bending is proportional to $\kappa^2$. Integrating over the whole segment gives the **total bending energy**:

$$E_\text{bend} = \frac{B}{2}\int_0^L \kappa(s)^2\, ds$$

where $B$ is the **bending rigidity** (also called flexural rigidity) of the yarn, with SI units of N·m².

## Bending rigidity $B = EI$

For a homogeneous elastic rod with Young's modulus $E$ and circular cross-section of diameter $d$:

$$B = EI = \frac{\pi d^4 E}{64}$$

where $I = \pi d^4/64$ is the second moment of area. Bending rigidity grows as the *fourth power* of diameter and linearly with $E$.

The bending moment $M$ required to achieve a given curvature is:

$$M = B\kappa$$

A yarn with large $B$ requires a large moment to curve — it is stiff in bending. Note that $B$ depends on both the material stiffness $E$ and the cross-section geometry; doubling the diameter increases $B$ by a factor of 16.

**Typical values**: For nylon monofilament (diameter 150 μm, $E \approx 3$ GPa), $B \approx 7 \times 10^{-8}$ N·m². For soft multi-filament acrylic knitting yarn, the effective $B$ is typically several orders of magnitude smaller.

## Measurement: the cantilever test

The bending rigidity of yarn cannot be reliably calculated from fibre properties alone (see §Multi-filament softening). Instead, it is measured directly. The **cantilever test** is the standard protocol:

1. Clamp one end of a yarn segment horizontally; let the free end droop under gravity.
2. Photograph the deflected shape.
3. Measure the horizontal span $\lambda$ from the clamp to the point directly above the free tip, and the vertical deflection $\delta$.

For a cantilever under uniformly distributed gravity load $q = \pi(d/2)^2 \rho_\text{yarn} g$ (N/m), Euler-Bernoulli beam theory gives the tip deflection:

$$\delta = \frac{q\lambda^4}{8B}$$

Solving for the apparent bending modulus $E^b = B/I$:

$$E^b = \frac{q\lambda^4}{8\delta I}$$

This protocol is used by Cornelissen & Akkerman (2009) and by Ding et al. (2023), who report $E^b = 0.249$ MPa for acrylic knitting yarn.

A note on beam theories: Euler-Bernoulli theory (EBT) assumes plane cross-sections remain plane and neglects shear deformation. The Timoshenko beam theory (TBT) adds a shear term $\delta_\text{shear} = qL^2/(2GA_s)$, but for typical yarn geometries (length $\gg$ diameter) the shear correction is negligible and EBT is accurate.

## Multi-filament softening

Most knitting yarns are not single solid cylinders — they are composed of hundreds or thousands of fine filaments twisted together. This dramatically reduces the effective bending rigidity compared to a solid rod of the same outer diameter.

**Two limiting cases** for a yarn with $N$ filaments of individual modulus $E$ and radius $r_f$, bundled into a composite of outer radius $R$:

| Case | Effective $B$ | Physical picture |
|---|---|---|
| Perfect bonding | $E \cdot I_\text{composite} = E\pi R^4/4$ | All filaments share one neutral axis; maximum stiffness |
| Free sliding | $N \cdot E I_f = N \cdot E\pi r_f^4/4$ | Each filament bends about its own neutral axis; minimum stiffness |

The ratio between these extremes is:

$$\frac{B_\text{bonded}}{B_\text{free}} = \frac{I_\text{composite}}{N I_f} = \frac{R^4}{N r_f^4}$$

For typical yarn with $R/r_f \sim 10$–$50$ and $N \sim 100$–$1000$, this ratio can reach $10^3$–$10^4$. Real yarns fall between the two limits depending on inter-filament friction. At low curvature, static friction locks filaments together (stiffer); at higher curvature they progressively unlock and slide (softer). This nonlinear, history-dependent bending behaviour means $E^b$ must be measured as an effective parameter, not calculated.

## Bending energy and knit elasticity

At rest, the yarn in a stitch forms a loop of radius $\sim w/2$ where $w$ is the stitch width in the wale direction. When the fabric is stretched, the loop geometry changes and the curvature distribution shifts. The elastic restoring force comes from the tendency to minimise bending energy.

In the **low-stress regime** of the fabric stress-strain curve, bending energy dominates. The fabric Young's modulus (slope of $\sigma$ vs. $\varepsilon$) scales as:

$$Y \propto \frac{B}{L \cdot A}$$

where $L$ is the loop length and $A$ is the stitch area. Defining the **normalised rigidity** $\tilde{Y} = Y \cdot LA/B$ removes the yarn-material dependence. When plotted for eight different yarn types, all four fabric patterns (stockinette, garter, rib, seed) each collapse to a single cluster — confirming that stitch topology, not yarn material, sets the anisotropy.

In the **high-stress regime**, the yarn segments straighten and curvature concentrates at the contact crossings. From that point on, compression energy at the contacts takes over (see Tutorial: Yarn Compression Energy).

## Example problems

### Problem 1 — Bending energy of a circular arc

A yarn segment with bending rigidity $B = 2.0 \times 10^{-10}$ N·m² forms a quarter-circle arc of radius $\rho = 2.0$ mm.

(a) What is the curvature $\kappa$?

(b) What is the arc length $s$?

(c) What is the total bending energy stored in this segment?

**Solution:**

(a) For a circular arc of radius $\rho$, the curvature is uniform:
$$\kappa = \frac{1}{\rho} = \frac{1}{2.0 \times 10^{-3}} = 500 \text{ m}^{-1}$$

(b) A quarter-circle ($\theta = \pi/2$) has arc length:
$$s = \rho\theta = 2.0 \times 10^{-3} \times \frac{\pi}{2} = 3.14 \times 10^{-3} \text{ m}$$

(c) Since $\kappa$ is constant, the integral reduces to a product:
$$E_\text{bend} = \frac{B}{2}\kappa^2 s = \frac{2.0 \times 10^{-10}}{2} \times (500)^2 \times 3.14 \times 10^{-3}$$
$$= 1.0 \times 10^{-10} \times 2.5 \times 10^5 \times 3.14 \times 10^{-3} = \mathbf{7.9 \times 10^{-8} \text{ J} \approx 79 \text{ nJ}}$$

This is the bending energy in a single curved yarn segment — comparable in scale to the thermal energy at room temperature ($k_BT \approx 4\times10^{-21}$ J) multiplied by $\sim 2 \times 10^{7}$. Bending is a purely mechanical (not thermal) effect at the stitch scale.

---

### Problem 2 — Cantilever measurement of bending modulus

A yarn of diameter $d = 0.5$ mm and density $\rho_\text{yarn} = 1200$ kg/m³ is clamped horizontally. With a free span of $\lambda = 60$ mm, it sags by $\delta = 8.0$ mm under gravity. Find the bending modulus $E^b$.

**Solution:**

Second moment of area:
$$I = \frac{\pi d^4}{64} = \frac{\pi (5.0 \times 10^{-4})^4}{64} = 3.07 \times 10^{-15} \text{ m}^4$$

Gravity load per unit length:
$$q = \pi\!\left(\frac{d}{2}\right)^2 \rho_\text{yarn} g = \pi \times (2.5 \times 10^{-4})^2 \times 1200 \times 9.81 = 2.31 \times 10^{-3} \text{ N/m}$$

Applying the cantilever formula:
$$E^b = \frac{q\lambda^4}{8\delta I} = \frac{2.31 \times 10^{-3} \times (0.060)^4}{8 \times 0.0080 \times 3.07 \times 10^{-15}}$$

Numerator: $2.31 \times 10^{-3} \times 1.296 \times 10^{-5} = 2.99 \times 10^{-8}$ N·m³

Denominator: $8 \times 0.0080 \times 3.07 \times 10^{-15} = 1.96 \times 10^{-16}$ m⁵

$$E^b = \frac{2.99 \times 10^{-8}}{1.96 \times 10^{-16}} = \mathbf{1.53 \times 10^8 \text{ Pa} = 153 \text{ MPa}}$$

This is a plausible modulus for a stiff monofilament or a tightly spun yarn with high inter-filament friction. Soft multi-filament spun yarns typically give $E^b \sim 0.1$–$1$ MPa when measured by this method.

---

### Problem 3 — Multi-filament softening

A composite yarn consists of $N = 200$ glass filaments, each of diameter $d_f = 10$ μm and Young's modulus $E = 70$ GPa. The composite yarn has outer diameter $D = 0.5$ mm.

Compare the effective bending rigidity under (a) perfect bonding and (b) free sliding of the filaments. What is the ratio?

**Solution:**

**(a) Perfect bonding** — all filaments share the composite neutral axis:
$$I_\text{composite} = \frac{\pi D^4}{64} = \frac{\pi (5.0 \times 10^{-4})^4}{64} = 3.07 \times 10^{-15} \text{ m}^4$$
$$B_\text{bonded} = E \cdot I_\text{composite} = 7.0 \times 10^{10} \times 3.07 \times 10^{-15} = \mathbf{2.15 \times 10^{-4} \text{ N·m}^2}$$

**(b) Free sliding** — each filament bends about its own neutral axis:
$$I_f = \frac{\pi d_f^4}{64} = \frac{\pi (1.0 \times 10^{-5})^4}{64} = 4.91 \times 10^{-22} \text{ m}^4$$
$$B_\text{free} = N \cdot E \cdot I_f = 200 \times 7.0 \times 10^{10} \times 4.91 \times 10^{-22} = \mathbf{6.87 \times 10^{-9} \text{ N·m}^2}$$

**Ratio:**
$$\frac{B_\text{bonded}}{B_\text{free}} = \frac{2.15 \times 10^{-4}}{6.87 \times 10^{-9}} \approx \mathbf{31{,}300}$$

Perfect bonding makes the yarn $\sim$31,000× stiffer in bending than free sliding. Real multi-filament yarns fall between these extremes depending on inter-filament friction, which is why the effective $E^b$ must always be measured by cantilever test rather than computed from fibre modulus.

---

## Further reading

- Cornelissen, B. & Akkerman, R. (2009). "Analysis of yarn bending behaviour." University of Twente. — systematic cantilever tests on single-filament and multi-filament yarns; derives the EBT/TBT framework and explains inter-filament friction softening.
- Ding, F. et al. (2023). "Yarn-level simulation of weft-knitted fabrics." *ACM Transactions on Graphics*. — uses the cantilever protocol to calibrate acrylic yarn at $E^b = 0.249$ MPa; formulates the bending energy integral used in B-spline simulation.
- Singal, K. et al. (2024). "Programming mechanics in knitted materials, stitch by stitch." *Nature Communications* 15, 2622. — shows how bending modulus $B$ enters the normalised rigidity $\tilde{Y}$; demonstrates that topology, not fibre type, determines anisotropy.
- Landau, L. D. & Lifshitz, E. M. — *Theory of Elasticity* (Course of Theoretical Physics, Vol. 7), §17–18. — rigorous derivation of the rod bending energy from continuum mechanics; bending and torsion rigidities for circular cross-sections.
- Likharev, K. — *Essential Graduate Physics*, Ch. 7. [LibreTexts, CC BY-NC-SA] — accessible treatment of beam bending, the Euler-Bernoulli model, and elastic energy.
