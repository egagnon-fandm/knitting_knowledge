# Pillay 1963 — Tensile Properties of Cotton Fiber Bundles and Yarns (Dry and Wet)

**Summary**: An experimental study of how wetting affects the tensile properties of cotton fiber bundles and spun yarns, covering 27 cotton varieties spun at six twist multipliers. Wetting increases yarn strength (more so at low twist), increases elongation and stiffness, and shifts the optimal twist multiplier for maximum strength from 5.0 (dry) to 4.5 (wet).

**Sources**: `raw/Pillay - 1963 - Investigation of the Relation between the Tensile Properties of Cotton Fiber Bundles and Yarns in th.pdf`

**Last updated**: 2026-05-18

---

## Citation

Pillay, K. P. R. (1963). Investigation of the relation between the tensile properties of cotton fiber bundles and yarns in the dry and wet states. *Textile Research Journal*, 33(5), 333–339. South India Textile Research Association, Coimbatore.

## Experimental design

- **27 cotton varieties** spanning a wide range of fiber properties (mean length 0.73–0.89 in, fineness 141–263 millitex).
- All cottons spun into 24s (24.6 tex) yarn with **twist multipliers 3.75, 4.0, 4.5, 5.0, 5.5, 6.0**.
- Fiber tests: Stelometer (strength and elongation of bundles), gravimetric fineness, caustic soda swelling (maturity).
- Yarn tests: Uster automatic single-yarn tester, 200 measurements per condition (20 tests × 10 bobbins).
- Wet protocol: fibers wetted 15 min; yarns wetted 1 hr at 5 g winding tension. Tests performed immediately on wet specimens.
- Properties reported: breaking strength (g/tex), breaking elongation (%), stiffness (g/tex per % elongation), toughness index (g/tex × % elongation / 2).

## Effect of wetting on fibers

| Property | Change on wetting |
|---|---|
| Breaking strength | +12.0% (without spacer), +21.6% (with spacer) |
| Breaking elongation | +15.4% average (range 4.5–31.5%) |
| Stiffness (stress-strain modulus) | Increases for weak cottons; decreases for strong ones |

The strength increase is attributed to the "weak link" effect: water strengthens the weakest places in fiber bundles by increasing inter-fiber cohesion and friction, with larger benefit for less uniform (weaker) cottons.

## Effect of wetting on yarns

### Strength

- Wet yarn strength is **greater** than dry at all twist multipliers tested.
- Average increase: **+55%** at TM 3.75, declining to **+22%** at TM 6.0.
- The mechanism is increased fiber-to-fiber friction from swelling, not fiber strengthening per se (fiber strength correlations were not statistically significant for the wet-state yarn strength increase).
- **Soft-twisted yarns benefit most** — water penetrates more easily, causing more fiber swelling and untwisting resistance.

### Optimal twist multiplier for strength

| State | Optimal TM for max strength |
|---|---|
| Dry | ≈ 5.0 |
| Wet | ≈ 4.5 |

The shift occurs because fiber swelling partially untwists the yarn. The yarn with TM 4.5 in the wet state effectively has the same twist geometry as TM 5.0 in the dry state.

### Elongation

- Wet breaking elongation **greater** than dry at all TMs.
- Percent increase decreases with twist: +15% at low TM, +7% at high TM.
- Greater elongation at break reflects the more efficient utilization of fiber elongation when swollen fibers form a tighter helical structure.

### Stiffness (tensile modulus)

- Wet yarn stiffness is on average **38% to 15% higher** than dry across the TM range.
- The increase is larger at low twist multipliers; it converges toward dry values at high TM.
- The simultaneous increase in both strength and elongation implies a large stiffness gain — consistent with swelling reducing fiber slippage during extension.

## Fiber–yarn correlations

Multiple correlation coefficients (combining 6 fiber properties simultaneously) for predicting yarn properties:

- Higher in dry state than wet state overall.
- **Wet correlations are systematically lower**, indicating that wetting brings in additional sources of variation (fiber heterogeneity in water-uptake, twist interactions) not captured by standard fiber tests.
- Fiber elongation and weight per unit length are the most predictive single-fiber properties for yarn strength on wetting.

## Relevance to knitting research

- Provides quantitative data on how moisture affects the tensile properties of cotton yarns — directly relevant to wash-and-wear behavior of knitted garments.
- The transverse isotropy of cotton yarn (low compressive stiffness relative to tensile) documented later in [[du-pasquier-2025]] is consistent with the dominance of inter-fiber friction in determining tensile properties here.
- The twist-multiplier dependence of wet strength has implications for knit simulation: yarn properties should not be assumed constant across environmental conditions.

## Follow-on: Htike et al. 2016

[[htike-2016]] extends Pillay's work to much higher twist factors (K > 7,000 vs. Pillay's ~1,865–2,985) and a wider humidity range (10–90% RH and water). At these high twist factors the dominant deformation mechanism shifts: instead of fiber-slippage strength gains, moisture triggers twist relaxation and snarling, increasing extensibility rather than stiffness. The two studies together map out how the twist-moisture interaction changes character across the full industrially relevant twist range.

## Related pages

- [[yarn]]
- [[du-pasquier-2025]]
- [[cornelissen-2009]]
- [[xiong-2026]]
- [[htike-2016]]
