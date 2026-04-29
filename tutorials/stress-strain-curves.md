# Stress-Strain Curves

**Last updated**: 2026-04-29

---

A **stress-strain curve** is the fundamental experimental fingerprint of a material's mechanical behaviour. It records how much stress develops as the material is deformed, and its shape immediately reveals whether a material is stiff or compliant, ductile or brittle, linear or highly nonlinear. This tutorial covers how to read the curve, the physics behind its main features, and why knitted fabrics produce a distinctly different shape from metals.

## What the axes mean

A stress-strain experiment applies a controlled deformation (strain $\varepsilon$) while measuring the resisting force per unit area (stress $\sigma$). The result is plotted as $\sigma$ vs. $\varepsilon$.

The key quantities readable from the curve:

| Quantity | How to extract it |
|---|---|
| **Young's modulus** $E$ | Slope of the initial linear portion: $E = \Delta\sigma / \Delta\varepsilon$ |
| **Yield stress** $\sigma_y$ | Stress at which the curve departs from linearity (permanent deformation begins) |
| **Ultimate tensile strength** | Maximum stress on the curve |
| **Fracture strain** $\varepsilon_f$ | Strain at break |
| **Toughness** | Area under the full curve: $\int_0^{\varepsilon_f} \sigma\, d\varepsilon$ (energy per unit volume or unit width) |

## Curve for a ductile metal (steel)

A ductile metal such as mild steel shows four stages:

1. **Linear elastic**: $\sigma = E\varepsilon$; the material returns to its original shape upon unloading. For steel, $E \approx 200$ GPa.
2. **Yield point**: plastic deformation begins at $\sigma_y$. Some steels show a sharp upper/lower yield; others transition gradually.
3. **Strain hardening**: continued deformation increases yield strength as dislocations accumulate. Described empirically by $\sigma = K\varepsilon_p^n$ (Hollomon's law), where $n \in [0.2, 0.5]$.
4. **Necking and fracture**: cross-section localises; engineering stress drops even as true stress increases until fracture.

## J-shaped curve: elastomers and knitted fabrics

Rubber, biological tissue, and knitted fabrics all produce a qualitatively different curve: **J-shaped** (convex upward, also called strain-stiffening).

1. **Low-stress regime** (Regime 1): very compliant — a small stress produces a large strain. The structure extends by geometric reorientation (polymer chains unfurl; knit loops unbend and reorient), not by stretching covalent bonds.
2. **High-stress regime** (Regime 2): rapidly stiffening — once structural elements are taut, any further extension must stretch bonds or yarn directly. The stiffness rises sharply.

There is no yield point in the ductile sense; the material does not permanently deform during normal loading (though friction and memory effects complicate the unloading path).

## The constitutive model for knitted fabrics

For knitted fabrics the two regimes have distinct physical origins and are captured by a two-term model (Singal et al. 2024):

$$\sigma(\varepsilon) = \underbrace{Y\varepsilon}_{\text{Regime 1}} + \underbrace{\beta(1 - \alpha\varepsilon)^{-2}}_{\text{Regime 2}}$$

- **Regime 1 term** ($Y\varepsilon$): linear, with Young's modulus $Y$ set by stitch topology (which stitches are knit or purl) and yarn bending modulus $B$. Different stitch patterns give $Y$ values differing by over an order of magnitude.
- **Regime 2 term** ($\beta(1-\alpha\varepsilon)^{-2}$): diverges as $\varepsilon \to 1/\alpha$ (maximum extensibility). The form resembles the worm-like chain model for polymer stretching.

Parameters $Y$, $\beta$, $\alpha$ depend on both the stitch pattern and the loading direction (wale vs. course).

## Anisotropy: direction matters

Knitted fabrics are **anisotropic** — the stress-strain curve in the wale direction (columns) differs from that in the course direction (rows). The Young's modulus ratio $Y_x / Y_y$ between directions can exceed 10 for some fabrics. The ordering by stiffness:

| Direction | Stiffest → Softest |
|---|---|
| Course ($x$) | Stockinette > Garter > Seed > Rib |
| Wale ($y$) | Stockinette > Rib > Garter > Seed |

Rib fabric is extreme: it is by far the softest in the course direction (loops straighten freely) yet relatively stiff in the wale direction.

## Hysteresis and loading history

In an ideal elastic material, the unloading curve exactly retraces the loading curve. In knitted fabrics, it does not — the two curves differ by a hysteresis loop whose area equals the energy dissipated per cycle by friction at yarn contacts.

Under repeated cycling, the fabric exhibits **return point memory**: after cycling to a maximum strain $\varepsilon_\text{max}$ and back, the next loading curve rejoins the prior unloading curve exactly at $\varepsilon_\text{max}$. This memory is rate-independent (it persists across two orders of magnitude in loading speed) and is modelled by a Preisach framework in which each yarn contact acts as a bistable element.

## Example problems

### Problem 1 — Young's modulus from experimental data

A rib-stitch fabric sample (50 mm wide) is tested in the course direction. Two data points in the linear regime:

| Strain $\varepsilon$ | Force $F$ (N) |
|---|---|
| 0.05 | 0.75 |
| 0.20 | 3.00 |

Compute the Young's modulus $Y$ in N/m.

**Solution:**

Convert force to fabric stress (force per unit width, $w = 50$ mm = 0.05 m):

$$\sigma_1 = \frac{0.75}{0.05} = 15 \text{ N/m}, \qquad \sigma_2 = \frac{3.00}{0.05} = 60 \text{ N/m}$$

Slope of the stress-strain curve:

$$Y = \frac{\sigma_2 - \sigma_1}{\varepsilon_2 - \varepsilon_1} = \frac{60 - 15}{0.20 - 0.05} = \frac{45}{0.15} = \mathbf{300 \text{ N/m}}$$

---

### Problem 2 — Constitutive model: comparing the two regimes

A stockinette fabric has parameters $Y = 200$ N/m, $\beta = 5$ N/m, $\alpha = 1.5$. Compute the stress at $\varepsilon = 0.20$ and $\varepsilon = 0.50$. What fraction of the total stress comes from Regime 2 at each strain?

**Solution:**

At $\varepsilon = 0.20$:
$$\sigma_\text{low} = 200 \times 0.20 = 40 \text{ N/m}$$
$$\sigma_\text{high} = \frac{5}{(1 - 1.5 \times 0.20)^2} = \frac{5}{(0.70)^2} = \frac{5}{0.49} \approx 10.2 \text{ N/m}$$
$$\sigma = 40 + 10.2 = \mathbf{50.2 \text{ N/m}} \quad (\text{Regime 2 contributes } 20\%)$$

At $\varepsilon = 0.50$:
$$\sigma_\text{low} = 200 \times 0.50 = 100 \text{ N/m}$$
$$\sigma_\text{high} = \frac{5}{(1 - 1.5 \times 0.50)^2} = \frac{5}{(0.25)^2} = \frac{5}{0.0625} = 80 \text{ N/m}$$
$$\sigma = 100 + 80 = \mathbf{180 \text{ N/m}} \quad (\text{Regime 2 contributes } 44\%)$$

As strain approaches the maximum extensibility $1/\alpha = 0.67$, the Regime 2 term diverges and dominates. This is the physical signature of yarn becoming fully taut.

---

### Problem 3 — Toughness from a piecewise linear curve

A knitted fabric stress-strain curve is approximated by two linear segments:
- Segment 1: $\sigma$ rises linearly from 0 to 120 N/m as $\varepsilon$ goes from 0 to 0.40.
- Segment 2: slope increases; $\sigma$ rises linearly from 120 to 200 N/m as $\varepsilon$ goes from 0.40 to 0.70, at which point the fabric fails.

Compute the toughness (energy per unit width, J/m).

**Solution:**

**Segment 1** — triangle:
$$T_1 = \frac{1}{2} \times \varepsilon_1 \times \sigma_1 = \frac{1}{2} \times 0.40 \times 120 = 24 \text{ J/m}$$

**Segment 2** — trapezoid:
$$T_2 = \frac{\sigma_\text{start} + \sigma_\text{end}}{2} \times \Delta\varepsilon = \frac{120 + 200}{2} \times (0.70 - 0.40) = 160 \times 0.30 = 48 \text{ J/m}$$

**Total toughness:**
$$T = T_1 + T_2 = 24 + 48 = \mathbf{72 \text{ J/m}}$$

Note: because fabric stress is in N/m (not Pa), toughness has units of J/m (energy per unit width), not J/m³. To convert to volumetric toughness one would need to divide by the fabric thickness, which is typically 1–3 mm.

---

## Further reading

- Likharev, K. — *Essential Graduate Physics*, Ch. 7. [LibreTexts, CC BY-NC-SA] — covers Young's modulus, Hooke's law, rod bending, and elastic energy from a physics perspective.
- Singal, K. et al. (2024). "Programming mechanics in knitted materials, stitch by stitch." *Nature Communications* 15, 2622. — full experimental and simulation study of J-shaped curves for stockinette, garter, rib, and seed; introduces the two-term constitutive model.
- Poincloux, S., Adda-Bedia, M., & Lechenault, F. (2018). "Geometry and elasticity of a knitted fabric." *Physical Review X* 8, 021075. — derives the stockinette constitutive relation from first principles; explains hysteresis between loading and unloading moduli.
- Dresselhaus, E. J. et al. (2025). "Return point memory in knitted fabrics." arXiv:2512.02132. — systematic study of hysteresis and memory in cyclic stress-strain curves; Preisach model.
- Jamshaid, H. & Mishra, R. (Eds.). (2024). *Knitting Science, Technology, Process and Materials*. Springer. — Ch. 5 covers the mechanics of jersey, rib, and interlock fabrics from an industrial perspective.
