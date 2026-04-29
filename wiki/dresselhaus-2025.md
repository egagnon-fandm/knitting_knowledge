# Dresselhaus, Hellebrand et al. — Return Point Memory in Knitted Fabrics (2025)

**Summary**: Demonstration that knitted fabrics exhibit return point memory (RPM) under cyclic uniaxial loading — a rate-independent, non-local hysteresis phenomenon explained by modeling yarn contacts as hysterons in an extended Preisach model.

**Sources**: `raw/Dresselhaus et al. - 2025 - Return point memory in knitted fabrics.pdf`

**Last updated**: 2026-04-13

---

## Citation

Dresselhaus, E. J., Hellebrand, S., Roy, R., Mandadapu, K. K., & Govindjee, S. (2025). Return point memory in knitted fabrics. arXiv:2512.02132v2 [cond-mat.soft]. Dated December 17, 2025.

## Key contributions

1. First systematic demonstration of return point memory (RPM) in knitted fabrics.
2. Shows hysteresis is **rate-independent** over two orders of magnitude in strain rate.
3. Identifies yarn-yarn contacts as the microscopic source of hysteresis (hysterons).
4. Develops a phenomenological Preisach extension that quantitatively replicates all memory features: non-locality, wiping-out, congruency.
5. Points to spatial symmetries of stitch patterns as constraints on the tensorial hysteresis properties.

## Material

- **Fabric**: Ribbed fabric, machine-knitted from acrylic fingering-weight yarn
- **Machine**: Instron universal testing machine
- **Clamps**: Custom paperclip clamps
- **Initial length**: $L = 131$ mm (zero-strain state defined in Appendix A3)
- **Extension rates tested**: $\Delta = 0.025$, $0.25$, $2.5$ mm/s

## Return point memory protocol

1. Load from zero to $\varepsilon_1$ → unload to zero → repeat: gives **return point A**
2. Load past $\varepsilon_1$ to $\varepsilon_2 > \varepsilon_1$ → creates new return point B, wipes memory of A
3. Cycle between $\varepsilon_1$ and $\varepsilon_2$: nested loops determined solely by $\varepsilon_2$

**Congruency**: loops between the same pair of strains are the same shape regardless of how many intermediate cycles were performed, as long as the return point is the same.

## Physical mechanism

Yarn contacts in entangled regions are bistable: during loading they are compressed and resist; during unloading the compressed yarn does not resist with the same strength. These contacts are identified as **hysterons** in the Preisach framework.

Strain is decomposed: $\varepsilon = \varepsilon_e + \varepsilon_t$ (elastic + entanglement), with stress $\sigma = E \varepsilon_e$.

## Preisach model

Total stress:

$$\sigma(\varepsilon[t], \varepsilon_t, \varepsilon_\text{max}; \alpha, \beta) = \iint_{\alpha \geq \beta} \mu(\alpha, \beta, \varepsilon_t, \varepsilon_\text{max}) \cdot s(\varepsilon[t], \varepsilon_t, \varepsilon_\text{max}; \alpha', \beta') \, d\alpha' \, d\beta'$$

The density function $\mu$ depends on the maximal strain experienced $\varepsilon_\text{max}$, encoding non-local memory and wiping-out. Entanglement strain $\varepsilon_t$ evolves via Karush-Kuhn-Tucker conditions.

## Simulation results

The extended Preisach model:
- Fits the experimental cycling data to $\varepsilon_1, \varepsilon_2, \varepsilon_1$ well
- Reproduces nested hysteresis loops including reconnection paths
- Captures three key features: non-local memory, wiping-out, congruency

## Broader implications

- Results extend to other loop-based textiles (crochet, woven fabrics) and knot-based materials
- Memory in woven fabrics expected to be weaker (fewer entangled contacts per unit area)
- Spatial symmetry of stitch patterns constrains tensor structure of memory properties
- Engineering RPM via fabrication tension could enable tuneable memory materials
- Connection to dislocation accumulation at grain boundaries: the entanglement strain evolves analogously

## Relationship to crackling dynamics

Both RPM (Dresselhaus 2025) and crackling (Poincloux PRL 2018) originate from stick-slip at yarn contacts. RPM captures the **cumulative** effect under cyclic loading; crackling captures **individual events** during quasistatic stretching. They are complementary views of the same underlying friction-at-contacts mechanism.

## Related pages

- [[return-point-memory]]
- [[crackling-dynamics]]
- [[knit-elasticity]]
- [[stress-strain-curve]]
- [[stitch-topology]]
- [[knitted-fabrics]]
- [[poincloux-prl-2018]]
