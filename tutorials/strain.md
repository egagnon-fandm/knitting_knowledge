# Strain

**Last updated**: 2026-04-29

---

When a material deforms — whether stretched, compressed, or twisted — we need a way to quantify *how much* it has changed shape, independently of its original size. That quantity is **strain**: a dimensionless measure of local deformation. This tutorial covers the main strain definitions, the strain tensor, and why knitted fabrics require the large-deformation versions.

## Engineering strain (Cauchy strain)

The simplest definition applies to a bar of initial length $L$ stretched to length $l$:

$$e = \frac{l - L}{L} = \frac{\Delta L}{L}$$

This is **engineering strain** (or Cauchy strain). It is dimensionless and the most common measure for small deformations (metals, stiff polymers). Positive $e$ means extension; negative means compression.

**Example**: a steel cable of length $L = 2$ m elongates by $\Delta L = 1$ mm. Its engineering strain is $e = 0.001/2 = 0.0005$ (0.05%).

## Stretch ratio

For large deformations — rubbers, biological tissue, knitted fabrics — the **stretch ratio** $\lambda$ is preferred:

$$\lambda = \frac{l}{L}$$

Related to engineering strain by $e = \lambda - 1$. A stretch ratio of $\lambda = 2$ means the material doubled in length (100% engineering strain); $\lambda = 0.5$ means it compressed to half. Knitted fabrics routinely reach $\lambda = 2$–$3$ in normal use. At these strains, loops are unfolding geometrically; the yarn itself elongates only a few percent.

## True (logarithmic) strain

For sequential deformation steps — as in metal forming — **true strain** (logarithmic strain) is additive and therefore preferred:

$$\varepsilon = \ln\!\left(\frac{l}{L}\right) = \ln\lambda = \ln(1 + e)$$

Two successive true strains $\varepsilon_1$ and $\varepsilon_2$ give total true strain $\varepsilon_1 + \varepsilon_2$. Engineering strains are *not* additive in this sense.

| Measure | Symbol | Formula | Best used when |
|---|---|---|---|
| Engineering strain | $e$ | $(l - L)/L$ | Small deformations ($e \ll 1$) |
| Stretch ratio | $\lambda$ | $l/L$ | Large deformations; elastomers, fabrics |
| True strain | $\varepsilon$ | $\ln(l/L)$ | Incremental forming; path-dependent processes |

At small strains all three agree to first order: $\varepsilon \approx e \approx \lambda - 1$ for $|e| \ll 1$.

## The strain tensor

In a 3D body, local deformation involves both stretching and shearing. For small displacements $\mathbf{q}(\mathbf{r})$, the **strain tensor** is:

$$s_{jj'} = \frac{1}{2}\!\left(\frac{\partial q_j}{\partial r_{j'}} + \frac{\partial q_{j'}}{\partial r_j}\right)$$

- **Diagonal entries** ($s_{xx}$, $s_{yy}$, $s_{zz}$): fractional length change along each axis (normal strain).
- **Off-diagonal entries** ($s_{xy}$, etc.): change in angle between originally perpendicular material lines (shear strain).
- **Volume strain** (dilatation): $\Delta V / V = s_{xx} + s_{yy} + s_{zz} = \text{Tr}(\mathbf{s})$.

Symmetry ($s_{jj'} = s_{j'j}$) leaves 6 independent components.

## Strain in knitted fabrics

Knitted fabrics operate in the **finite strain** regime — deformations large enough that the deformed and reference configurations differ significantly. Several consequences:

1. **Engineering strain is insufficient**: stretch ratios $\lambda$ are the natural language.
2. **Two principal directions**: wale (column, $y$) and course (row, $x$). Strain in one direction couples to the other through the Poisson ratio.
3. **Two regimes**: at low strain, loops reorient and yarn bends (geometric extensibility); at high strain, yarn itself stretches.

### The Poisson ratio

When a material is stretched in one direction it contracts transversely. The Poisson ratio $\nu$ quantifies this:

$$\nu = -\frac{\varepsilon_\text{transverse}}{\varepsilon_\text{axial}}$$

For stockinette knit, $\nu \approx 0.46$ — nearly the same as rubber ($\nu = 0.5$, incompressible) — even though the fabric is mostly air. This near-incompressibility is an emergent geometric property of the stitch topology, not a yarn material property.

### Yarn-length conservation

A key constraint in stitch mechanics: the total yarn length per stitch is conserved. For stockinette this gives:

$$\langle c \rangle + \delta \langle w \rangle = \ell^* = \text{const}$$

where $c$ and $w$ are stitch dimensions in the course and wale directions, and $\delta \approx 0.86$ is a geometry parameter set by the knitting machine. This relation couples the two strain components and is the basis for predicting the Poisson ratio and displacement fields from first principles.

## Example problems

### Problem 1 — Three strain measures

A yarn segment with rest length $L = 40$ mm is stretched to $l = 56$ mm. Compute: (a) engineering strain, (b) stretch ratio, (c) true strain.

**Solution:**

(a) $e = (56 - 40)/40 = 16/40 = \mathbf{0.40}$ (40%)

(b) $\lambda = 56/40 = \mathbf{1.40}$

(c) $\varepsilon = \ln(1.40) \approx \mathbf{0.336}$

Note $\varepsilon < e$ for extension. For small deformations (say, $e = 0.01$) all three would agree to better than 1%. At $e = 0.40$ they differ by 16%, so the choice of measure matters.

---

### Problem 2 — Poisson ratio from fabric measurements

A stockinette sample has initial dimensions: width (course) $w_0 = 100$ mm, height (wale) $h_0 = 80$ mm. After stretching the wale direction to $h = 90$ mm, the width is measured as $w = 94.3$ mm. Compute the Poisson ratio.

**Solution:**

Axial strain (wale direction):
$$\varepsilon_\text{wale} = \frac{90 - 80}{80} = 0.125$$

Transverse strain (course direction):
$$\varepsilon_\text{course} = \frac{94.3 - 100}{100} = -0.057 \quad \text{(compression)}$$

Poisson ratio:
$$\nu = -\frac{\varepsilon_\text{course}}{\varepsilon_\text{wale}} = -\frac{-0.057}{0.125} = \mathbf{0.46}$$

This matches the value measured by Poincloux et al. (2018) for nylon monofilament stockinette.

---

### Problem 3 — Yarn-length conservation in a stitch

A stockinette stitch has reference dimensions $c^* = 3.93$ mm (course) and $w^* = 2.08$ mm (wale), with machine geometry parameter $\delta = 0.86$. The fabric is stretched in the wale direction to $w = 2.60$ mm. Find the new course dimension $c$.

**Solution:**

Reference yarn length per stitch:
$$\ell^* = c^* + \delta w^* = 3.93 + 0.86 \times 2.08 = 3.93 + 1.789 = 5.719 \text{ mm}$$

Applying conservation ($c + \delta w = \ell^*$):
$$c = 5.719 - 0.86 \times 2.60 = 5.719 - 2.236 = \mathbf{3.48 \text{ mm}}$$

The course dimension shrank from 3.93 mm to 3.48 mm as the wale dimension grew from 2.08 mm to 2.60 mm — the fabric narrowed while being stretched in height, exactly as expected from a positive Poisson ratio.

---

## Further reading

- Likharev, K. — *Essential Graduate Physics*, Ch. 7 §7.1. [LibreTexts, CC BY-NC-SA] — systematic introduction to the strain tensor for 3D continua.
- Landau, L. D. & Lifshitz, E. M. — *Theory of Elasticity* (Vol. 7), Ch. I. — rigorous development of finite strain theory.
- Poincloux, S., Adda-Bedia, M., & Lechenault, F. (2018). "Geometry and elasticity of a knitted fabric." *Physical Review X* 8, 021075. — derives the yarn-length conservation constraint and Poisson ratio of stockinette from first principles.
- Singal, K. et al. (2024). "Programming mechanics in knitted materials, stitch by stitch." *Nature Communications* 15, 2622. — measures strain in the course and wale directions for four knit fabrics across eight yarn types.
