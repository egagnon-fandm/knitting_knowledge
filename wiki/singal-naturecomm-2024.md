# Singal, Dimitriyev et al. — Programming Mechanics in Knitted Materials, Stitch by Stitch (Nature Communications 2024)

**Summary**: Systematic study combining experiment and simulation to show how stitch topology (knit vs. purl patterns) programs the emergent elastic response of knitted fabrics, with a reduced-symmetry model and constitutive relation enabling rational design of textile metamaterials.

**Sources**: `raw/Singal_NatureComm_2024.pdf`, `raw/Singal_NatureComm_2024_Suppl.pdf`

**Last updated**: 2026-04-13

---

## Citation

Singal, K., Dimitriyev, M. S., Gonzalez, S. E., Cachine, A. P., Quinn, S., & Matsumoto, E. A. (2024). Programming mechanics in knitted materials, stitch by stitch. *Nature Communications*, **15**, 2622. DOI: 10.1038/s41467-024-46498-z

## Key contributions

1. **Four-fabric systematic study**: Stockinette, garter, rib, seed — stress-strain curves measured in both x and y directions for 8 yarn types.
2. **Even/odd segment framework**: Explains relative stiffness differences from first principles of segment symmetry.
3. **Reduced Symmetry (RS) model**: Estimates Young's moduli from geometry alone; close quantitative agreement with experiment.
4. **Nonlinear constitutive model**: $\sigma(\varepsilon) = Y\varepsilon + \beta(1-\alpha\varepsilon)^{-2}$ fits all fabrics.
5. **FEA validation**: Constitutive model applied to finite element simulation; reproduces non-affine displacement fields.
6. **Therapeutic glove prototype**: Demonstrates programmable mechanics using all four fabric types.

## Experiments

- Uniaxial stretching in both x and y directions
- **8 yarn types**: acrylic, cotton, lace-weight alpaca-mohair, blue mohair, cashmere, bamboo, acrylic (lace), and glove yarn
- **2 industrial knitting machines**: Taitexma (acrylic/cotton) and STOLL CMS 530 HP (lace weights)
- **Tracking**: Fiji+TrackMate for pin/clamp positions; OCR for dynamometer reading
- **DIC** (digital image correlation, Ncorr software) for spatially resolved displacement fields

## Simulations

Elastica-model with degree-5 Bézier splines, inextensible yarn, hard-core soft-shell contact. Periodic boundary conditions; energy minimization varying box dimensions. See [[yarn-simulation]].

## Key results

### Young's modulus ordering

| Direction | Stiffest → Softest |
|---|---|
| x (course) | Stockinette > Garter > Seed > Rib |
| y (wale) | Stockinette > Rib > Garter > Seed |

Rib has extreme extensibility in x (180% extension under the same applied stress as 21% for stockinette; cf. Jamshaid & Mishra 2024 who report a maximum of ~200% for rib — a different measurement condition).

### Normalized rigidity collapse

The normalized rigidity $Y \cdot L \cdot A / B$ clusters by fabric type across all 8 yarn types — confirming stitch pattern, not fiber, determines anisotropy.

### Even/odd stiffness ratio

From the RS model: $Y_\text{even} / Y_\text{odd} \approx 15$ at typical geometry parameters.

### RS model agreement

RS model estimates are systematically ~10-30% stiffer than experiment, but qualitative and near-quantitative agreement across all fabrics and directions.

## Application: therapeutic glove

A prototype glove uses:
- **Stockinette** (blue): stiff wrist support (radiocarpal joint, all-even segments)
- **Seed** (pink): isotropic thumb mobility (carpometacarpal joint, all-odd segments)
- **Rib** (green): finger extension/contraction (odd in course direction)
- **Garter** (orange): wrist flexion (odd in wale direction)

The different regions are knit seamlessly; their interfaces are structurally continuous.

## Open questions / limitations

- Seed fabric simulation diverges from experiment at high strain due to a compression-related buckling instability in the computation
- Model uses only loading experiments; unloading hysteresis not addressed (see [[return-point-memory]])
- Goal of fully automated design pipeline (desired mechanics → stitch pattern) not yet achieved

## Related pages

- [[stitch-types]]
- [[stitch-topology]]
- [[knit-elasticity]]
- [[constitutive-model]]
- [[yarn-simulation]]
- [[yarn]]
- [[knitted-fabrics]]
- [[dimitriyev-notes-2019]]
- [[ding-2023]]
