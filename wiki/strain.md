# Strain

**Summary**: Strain is the measure of deformation of a material relative to a reference configuration — a dimensionless ratio of length change to original length.

**Sources**: `raw/Strain.md` (Wikipedia)

**Last updated**: 2026-04-13

---

Strain quantifies how much a material has deformed locally. It is dimensionless (m/m) and distinct from [[deformation]], which has units of length.

## Engineering strain (Cauchy strain)

The most common definition for small deformations:

$$e = \frac{\Delta L}{L} = \frac{l - L}{L}$$

where $L$ is original length and $l$ is final length. Positive = tensile, negative = compressive.

## Stretch ratio

An alternative measure used for large-deformation materials (elastomers, knitted fabrics):

$$\lambda = \frac{l}{L}$$

Related to engineering strain by $e = \lambda - 1$. Knitted fabrics can reach stretch ratios of 2–3 in normal use, making this a more natural measure than $e$ (source: Strain.md).

## Logarithmic (true) strain

$$\varepsilon = \ln(\lambda) = \ln(1 + e)$$

Correct for incremental deformation sequences; preferred when deformation path matters.

## Strain regimes

- **Infinitesimal strain theory**: strains and rotations both small; undeformed and deformed configurations treated as identical. Used for steel, concrete.
- **Finite strain theory**: large rotations and strains; deformed and reference configurations differ significantly. Required for elastomers, biological soft tissue, and **knitted fabrics** (source: Strain.md).

## Normal and shear strain

The full strain state at a point is captured by the strain tensor, with:
- **Normal strains** ($\varepsilon_{xx}$, $\varepsilon_{yy}$, $\varepsilon_{zz}$): change in length along each axis
- **Shear strains** ($\gamma_{xy}$, etc.): change in angle between originally perpendicular material lines

In knitted fabric experiments, both the longitudinal (wale) strain and the transverse (course) strain are measured to compute the [[poisson-ratio]] of the fabric (source: Poincloux PRX 2018).

## Volume (bulk) strain

$$\delta = \frac{\Delta V}{V_0} = \varepsilon_{xx} + \varepsilon_{yy} + \varepsilon_{zz}$$

Pure shear produces no volume change.

## Related pages

- [[stress]]
- [[deformation]]
- [[stress-strain-curve]]
- [[poisson-ratio]]
- [[knit-elasticity]]
- [[wale-and-course]]
- [[poincloux-prx-2018]]
