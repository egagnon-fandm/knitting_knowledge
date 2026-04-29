# Crackling Dynamics

**Summary**: When stretched quasistatically, knitted fabrics display crackling noise — an intermittent, scale-invariant mechanical response driven by stick-slip events at yarn contacts that propagate as avalanches through the stitch network, with power-law size distributions matching mean-field predictions for soft amorphous materials.

**Sources**: `raw/Poincloux_PRL_2018.pdf`, `raw/Poincloux_PRX_2018.pdf`

**Last updated**: 2026-04-17

---

## What is crackling noise?

Crackling noise is an intermittent response characterized by discrete events of broadly distributed sizes, often forming avalanches. It appears in systems including:
- Granular materials
- Metallic glasses
- Seismic faults
- Knitted fabrics (discovered by Poincloux et al. 2018)

Despite their topologically ordered structure, knitted fabrics exhibit crackling dynamics because friction at yarn contact points adds an irreversible, stochastic element to an otherwise elastic system.

## Physical mechanism

A knit consists of a regular network of frictional contacts linked by the elasticity of the yarn. When deformed:

1. Stitches deform elastically through **yarn bending**
2. Friction at crossing points introduces uncertainty in contact forces
3. When local stress exceeds the friction threshold, **stick-slip events** occur
4. One slip redistributes stress to neighboring contacts, potentially triggering further events
5. These cascades are **avalanches**

The stitch network cannot rearrange structurally ([[knitted-fabrics#Topological protection]]) — it is topologically locked. This makes the system distinct from foams or granular packings where rearrangement occurs.

Each frictional contact is an **elastic orthogonal clasp** (Grandgeorge et al. 2021 — see [[yarn-contact]]): two yarn segments in near-orthogonal contact with a diamond-shaped contact region and a capstan-like tension asymmetry. The stick-slip threshold corresponds to the contact switching between its locked and sliding states.

## Experimental measurements

Poincloux et al. (PRL 2018) performed tensile tests on a $83 \times 83$ stitch nylon monofilament fabric (150 μm diameter), recording:

1. **Force signal** at high frequency: shows linear loading segments interrupted by abrupt force drops $\Delta f$
2. **High-resolution images** every $\Delta L = 0.2$ mm: enables tracking of stitch displacement fields

### Nonaffine displacement field

The affine (linear) part of the displacement is subtracted, leaving the **nonaffine field** $\vec{u} = \vec{u}_\text{tot} - \vec{u}_\text{lin}$. This field shows highly heterogeneous structure with abrupt changes along diagonal lines — reminiscent of dislocation lines in crystals (source: Poincloux_PRL_2018.pdf).

### Vorticity and deviatoric strain

Two invariants of the displacement gradient tensor are used as event signatures:

$$\omega = \frac{\partial u_y}{\partial x} - \frac{\partial u_x}{\partial y} \quad \text{(vorticity)}$$

$$\varepsilon_d = \sqrt{\left(\frac{\partial u_x}{\partial x} - \frac{\partial u_y}{\partial y}\right)^2 + \left(\frac{\partial u_y}{\partial x} + \frac{\partial u_x}{\partial y}\right)^2} \quad \text{(deviatoric strain)}$$

High values of $|\omega|$ and $\varepsilon_d$ mark sliding events. Divergence and shear strain are vanishingly small at event locations (source: Poincloux_PRL_2018.pdf).

## Power-law distributions

Three independent measurements of avalanche size all show power-law decay:

| Measurement | Exponent |
|---|---|
| Force drops $\Delta f$ | $-1.50 \pm 0.03$ |
| Vorticity events $S_\omega$ | $-1.51 \pm 0.05$ |
| Deviatoric strain events $S_d$ | $-1.61 \pm 0.03$ |

These are consistent with the mean-field prediction of $-3/2$ for soft amorphous materials (Dahmen et al. 2011, cited in Poincloux PRL 2018).

The internal ($S_\omega$, $S_d$) and external ($\Delta f$) measurements are linearly correlated, confirming they measure the same avalanche events with a proportionality constant $E_p = 0.12$ N (source: Poincloux_PRL_2018.pdf).

## Avalanche morphology and propagation

- Avalanches often nucleate at a single interior stitch and propagate outward
- Positive events (ω > 0) propagate along the $-\pi/4$ diagonal; negative events along $+\pi/4$
- The spatial correlation function $C^\pm_\omega$ confirms diagonal propagation directions

This propagation is explained by the elastic response of the knit to a local perturbation: a local vorticity perturbation generates a stress field that is maximal along the $\pm\pi/4$ diagonals, triggering further slips in those directions (source: Poincloux_PRL_2018.pdf).

## Comparison to elastoplastic models

The knitted fabric fits the framework of **elastoplastic models** of soft amorphous solids:
- The fabric has a spatially distributed plastic threshold (determined by local friction)
- When global stress increases, regions near threshold yield first
- Yielding redistributes stress, potentially triggering further events (avalanche)
- The fabric does NOT flow or fail — connectivity is topologically locked

This makes knitted fabric an unusually clean model system for studying avalanche universality: it has topological order (no structural disorder) but still shows power-law statistics, isolating the role of distributed friction thresholds from structural disorder.

## Related pages

- [[knitted-fabrics]]
- [[knit-elasticity]]
- [[return-point-memory]]
- [[deformation]]
- [[stress-strain-curve]]
- [[poincloux-prl-2018]]
- [[poincloux-prx-2018]]
- [[yarn-contact]]
- [[grandgeorge-2021]]
- [[dresselhaus-2025]]
- [[physics-world-2019]]
