# Knit Elasticity

**Summary**: The elastic response of a knitted fabric is an emergent property of stitch topology, determined in the linear regime by yarn bending modulus and the symmetry of connecting yarn segments, and in the nonlinear regime by contact confinement as yarn becomes taut.

**Sources**: `raw/Singal_NatureComm_2024.pdf`, `raw/Poincloux_PRX_2018.pdf`, `raw/notes_for_Tim.pdf`

**Last updated**: 2026-04-13

---

## Two regimes of response

### Low-stress (linear) regime
- Dominated by **bending energy** of yarn
- Young's modulus $Y$ is the slope of $\sigma$ vs. $\varepsilon$
- Governed by [[stitch-topology]] — specifically the even/odd symmetry of connecting yarn segments
- Different [[stitch-types]] have Young's moduli differing by orders of magnitude despite small geometric differences

### High-stress (nonlinear/strain-stiffening) regime
- Yarn segments straighten at their mid-lengths; curvature localizes to the entangled contact regions
- **Compression energy** increases markedly
- Response: $\sigma_\text{high}(\varepsilon) \approx \beta(1 - \alpha\varepsilon)^{-2}$, analogous to force-extension of stiff polymers (worm-like chain)
- All four fabric types (stockinette, garter, rib, seed) show similar nonlinear behavior, dominated by yarn geometry rather than pattern

See [[constitutive-model]] for the combined stress-strain relationship.

## Young's moduli of the four fabrics

From uniaxial experiments (acrylic yarn, Singal 2024):

| Fabric | x (course) | y (wale) |
|---|---|---|
| Stockinette | Stiffest | High |
| Garter | Intermediate | Soft |
| Rib | Softest (extreme extensibility) | Intermediate |
| Seed | Soft | Softest |

Rib is by far the softest in the course direction due to odd connecting segments in both adjacent rows; garter and seed are softer in the wale direction. (source: Singal_NatureComm_2024.pdf)

## Normalized rigidity

Because Young's modulus $Y$ depends on both stitch topology and yarn properties, a normalized rigidity is defined:

$$\tilde{Y} = Y \cdot \frac{L \cdot A}{B}$$

where $L$ = loop length, $A$ = stitch area, $B$ = bending modulus. When plotted as $\tilde{Y}_y$ vs $\tilde{Y}_x$, all eight yarn types cluster into four groups — one per fabric pattern — confirming that **anisotropy is topology-dependent, not fiber-dependent** (source: Singal_NatureComm_2024.pdf).

## Effective stretching modulus (Poincloux model)

From the first-principles model (Poincloux PRX 2018), the elastic response of a uniformly deformed stockinette fabric is:

$$F(\varepsilon_h) = \tilde{Y} N_c \delta_{w^*}^2 \left[\frac{1}{(1+\varepsilon_h)^2} - \frac{1}{(1-\delta\frac{w^*}{c^*}\varepsilon_h)^2}\right]$$

where $\tilde{Y} = \tilde{B}/(c^* w^*)$ is the effective stretching modulus (units of line tension, N/m), $N_c$ is the number of course stitches, and $\varepsilon_h$ is the applied wale strain.

The experimentally measured values: $\tilde{Y}^\uparrow = 3.8 \times 10^{-2}$ J/m (loading) and $\tilde{Y}^\downarrow = 0.8 \times 10^{-2}$ J/m (unloading), with the asymmetry due to friction (source: Poincloux_PRX_2018.pdf).

## Bending energy asymmetry parameter $\beta$

The parameter $\beta = \delta(w^*/c^*)^2 \approx 0.24$ (for stockinette) quantifies the asymmetry between course and wale bending energies. It is marginally dependent on strain and can be treated as a fabric characteristic (source: Poincloux_PRX_2018.pdf).

## Poisson ratio

Stockinette fabric has an effective [[poisson-ratio]] of $\nu \approx 0.46$, making it nearly incompressible despite being mostly air. This is an emergent geometric property (source: Poincloux_PRX_2018.pdf).

## Related pages

- [[stitch-types]]
- [[stitch-topology]]
- [[constitutive-model]]
- [[yarn]]
- [[wale-and-course]]
- [[poisson-ratio]]
- [[poincloux-prx-2018]]
- [[singal-naturecomm-2024]]
- [[physics-world-2019]]
