# Return Point Memory

**Summary**: Knitted fabrics subjected to cyclic uniaxial loading exhibit return point memory — they "remember" the maximum strain previously experienced, with subsequent loading curves rejoining the previous unloading curve at that strain. This rate-independent hysteresis is modeled by a Preisach framework where yarn contacts act as bistable hysterons.

**Sources**: `raw/Dresselhaus et al. - 2025 - Return point memory in knitted fabrics.pdf`

**Last updated**: 2026-04-16

---

## What is return point memory?

Return point memory (RPM) is a property of materials subjected to cyclic input (magnetization, stress, deformation) where the response at a given input value depends only on the **maximum value previously experienced**, not the full history. It was first described in ferromagnets (Preisach 1935) and has been observed in:
- Anti-ferromagnets
- Sheared amorphous solids
- Unfolded crumpled sheets
- Knitted fabrics (Dresselhaus et al. 2025)

## Experimental observations

Dresselhaus et al. (2025) performed cyclic uniaxial stress experiments on a ribbed (acrylic fingering-weight yarn) knitted fabric using an Instron universal testing machine.

**Key findings:**
1. **Substantial hysteresis**: Loading and unloading curves differ significantly at all tested strain rates spanning 2 orders of magnitude.
2. **Rate independence**: The behavior is the same at extension rates $\Delta = 0.025, 0.25, 2.5$ mm/s — memory is non-local in time, not a viscous effect.
3. **Return point property**: After cycling to strain $\varepsilon_1$ and unloading, subsequent loading to $\varepsilon_1$ rejoins the prior unloading curve. This is learned in a single cycle.
4. **Congruency**: Nested hysteresis loops between two intermediate strains $\varepsilon_1 < \varepsilon_2$ are determined solely by the return point $\varepsilon_\text{max}$ — not by the intermediate strains themselves.
5. **Wiping out**: Loading to a new maximum strain $\varepsilon_2 > \varepsilon_1$ creates a new return point B and wipes all hysteresis loops below $\varepsilon_2$ (source: Dresselhaus_2025.pdf).

## Physical mechanism: yarn contacts as hysterons (orthogonal clasps)

The elementary mechanism is the yarn-yarn contact in entangled regions of the stitch structure. Each contact is bistable:
- **Loading**: compressed radially; resists deformation with full strength
- **Unloading**: compressed yarn has been deformed; does not resist unloading with the same strength

These contacts play the role of **hysterons** in the Preisach model — bistable elements that switch irreversibly between two states when their threshold is crossed.

The physical structure of each contact is that of an **elastic orthogonal clasp** (Grandgeorge et al. 2021): two elastic tubes meeting in near-orthogonal contact, with a diamond-shaped contact region and a friction-induced tension ratio. The capstan-like asymmetry between loading (tension builds) and unloading (tension releases at a different threshold) is the microscopic basis for bistability. See [[yarn-contact]] and [[grandgeorge-2021]].

## Preisach model

The Preisach model (originally developed for ferromagnetic hysteresis) is an ensemble of non-interacting hysterons with a distribution of thresholds. For knitted fabrics, the stress is written as:

$$\sigma(\varepsilon[t], \varepsilon_t, \varepsilon_\text{max}; \alpha, \beta) = \iint_{\alpha \geq \beta} \mu(\alpha, \beta, \varepsilon_t, \varepsilon_\text{max}) \cdot s(\varepsilon[t], \varepsilon_t, \varepsilon_\text{max}; \alpha', \beta') \, d\alpha' \, d\beta'$$

where $\mu$ is the Preisach density function and $s$ is the relay function for each hysteron.

An extended version incorporating:
- **Non-local memory** (dependence on $\varepsilon_\text{max}$)
- **Wiping-out property**
- **Congruency**

reproduces all experimental observations. The total strain is decomposed as $\varepsilon = \varepsilon_e + \varepsilon_t$ (elastic + entanglement components); stress is proportional to elastic strain $\sigma = E \varepsilon_e$ (source: Dresselhaus_2025.pdf).

## Implications

- Memory in knitted fabrics is **non-local in time** and **rate-independent** — distinct from viscoelasticity or plasticity
- The spatial symmetries of stitches constrain the tensorial properties of the hysteresis (anomalous tensors may arise in wallpaper-group fabrics)
- RPM could in principle be engineered: varying yarn tension during fabrication changes the hysteron interactions and thus the memory landscape
- The results extend beyond knitting to other loop-based textiles (crochet, woven fabrics, knotted materials) and to colloidal/biological systems where entangled contacts play analogous roles

## Contrast with work hardening

In metals, repeated plastic cycling increases yield strength ([[work-hardening]]). In knitted fabrics the direction is reversed: the fabric softens and settles after the first load cycle, with subsequent cycles following the Preisach return-point pattern rather than stiffening. The underlying mechanism is also different — friction and contact rearrangement rather than dislocation accumulation.

## Related pages

- [[knitted-fabrics]]
- [[crackling-dynamics]]
- [[stress-strain-curve]]
- [[knit-elasticity]]
- [[stitch-topology]]
- [[dresselhaus-2025]]
- [[work-hardening]]
- [[yarn-contact]]
- [[grandgeorge-2021]]
