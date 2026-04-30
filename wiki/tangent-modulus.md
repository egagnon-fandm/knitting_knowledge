# Tangent Modulus

**Summary**: The tangent modulus is the instantaneous slope of the stress-strain curve, dσ/dε, at a given strain. It equals Young's modulus in the linear elastic regime and changes continuously in a nonlinear regime such as strain stiffening.

**Sources**: `raw/Singal_NatureComm_2024.pdf`, `raw/Stress_strain_curve.md`

**Last updated**: 2026-04-29

---

## Definition

For a material with stress-strain relationship σ(ε), the **tangent modulus** at strain ε is:

$$E_t(\varepsilon) = \frac{d\sigma}{d\varepsilon}$$

It is a local, strain-dependent quantity. Contrast with two related but distinct concepts:

| Quantity | Definition | Properties |
|---|---|---|
| **Young's modulus** E | dσ/dε in the linear elastic regime | Constant; a material property |
| **Tangent modulus** E_t(ε) | dσ/dε at a given ε | Varies along the curve; equals E in the linear regime |
| **Secant modulus** E_s(ε) | σ(ε)/ε — chord slope from the origin | Also varies; always ≤ E_t for a strain-stiffening curve |

For a linear elastic material (Hooke's law), all three coincide: E_t = E_s = E at every strain.

## Tangent modulus for knitted fabrics

Knitted fabrics follow the two-regime constitutive model (source: Singal_NatureComm_2024.pdf):

$$\sigma(\varepsilon) = Y\varepsilon + \beta(1 - \alpha\varepsilon)^{-2}$$

Differentiating with respect to ε gives the tangent modulus:

$$E_t(\varepsilon) = Y + \frac{2\alpha\beta}{(1 - \alpha\varepsilon)^3}$$

### Behavior in each regime

**Low-stress regime** (ε small, αε ≪ 1):

$$E_t \approx Y + 2\alpha\beta$$

The second term is small, so E_t ≈ Y — the tangent modulus is approximately the Young's modulus Y measured from the linear portion of the curve.

**High-stress regime** (ε → 1/α):

$$E_t \to \infty$$

The tangent modulus diverges, reflecting the yarn segments becoming fully taut. This is the strain-stiffening signature of knitted fabrics. The secant modulus also grows but remains finite up to the extensibility limit.

## Physical interpretation

In the low-stress regime, the tangent modulus reflects the bending stiffness of yarn rearranging within the stitch. In the high-stress regime, it reflects the compressional contact energy as yarn segments straighten and jam. The crossover between the two is the transition point where the dominant energy contribution shifts from bending to contact. See [[knit-elasticity]] for the physical picture and [[constitutive-model]] for the full model.

## Relation to anisotropy

Because Y, α, and β are independently fitted for the x (course) and y (wale) directions, the tangent modulus is different in each direction at the same ε. The anisotropy ratio E_t^y / E_t^x evolves with strain: at low strain it is set by the Young's moduli ratio (topology-dependent), while at high strain both directions stiffen and the ratio can converge. See [[wale-and-course]] and [[stitch-topology]].

## Hysteresis

Under cyclic loading, loading and unloading follow different σ(ε) curves (friction at yarn contacts). The tangent modulus therefore differs between loading and unloading at the same ε. The effective stretching modulus Ỹ is larger during loading than unloading by a factor of ~5× for stockinette nylon (source: Poincloux_PRX_2018.pdf). See [[return-point-memory]].

## Related pages

- [[hookes-law]]
- [[stress-strain-curve]]
- [[constitutive-model]]
- [[knit-elasticity]]
- [[stitch-topology]]
- [[wale-and-course]]
- [[return-point-memory]]
