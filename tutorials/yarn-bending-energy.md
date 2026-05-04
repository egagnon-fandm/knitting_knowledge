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

## Multi-filament softening

Most knitting yarns are not single solid cylinders — they are composed of hundreds or thousands of fine filaments twisted together. This dramatically reduces the effective bending rigidity compared to a solid rod of the same outer diameter.

**Two limiting cases** for a yarn with $N$ filaments of individual modulus $E$ and radius $r_f$, bundled into a composite of outer radius $R$:

| Case | Effective $B$ | Physical picture |
|---|---|---|
| Perfect bonding | $E \cdot I_\text{composite} = E\pi R^4/4$ | All filaments share one neutral axis; maximum stiffness |
| Free sliding | $N \cdot E I_f = N \cdot E\pi r_f^4/4$ | Each filament bends about its own neutral axis; minimum stiffness |

The ratio between these extremes is:

$$\frac{B_\text{bonded}}{B_\text{free}} = \frac{I_\text{composite}}{N I_f} = \frac{R^4}{N r_f^4}$$

For typical yarn with $R/r_f \sim 10$–$50$ and $N \sim 100$–$1000$, this ratio can reach $10^3$–$10^4$. Real yarns fall between the two limits depending on inter-filament friction. At low curvature, static friction locks filaments together (stiffer); at higher curvature they progressively unlock and slide (softer). This nonlinear, history-dependent bending behaviour means $E^b$ must be measured as an effective parameter rather than derived from fibre properties alone.

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

### Problem 2 — Multi-filament softening

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

Perfect bonding makes the yarn $\sim$31,000× stiffer in bending than free sliding. Real multi-filament yarns fall between these extremes depending on inter-filament friction, which is why the effective $E^b$ must always be measured experimentally rather than computed from fibre modulus.

---

### Problem 3 — Diameter scaling and bending moment

A knitter is choosing between two nylon monofilament yarns of the same material ($E = 4.0$ GPa) but different diameters: Yarn A has $d_A = 0.2$ mm and Yarn B has $d_B = 0.4$ mm.

(a) Calculate the bending rigidity $B$ for each yarn.

(b) By what factor does $B$ increase from Yarn A to Yarn B? Confirm this using the diameter ratio alone.

(c) When forming a stitch, each yarn is bent to a radius of curvature of $\rho = 2.0$ mm. What bending moment $M$ must the knitter's needles exert on each yarn?

**Solution:**

**(a) Bending rigidity of each yarn:**

For Yarn A ($d_A = 2.0 \times 10^{-4}$ m):
$$I_A = \frac{\pi d_A^4}{64} = \frac{\pi (2.0 \times 10^{-4})^4}{64} = \frac{\pi \times 1.6 \times 10^{-15}}{64} = 7.85 \times 10^{-17} \text{ m}^4$$
$$B_A = E \cdot I_A = 4.0 \times 10^{9} \times 7.85 \times 10^{-17} = \mathbf{3.14 \times 10^{-7} \text{ N·m}^2}$$

For Yarn B ($d_B = 4.0 \times 10^{-4}$ m):
$$I_B = \frac{\pi d_B^4}{64} = \frac{\pi (4.0 \times 10^{-4})^4}{64} = \frac{\pi \times 2.56 \times 10^{-14}}{64} = 1.257 \times 10^{-15} \text{ m}^4$$
$$B_B = E \cdot I_B = 4.0 \times 10^{9} \times 1.257 \times 10^{-15} = \mathbf{5.03 \times 10^{-6} \text{ N·m}^2}$$

**(b) Diameter scaling:**

$$\frac{B_B}{B_A} = \frac{5.03 \times 10^{-6}}{3.14 \times 10^{-7}} \approx 16$$

This follows directly from $B \propto d^4$. Doubling the diameter increases bending rigidity by $2^4 = 16$, regardless of material. A yarn that is twice as thick requires sixteen times more moment to bend to the same curvature.

**(c) Bending moment at stitch curvature:**

The stitch radius $\rho = 2.0$ mm gives curvature $\kappa = 1/\rho = 500$ m$^{-1}$. Using $M = B\kappa$:

$$M_A = B_A \kappa = 3.14 \times 10^{-7} \times 500 = \mathbf{1.57 \times 10^{-4} \text{ N·m}}$$
$$M_B = B_B \kappa = 5.03 \times 10^{-6} \times 500 = \mathbf{2.51 \times 10^{-3} \text{ N·m}}$$

Yarn B requires 16 times more moment — a factor that grows rapidly with diameter. This is why thick yarns feel stiff and springy on the needles, and why hand-knitters tend to use larger needles (longer lever arm) with heavier yarns.
