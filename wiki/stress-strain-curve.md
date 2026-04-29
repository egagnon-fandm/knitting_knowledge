# Stress-Strain Curve

**Summary**: A stress-strain curve plots the relationship between applied force per unit area (stress) and resulting deformation (strain), revealing key material properties including Young's modulus, yield strength, and ultimate tensile strength.

**Sources**: `raw/Stress_strain_curve.md` (Wikipedia), `raw/Singal_NatureComm_2024.pdf`, `raw/Work_hardening.md` (Wikipedia)

**Last updated**: 2026-04-16

---

## Stages for a typical ductile material

### 1. Linear elastic region
Stress is proportional to [[strain]]: $\sigma = E \varepsilon$, where $E$ is **Young's modulus** (slope of the curve). The material fully recovers when load is removed. Ends at the **yield point**.

### 2. Strain hardening region
Beyond yield, plastic deformation accumulates. Stress increases until the **ultimate tensile strength** (UTS). For some metals (steel) there is a flat "Lüders band" region at the lower yield point.

Quantified by **Hollomon's law**: σ = Kε_p^n, where ε_p is plastic strain and n ∈ [0.2, 0.5] is the strain hardening exponent. See [[work-hardening]] for the full treatment.

### 3. Necking region
Cross-sectional area decreases locally; engineering stress drops even as true stress increases. Ends in fracture.

## Knitted fabric stress-strain behavior

Knitted fabrics do not follow the ductile or brittle paradigms above. Their stress-strain curves show two distinct regimes (source: Singal_NatureComm_2024.pdf):

1. **Low-stress linear regime**: Slope = Young's modulus $Y$. Governed by [[stitch-topology]] and [[knit-elasticity]]; dominated by **bending energy** of yarn.
2. **High-stress strain-stiffening regime**: Response becomes strongly nonlinear as yarn segments straighten and become taut. Governed by **compression/contact energy**. Modeled as $\sigma_\text{high}(\varepsilon) \sim \beta(1 - \alpha\varepsilon)^{-2}$.

The combined constitutive model is:
$$\sigma(\varepsilon) = \sigma_\text{low}(\varepsilon) + \sigma_\text{high}(\varepsilon)$$

See [[constitutive-model]] for details.

### Hysteresis and cyclic loading

Unlike metals, knitted fabrics show pronounced hysteresis — the unloading curve does not follow the loading curve. This is due to friction and stick-slip at yarn contact points. Under repeated cycles, fabrics exhibit **return point memory**: the fabric "remembers" the maximum strain previously experienced. See [[return-point-memory]].

## Toughness

Toughness is the area under the stress-strain curve: $\int_0^{\varepsilon_f} \sigma \, d\varepsilon$, with units of energy per volume.

## Related pages

- [[strain]]
- [[deformation]]
- [[knit-elasticity]]
- [[constitutive-model]]
- [[return-point-memory]]
- [[crackling-dynamics]]
- [[work-hardening]]
- [[hookes-law]]
