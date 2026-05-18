# Yarn

**Summary**: Yarn is a hierarchical 1D material (short staple fibers spun into a continuous strand) whose dominant mechanical contributions to fabric behavior are bending stiffness and compressibility; extensional rigidity and torsion play negligible roles in normal fabric deformation.

**Sources**: `raw/Singal_NatureComm_2024.pdf`, `raw/notes_for_Tim.pdf`, `raw/Poincloux_PRX_2018.pdf`, `raw/Cornelissen_Analysis_of_yarn_bending_behaviour_2009.pdf`, `raw/Unravelling the Mechanics of Knitted Fabrics Through.pdf`, `raw/Chen_2025_Multilevel_Mechanical_Modeling_Weft_Knit.pdf`, `raw/Pillay - 1963 - ...pdf`, `raw/Xiong et al. - 2026 - ...pdf`, `raw/Htike et al. - 2016 - ...pdf`

**Last updated**: 2026-05-18

---

## Structure

Yarn is inherently hierarchical: short staple fibers are spun or twisted into an indefinitely long strand. This internal structure creates internal stresses and friction that complicate mechanical characterization. As a result, bending modulus is best measured via cantilever experiments rather than three-point flexural tests (which compress the yarn cross-section) (source: Singal_NatureComm_2024.pdf).

## Key mechanical properties

### Bending modulus $B$ (or $E^b$)
The dominant energy cost for yarn deforming in a stitch. The bending energy for a curve $\gamma(s)$ is:

$$E_\text{bend} = \frac{B}{2} \int_0^L ds \left|\partial_s \hat{t}\right|^2 = \frac{E^b I l}{2} \int_\Omega \kappa^2\, ds$$

where $\hat{t} = \partial_s \gamma$ is the unit tangent and $\kappa = \|\mathbf{y}' \times \mathbf{y}''\|/\|\mathbf{y}'\|^3$ is the local curvature (sources: Singal_NatureComm_2024.pdf, Ding 2023).

**Cantilever measurement**: bending stiffness is measured by clamping one end of a yarn horizontally and measuring the vertical deflection $\delta$ under gravity over horizontal span $\lambda$. For a distributed load $q = \pi r^2 \rho g$:
$$E^b = \frac{q\lambda^4}{8\delta I}$$
This is the same protocol in Cornelissen 2009 and Ding 2023. The Singal/Singal group used a variant (hanging off platform edge). Result for acrylic spun yarn: $E^b = 0.249$ MPa (source: Ding 2023).

**Flexural rigidity formula**: for a circular cross-section yarn of diameter $d$:
$$G_0 = EI = \frac{\pi d^4 E}{64}$$

where $E$ is the Young's modulus of the yarn material. (source: Jamshaid & Mishra 2024, Cornelissen 2009)

**Multi-filament softening**: in spun or multi-filament yarns, individual filaments can slide past each other during bending, reducing the effective bending stiffness far below the homogeneous-cross-section prediction. The effective $E^b$ is dominated by inter-filament friction and must be measured directly, not calculated from fiber modulus (source: Cornelissen 2009). See [[cornelissen-2009]] for analysis.

### Compression (core-shell interaction)
Yarn has a finite diameter $2R$ and resists compression when two yarn segments are pressed together. Modeled as a hard core with a soft shell interaction potential derived from experiments (source: Singal_NatureComm_2024.pdf). Compression energy becomes important in the high-stress (strain-stiffening) regime.

In Dimitriyev's simulation framework (source: notes_for_Tim.pdf), yarn-yarn contact is modeled via a Hertzian potential:

$$V_\text{int} = \frac{M}{5} \sum_{i,j} \Delta_{ij}^{5/2} \quad \text{for } \Delta_{ij} < 0$$

where $\Delta_{ij} = |\gamma_m(i/N_\text{sph}) - \gamma_n(j/N_\text{sph})| - 2R$ is the overlap distance.

### Torsional rigidity
Comparatively negligible for balanced, spun yarn — the yarn is allowed to freely twist in simulations (source: Singal_NatureComm_2024.pdf).

### Extensional rigidity
The yarn is modeled as **inextensible** in the Dimitriyev / Singal framework (total length $L$ is a fixed constraint). Ding et al. 2023 uses a linear elastic stretching term with $E^s = 79.0$ MPa for acrylic yarn, noting that less than 20% of yarn segments exceed 5% tensile strain even at 60% fabric strain — so the inextensibility approximation is reasonable for typical loading ranges.

The stitch structure provides fabric-level extensibility; the yarn itself stretches only in regime 2 (high-strain, yarn-stretching-dominated response).

## Loop length $L$

The **loop length** (yarn length per stitch) is a key geometric parameter. It is measured by dissecting sample swatches and averaging. Together with bending modulus $B$ and stitch area $A$, it enters the normalized rigidity plots that collapse data across different yarn types (source: Singal_NatureComm_2024.pdf).

## Yarn types studied

Multiple yarn materials have been tested, showing that **stitch pattern, not fiber type, determines relative anisotropy** (source: Singal_NatureComm_2024.pdf):

| Yarn | Gauge |
|---|---|
| Brava worsted 100% acrylic | 9-12 WPI |
| Pearl cotton 3/2 | fine |
| Lace weight alpaca-mohair | fine |
| Lace weight cashmere | fine |
| Lace weight bamboo | fine |
| Wool/acrylic/cashmere blend | 14-18 WPI (glove prototype) |
| Nylon monofilament 150 μm | model system (Poincloux) |

## Transverse anisotropy

Cotton and nylon yarns are **transversely isotropic**: their transverse (radial) compressive stiffness is orders of magnitude lower than their longitudinal tensile stiffness. This arises from the loosely bound fiber bundle structure — fibers reconfigure laterally under compression while resisting elongation more strongly. PET monofilament, being a single extruded fiber, behaves as isotropic.

Experimental distinction (source: Chen_2025_Multilevel_Mechanical_Modeling_Weft_Knit.pdf §2): the **free-standing diameter $d_0$** (at rest) is measurably larger than the **post-knit diameter $d_k$** (in fabric). This difference reflects the compressive pre-stress imposed during knitting by yarn-yarn contact forces at crossings. For accurate FEA, compression tests must be performed on yarns pre-tensioned to $d_k$.

## Tensile modulus: twist angle and friction

For cotton ring-spun yarn, the tensile modulus depends primarily on **twist angle** and **inter-fiber friction coefficient**, not yarn diameter (source: Xiong et al. 2026, [[xiong-2026]]):

- Tensile modulus **decreases** with twist angle; the drop is sharp above ~29°.
- Friction coefficient $\mu_f \approx 0.5$ gives the best experimental match (< 2% error in FE simulations).
- At high twist, friction reaches a "mutual locking" plateau — further increase in $\mu_f$ beyond ~0.4 produces diminishing returns.

The modified rule-of-mixtures captures this coupling:

$$E'_y = \cos^2\!\theta \cdot (1 + \mu_f\sin^2\theta) \cdot V_f E_f$$

where $E_f$ is the fiber longitudinal modulus, $V_f$ is fiber volume fraction, and $\theta$ is the surface twist angle. This outperforms the classical $E_y = \cos^2\!\theta \cdot V_f E_f$ (source: Xiong et al. 2026).

## Wet properties (cotton)

Wetting a cotton yarn increases its tensile strength, elongation, and stiffness (source: Pillay 1963, [[pillay-1963]]):

| Property | Average change on wetting | Dependence on twist |
|---|---|---|
| Breaking strength | +22% to +55% | Larger gain at low TM |
| Breaking elongation | +7% to +15% | Smaller gain at high TM |
| Stiffness (modulus) | +15% to +38% | Larger gain at low TM |

The mechanism is increased inter-fiber friction from fiber swelling — not intrinsic fiber strengthening. Wetting also shifts the optimal twist multiplier for maximum strength from ~5.0 (dry) to ~4.5 (wet), because swelling partially untwists the yarn. These effects are specific to staple (short-fiber) cotton; monofilament PET is unaffected by wetting within clothing-use strains (source: Chen_2025_Multilevel_Mechanical_Modeling_Weft_Knit.pdf §3).

## High-twist regime: humidity increases extensibility

At very high twist factors (K > 7,000, twist angles >40°), the moisture response reverses character relative to normal-twist yarns (source: Htike et al. 2016, [[htike-2016]]):

- **Extensibility (EM-1) increases with RH** for all yarns. Higher twist amplifies the effect.
- **Resilience decreases with RH** — at 90% RH, roughly 50% of the first-cycle extension becomes permanent residual strain.
- **Twist ratio controls extensibility ratio**: for yarns of equal count, $\text{EM-1}(Y_2)/\text{EM-1}(Y_1) = E_1/E_2 \approx 3.08$ (constant at 40–90% RH), where $E$ is the longitudinal modulus. Higher twist lowers $E$, increasing extensibility at fixed load.
- **Snarling** occurs at very high humidity (>70% RH) for the most twisted yarns: over-twist torque relaxes by forming local coils, further increasing extensibility. Snarled sections have locally higher twist angles.
- **First-cycle hysteresis** is much larger than subsequent cycles — the same cycling-induced softening observed at the fabric level in [[return-point-memory]] and [[crackling-dynamics]] has its origin partly at the yarn level.

The weft-direction extensibility of plain-woven crepe fabric made from high-twist weft yarn reaches 16–26%, placing it in the same range as outer-knitted fabrics. This confirms that high twist is a structural mechanism for achieving knit-like compliance in a woven structure.

## Non-Hookean behavior

Yarn is a soft fibrous material and behaves similarly to rubber: its mechanical response is **non-Hookean** — stress is not linearly proportional to strain, and the response depends on loading history and rate. This means that standard continuum mechanics moduli (Young's modulus, shear modulus) cannot be directly applied to yarn as they would to steel or glass. Instead, yarn bending stiffness (B) and contact compressibility are measured empirically and used as inputs to fabric-level models. See [[hookes-law]] for discussion of the limits of linear elasticity for soft materials.

## Related pages

- [[knitted-fabrics]]
- [[stitch-types]]
- [[knit-elasticity]]
- [[yarn-simulation]]
- [[wale-and-course]]
- [[cornelissen-2009]]
- [[ding-2023]]
- [[jamshaid-mishra-2024]]
- [[du-pasquier-2025]]
- [[pillay-1963]]
- [[xiong-2026]]
- [[htike-2016]]
