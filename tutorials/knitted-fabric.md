# Knitted Fabric

**Last updated**: 2026-05-04

---

A **knitted fabric** is a 2D surface formed by interlocking loops of yarn into a periodic network of stitches. This tutorial introduces what knitted fabrics are, how they are structured, and why their mechanical properties are so different from other textiles.

## How knitting differs from weaving

In a woven fabric, two independent sets of threads — warp (lengthwise) and weft (crosswise) — are interlaced at right angles. Extension is limited because it requires either stretching the threads themselves or distorting the weave geometry. Maximum strain is typically a few percent.

In a knitted fabric, a **single continuous yarn** per row is formed into a chain of loops, each loop pulling through the one below it. Extension does not require stretching the yarn — instead, the loops can geometrically **unfold, reorient, and straighten** as the fabric is pulled. This geometric mechanism allows knitted fabrics to reach strains of 100–300% while the yarn itself elongates only a few percent.

## The elementary stitches

All weft-knitted fabrics are built from two elementary stitches:

- **Knit stitch (K)**: a loop of yarn passes from the back to the front of the fabric, through an existing loop. On the front face this creates smooth V-shaped columns.
- **Purl stitch (P)**: a loop passes from front to back — geometrically, a knit rotated 180° about the column axis. On the face it creates bumpy horizontal ridges.

K and P are the same geometric object seen from opposite sides. All stitch patterns are spatial arrangements of Ks and Ps.

## Wale and course: the two principal directions

Every knitted fabric has two principal directions defined by its stitch geometry:

- **Course direction** (x): along the rows of stitches, perpendicular to the knitting direction.
- **Wale direction** (y): along the columns of stitches, parallel to the knitting direction.

Each stitch occupies a rectangular **unit cell** with two length scales:
- $c$ = stitch size in the course direction (lateral spacing between stitches)
- $w$ = stitch size in the wale direction (row-to-row spacing)

For nylon monofilament stockinette, typical reference values are $c^* \approx 3.93$ mm and $w^* \approx 2.08$ mm in the relaxed state (source: Poincloux et al. 2018).

Industrial terminology:

- **CPI** (courses per inch) = row density $\approx 1/c$ in units of inch$^{-1}$
- **WPI** (wales per inch) = column density $\approx 1/w$ in units of inch$^{-1}$
- **Stitch density** = CPI × WPI (stitches per square inch)
- **Stitch length**: the total yarn length consumed per loop

## The four canonical fabric patterns

Arranging Ks and Ps in different repeating patterns produces four canonical weft-knit fabrics. The pattern determines which adjacent stitches are connected by **even-symmetry** (K-K or P-P) versus **odd-symmetry** (K-P or P-K) yarn segments, and this distinction is the key to understanding their mechanics.

| Fabric | Pattern | Connecting segments | Mechanical character |
|---|---|---|---|
| **Stockinette** | All Ks on one face | Even in x and y | Stiffest; strong anisotropy; curls at edges |
| **Garter** | Alternating K/P rows | Even in x, odd in y | Soft in wale direction; lies flat |
| **Rib** (1×1) | Alternating K/P columns | Odd in x, even in y | Extremely soft in course; used in cuffs and waistbands |
| **Seed** | Checkerboard of K/P | Odd in x and y | Softest overall; nearly isotropic |

**Why even/odd matters.** An even-symmetry connecting segment must curve to accommodate extension — it acts like a stiff spring ($\sim 180B/\lambda^3$, where $B$ is the yarn bending rigidity and $\lambda$ is the stitch stretch ratio). An odd-symmetry segment can instead rotate as a moment arm — it is about 10× softer ($\sim 12B/\lambda^3$). Fabrics built entirely from odd segments (seed) are far more extensible than those built from even segments (stockinette).

## Key mechanical features

### Extreme extensibility

Because stitch loops can unfold geometrically, knitted fabrics sustain stretch ratios $\lambda = l/L \approx 2$–$3$ (100–200% engineering strain) during normal use. The yarn itself may elongate only a few percent throughout. This geometric extensibility is topological in origin — it requires only that loops be free to reorient.

### Anisotropy

The fabric responds differently along course ($x$) and wale ($y$). The Young's modulus ratio $Y_x/Y_y$ can exceed 10 for some fabrics. Ordering by stiffness:

| Direction | Stiffest → Softest |
|---|---|
| Course (x) | Stockinette > Garter > Seed > Rib |
| Wale (y) | Stockinette > Rib > Garter > Seed |

Anisotropy is controlled by stitch topology, not yarn composition — the same ordering holds across acrylic, cotton, wool, and monofilament yarns.

### J-shaped stress-strain curve

The stress-strain curve is **J-shaped** (concave upward, also called strain-stiffening):

1. **Low-strain regime** (bending-dominated): loops reorient; stress is approximately linear, $\sigma \approx Y\varepsilon$.
2. **High-strain regime** (contact-dominated): loops straighten; curvature concentrates at crossing points where yarns press against each other; stress rises steeply.

The full constitutive model capturing both regimes (Singal et al. 2024):

$$\sigma(\varepsilon) = \underbrace{Y\varepsilon}_{\text{linear, bending}} + \underbrace{\beta(1-\alpha\varepsilon)^{-2}}_{\text{stiffening, contacts}}$$

Parameters $Y$, $\beta$, $\alpha$ are fitted independently for each direction and stitch type. The second term diverges as $\varepsilon \to 1/\alpha$, the maximum extensibility.

### Hysteresis and return point memory

Yarn contacts involve friction. Loading and unloading therefore follow different paths, and the area enclosed between the curves equals energy dissipated by friction per cycle. Under repeated cycling, fabrics display **return point memory**: after loading to a maximum strain $\varepsilon_\text{max}$ and unloading, the next loading curve rejoins the prior unloading curve exactly at $\varepsilon_\text{max}$. This memory is rate-independent.

### Near-incompressibility and yarn-length conservation

When pulled in one direction, the fabric contracts transversely. The effective Poisson ratio of stockinette is $\nu \approx 0.46$ — nearly the same as rubber — despite the fabric being mostly air. This arises from yarn-length conservation: the total yarn length per stitch is fixed,

$$\langle c \rangle + \delta \langle w \rangle = \ell^* = \text{const}, \qquad \delta \approx 0.86$$

So stretching in the wale direction ($w$ increases) forces the course dimension $c$ to decrease. The fabric narrows as it lengthens.

## Applications

Knitted fabrics are used wherever large, controlled deformations are needed:

- Compression garments and bandages (graduated stiffness via stitch pattern)
- Wearable strain sensors and soft robotics actuators
- Medical implants (hernia mesh, surgical grafts)
- Therapeutic gloves for hand conditions
- Architecture (tensile membranes)
- Sports apparel (zone-specific extensibility)

## Example problems

### Problem 1 — Stitch density from CPI and WPI

A knitted fabric has CPI = 20 and WPI = 16.

(a) What are the stitch dimensions $c$ and $w$ in mm?

(b) What is the stitch density in stitches/cm²?

(c) If the course dimension is increased to 28 WPI (tighter wale spacing) while CPI remains 20, by what percentage does the stitch density change?

**Solution:**

**(a) Stitch dimensions:**

One inch = 25.4 mm.

$$c = \frac{25.4 \text{ mm}}{20} = 1.27 \text{ mm}, \qquad w = \frac{25.4 \text{ mm}}{16} = 1.59 \text{ mm}$$

**(b) Stitch density:**

Convert to per-centimetre:
$$\text{CPI in cm}^{-1} = \frac{20}{2.54} = 7.87 \text{ cm}^{-1}, \qquad \text{WPI in cm}^{-1} = \frac{16}{2.54} = 6.30 \text{ cm}^{-1}$$
$$\text{Density} = 7.87 \times 6.30 = \mathbf{49.6 \text{ stitches/cm}^2}$$

**(c) Change in stitch density with WPI = 28:**

$$\text{New WPI in cm}^{-1} = \frac{28}{2.54} = 11.02 \text{ cm}^{-1}$$
$$\text{New density} = 7.87 \times 11.02 = 86.7 \text{ stitches/cm}^2$$
$$\text{Change} = \frac{86.7 - 49.6}{49.6} = \mathbf{75\% \text{ increase}}$$

Tighter wales pack in more stitches per unit area, producing a denser, stiffer, less porous fabric.

---

### Problem 2 — Extensibility: knit vs. weave

A woven cotton swatch elongates from 100 mm to 104 mm before the weave jams and the threads begin to tear. A stockinette swatch of the same yarn elongates from 100 mm to 215 mm before the yarn itself begins to yield.

(a) Compute the engineering strain $e$ and stretch ratio $\lambda$ at failure for each fabric.

(b) What fraction of the total knit extension is due to yarn elongation, if the yarn itself can only sustain 4% engineering strain before yielding?

**Solution:**

**(a) Failure strains and stretch ratios:**

*Woven fabric:*
$$e_\text{woven} = \frac{104 - 100}{100} = 0.04 \quad (4\%), \qquad \lambda_\text{woven} = 1.04$$

*Stockinette:*
$$e_\text{knit} = \frac{215 - 100}{100} = 1.15 \quad (115\%), \qquad \lambda_\text{knit} = 2.15$$

**(b) Fraction of extension from yarn elongation:**

At failure, the yarn has strained 4%. The yarn segments within each stitch account for 4% of the stitch length increase; the remainder is geometric (loop unfolding).

Total fabric extension: 115 mm. Yarn contribution: 4% of the 215 mm final length = 8.6 mm.

$$\text{Fraction} = \frac{8.6}{115} \approx \mathbf{7.5\%}$$

More than 92% of the knit fabric's elongation is geometric — the loops unfold — not from yarn stretching. This is the essence of knit extensibility.

---

### Problem 3 — Fabric selection and constitutive model

A designer is developing a compression bandage. The bandage must be:
- Soft in the course direction (easy to wrap): $Y_x \leq 25$ N/m
- Stiff in the wale direction (provides compression): $Y_y \geq 80$ N/m

Three candidate fabrics have been tested:

| Fabric | $Y_x$ (N/m) | $Y_y$ (N/m) |
|---|---|---|
| Stockinette | 90 | 55 |
| Rib | 14 | 92 |
| Seed | 20 | 24 |

All three share nonlinear parameters $\beta = 5.0$ N/m and $\alpha = 1.4$.

(a) Which fabric meets both requirements?

(b) Compute the anisotropy ratio $Y_y/Y_x$ for each fabric.

(c) Using the constitutive model, compute the stress in the wale direction for the chosen fabric at $\varepsilon = 0.25$.

**Solution:**

**(a) Selecting the fabric:**

- Stockinette: $Y_x = 90 > 25$ ✗ (too stiff to wrap)
- Seed: $Y_y = 24 < 80$ ✗ (too soft to compress)
- Rib: $Y_x = 14 \leq 25$ ✓ and $Y_y = 92 \geq 80$ ✓ → **Rib meets both requirements**

This is expected: rib has odd-symmetry segments in the course direction (very soft) and even-symmetry in the wale direction (relatively stiff).

**(b) Anisotropy ratios:**

$$\text{Stockinette: } Y_y/Y_x = 55/90 = 0.61 \quad \text{(actually softer in wale)}$$
$$\text{Rib: } Y_y/Y_x = 92/14 = \mathbf{6.6} \quad \text{(strongly anisotropic)}$$
$$\text{Seed: } Y_y/Y_x = 24/20 = 1.2 \quad \text{(nearly isotropic)}$$

**(c) Wale stress for rib at $\varepsilon = 0.25$:**

$$\sigma_y = Y_y \varepsilon + \beta(1-\alpha\varepsilon)^{-2}$$
$$= 92 \times 0.25 + \frac{5.0}{(1 - 1.4 \times 0.25)^2}$$
$$= 23.0 + \frac{5.0}{(0.65)^2}$$
$$= 23.0 + \frac{5.0}{0.4225}$$
$$= 23.0 + 11.8 = \mathbf{34.8 \text{ N/m}}$$

At this strain, the nonlinear compression term (11.8 N/m) already contributes about 34% of the total. As $\varepsilon$ approaches the maximum extensibility $1/\alpha = 1/1.4 = 0.71$, the second term diverges and the fabric becomes very stiff — the compression bandage locks up at large strain.
