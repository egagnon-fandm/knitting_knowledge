# Poisson's Ratio

**Summary**: Poisson's ratio ν is the negative ratio of transverse strain to axial strain when a material is uniaxially loaded; it quantifies how much a material narrows when stretched.

**Sources**: `raw/Poisson_ratio.md` (Wikipedia), `raw/Poincloux_PRX_2018.pdf`

**Last updated**: 2026-04-13

---

## Definition

$$\nu = -\frac{d\varepsilon_\text{trans}}{d\varepsilon_\text{axial}}$$

Positive strain = extension, negative = contraction. Most materials have $\nu \in [0, 0.5]$.

| Material | Typical ν |
|---|---|
| Steel, rigid polymers | ~0.3 |
| Rubber | ~0.5 (nearly incompressible) |
| Cork | ~0.0 |
| Stockinette knit fabric | ~0.46 (source: Poincloux PRX 2018) |

## Auxetic materials

Materials with negative Poisson's ratio — they expand transversely when stretched. Certain polymer foams, origami folds, and some knitting patterns can exhibit auxetic behavior, though the four standard fabrics (stockinette, garter, rib, seed) studied in Singal 2024 do not.

## Volumetric change

For a uniaxially stretched material:
$$\frac{\Delta V}{V} \approx (1 - 2\nu) \frac{\Delta L}{L}$$

At $\nu = 0.5$, volume is conserved. At $\nu \approx 0.46$ (stockinette), the fabric is nearly but not exactly incompressible (source: Poincloux PRX 2018).

## Knit-fabric Poisson ratio

The Poisson ratio of a knitted fabric is not a simple yarn property — it emerges from the stitch geometry. In the Poincloux PRX 2018 model, it is defined through the ratio of course and wale dimension changes:

$$\nu = \left[\frac{(c^* - \langle c \rangle)/c^*}{(\langle w \rangle - w^*)/w^*}\right] \approx 0.46$$

where $c^*$ and $w^*$ are reference stitch dimensions (source: `raw/Poincloux_PRX_2018.pdf`). Remarkably, even though the knitted fabric is highly deformable and largely hollow, it behaves like a near-incompressible elastic medium in terms of area conservation.

The anisotropic elastic response of different [[stitch-types]] (rib, garter, seed) produces different effective Poisson ratios in the course vs. wale directions; see [[knit-elasticity]].

## Related pages

- [[strain]]
- [[deformation]]
- [[knit-elasticity]]
- [[wale-and-course]]
- [[stitch-types]]
- [[singal-naturecomm-2024]]
