# Wiki Log

Append-only record of all operations.

---

## 2026-04-13 — Initial wiki creation

**Sources ingested** (all sources in `raw/` at time of writing):

- `raw/Strain.md` (Wikipedia — Strain mechanics)
- `raw/Stress_strain_curve.md` (Wikipedia — Stress-strain curve)
- `raw/Deformation.md` (Wikipedia — Deformation physics)
- `raw/Poisson_ratio.md` (Wikipedia — Poisson's ratio)
- `raw/Stress_strain_analysis.md` (Wikipedia — Stress-strain analysis)
- `raw/notes_for_Tim.pdf` (Dimitriyev 2019 — Fabric simulation notes)
- `raw/Poincloux_PRX_2018.pdf` (Poincloux et al. 2018 — Geometry and Elasticity of a Knitted Fabric)
- `raw/Poincloux_PRL_2018.pdf` (Poincloux et al. 2018 — Crackling Dynamics)
- `raw/Poincloux_PRL_2018_Supplemental.pdf` (Supplemental to PRL 2018)
- `raw/Singal_NatureComm_2024.pdf` (Singal, Dimitriyev et al. 2024 — Programming Mechanics)
- `raw/Singal_NatureComm_2024_Suppl.pdf` (Supplemental to NatureComm 2024)
- `raw/Dresselhaus et al. - 2025 - Return point memory in knitted fabrics.pdf`

**PDFs present but not yet fully read** (large or not prioritized in initial pass):
- `raw/Cornelissen_Analysis_of_yarn_bending_behaviour_2009.pdf`
- `raw/Knit and stretch – Physics World.pdf`
- `raw/Knitting Science, Technology, Process and Materials.pdf`
- `raw/Unravelling the Mechanics of Knitted Fabrics Through.pdf`

**Pages created** (19 total):

| Page | Description |
|---|---|
| `strain.md` | Strain mechanics background |
| `stress-strain-curve.md` | Stress-strain curves background |
| `deformation.md` | Deformation physics background |
| `poisson-ratio.md` | Poisson's ratio background |
| `knitted-fabrics.md` | Overview of knitted fabrics as metamaterials |
| `stitch-types.md` | K, P stitches; stockinette, garter, rib, seed |
| `yarn.md` | Yarn structure and mechanical properties |
| `wale-and-course.md` | Principal fabric directions and stitch geometry |
| `knit-elasticity.md` | Emergent elastic response of knitted fabrics |
| `stitch-topology.md` | Even/odd segment symmetry framework |
| `constitutive-model.md` | Full stress-strain constitutive relation |
| `crackling-dynamics.md` | Stick-slip avalanches and crackling noise |
| `return-point-memory.md` | Cyclic hysteresis and return point memory |
| `yarn-simulation.md` | Bézier curve simulation framework |
| `poincloux-prx-2018.md` | Source summary: PRX 2018 |
| `poincloux-prl-2018.md` | Source summary: PRL 2018 |
| `singal-naturecomm-2024.md` | Source summary: NatureComm 2024 |
| `dimitriyev-notes-2019.md` | Source summary: simulation notes |
| `dresselhaus-2025.md` | Source summary: return point memory 2025 |

**Pages still to be created** (awaiting full reading of remaining PDFs):
- Pages from Cornelissen 2009 (yarn bending), Physics World article, Knitting Science textbook, "Unravelling" paper

---

## 2026-04-13 — Second ingest session

**Sources ingested** (four previously deferred PDFs):

- `raw/Knit and stretch – Physics World.pdf` (Poincloux 2019 — popular science article)
- `raw/Cornelissen_Analysis_of_yarn_bending_behaviour_2009.pdf` (Cornelissen & Akkerman 2009 — yarn bending)
- `raw/Unravelling the Mechanics of Knitted Fabrics Through.pdf` (Ding, Sanchez, Bertoldi, Rycroft 2023 — B-spline dynamical simulation)
- `raw/Knitting Science, Technology, Process and Materials.pdf` (Jamshaid & Mishra 2024 — textbook; read Introduction and Mechanics chapters)

**New pages created** (4):

| Page | Description |
|---|---|
| `ding-2023.md` | Source summary: B-spline dynamical simulation; pre-tension; yarn rearrangement |
| `cornelissen-2009.md` | Source summary: yarn bending; EBT vs TBT; cantilever test; intra-yarn friction |
| `jamshaid-mishra-2024.md` | Source summary: textbook; weft vs warp; jersey/rib/interlock mechanics; terminology |
| `physics-world-2019.md` | Source summary: popular science; knit vs weave; two-regime response; crackling |

**Pages updated** (7):

| Page | Changes |
|---|---|
| `yarn-simulation.md` | Added Ding 2023 B-spline framework; comparison table of both simulation approaches |
| `yarn.md` | Added cantilever bending protocol; EBT formula; multi-filament friction softening; extensible vs inextensible distinction; Cornelissen and Ding cross-references |
| `stitch-types.md` | Added interlock fabric description (from textbook) |
| `wale-and-course.md` | Added textile measurement conventions (CPI, WPI, GSM, stitch length, machine gauge) |
| `knitted-fabrics.md` | Added weft vs warp distinction; manufacturing pre-tension section; new source references |
| `index.md` | Added 4 new source summary pages |
| `log.md` | This entry |

---

## 2026-04-17 — Fifth ingest session

**Sources ingested** (Chapter II of previously noted reference):

- `raw/Landau and Lifshitz - Theory of Elasticity.pdf` — Chapter II only (§11–§21, book pages 38–86)

**New pages created** (1):

| Page | Description |
|---|---|
| `landau-chap2.md` | Source summary: thin plate bending (biharmonic D△²ζ=P); Föppl–von Kármán large-deflection equations; shell mechanics and buckling; rod torsion (C=½μπR⁴) and bending (EI=¼EπR⁴); stretched-beam equation; Euler buckling |

**Pages updated** (2):

| Page | Changes |
|---|---|
| `index.md` | Added landau-chap2 under source summaries; updated L&L reference note |
| `log.md` | This entry |

---

## 2026-04-16 — Third ingest session

**Sources ingested** (three new files in `raw/`):

- `raw/Chap7.pdf` (Likharev — LibreTexts Ch. 7 "Deformations and Elasticity"; CC BY-NC-SA)
- `raw/Hooke_law.md` (Wikipedia — Hooke's Law)
- `raw/Work_hardening.md` (Wikipedia — Work Hardening)

**New pages created** (3):

| Page | Description |
|---|---|
| `likharev-chap7.md` | Source summary: continuum mechanics textbook; strain/stress tensors; tensor Hooke's law; rod bending; elastic waves |
| `hookes-law.md` | Concept: linear elasticity; tensor form; limits for soft/rubber-like materials; orthotropy |
| `work-hardening.md` | Concept: Hollomon/Ludwik power-law hardening; dislocation mechanism; contrast with fabric cycling |

**Pages updated** (5):

| Page | Changes |
|---|---|
| `constitutive-model.md` | Added tensor mechanics background section; notes on why isotropic Hooke's law doesn't apply to fabrics; links to hookes-law and likharev-chap7 |
| `stress-strain-curve.md` | Added Hollomon's law reference in strain hardening section; links to work-hardening and hookes-law |
| `return-point-memory.md` | Added contrast section: work hardening vs. RPM (softening not hardening); link to work-hardening |
| `yarn.md` | Added non-Hookean behavior section noting yarn is rubber-like |
| `index.md` | Added hookes-law, work-hardening (background mechanics), likharev-chap7 (source summary) |

---

## 2026-04-20 — Sixth ingest session

**Sources ingested**:

- `raw/Coleman et al. - 1993 - On the dynamics of rods in the theory of Kirchhoff.pdf` (Coleman, Dill, Lembo, Lu & Tobias 1993 — Arch. Rational Mech. Anal. 121, 339–359)

**New pages created** (2):

| Page | Description |
|---|---|
| `coleman-1993.md` | Source summary: Kirchhoff-Clebsch rod dynamics; constitutive equations; five conservation laws including twist impulse; solitary wave crease solution $k \sim \operatorname{sech}$ |
| `kirchhoff-rod.md` | Concept: inextensible director-frame rod model; curvature vector; bending/torsion rigidity; elastic energy; solitary wave as crease model |

**Pages updated** (4):

| Page | Changes |
|---|---|
| `yarn-simulation.md` | Added Coleman 1993 as theoretical source; cited $B=J$ justification from Kirchhoff rod ratio $\Omega = (1+\nu)^{-1}$; added kirchhoff-rod and coleman-1993 to related pages |
| `landau-chap2.md` | Added kirchhoff-rod and coleman-1993 to related pages |
| `index.md` | Added kirchhoff-rod (simulation methods section) and coleman-1993 (source summaries section) |
| `log.md` | This entry |

---

## 2026-04-21 — Seventh ingest session

**Sources ingested**:

- `raw/Nonlinear_Problems_of_Elasticity.pdf` — Stuart S. Antman, *Nonlinear Problems of Elasticity*, 2nd ed. (Springer, 2005). Chapter 4, Sections 1–2 only (book pp. 95–110).

**New pages created** (2):

| Page | Description |
|---|---|
| `antman-chap4.md` | Source summary: planar Cosserat rod theory; strain variables ν,η,μ; equilibrium equations; monotonicity condition; stored-energy function; boundary conditions; buckling phase portrait; Euler elastica |
| `cosserat-rod.md` | Concept: geometrically exact extensible+shearable rod; director field; three strain variables; constitutive requirements; hierarchy of rod models |

**Pages updated** (4):

| Page | Changes |
|---|---|
| `kirchhoff-rod.md` | Added paragraph noting Kirchhoff as special case of Cosserat (ν=1, η=0); N and H become Lagrange multipliers; links to cosserat-rod and antman-chap4 |
| `constitutive-model.md` | Added "Rod constitutive equations" section: (N,H,M) vs (ν,η,μ); monotonicity condition; stored-energy W; elastica as special case; links to cosserat-rod and antman-chap4 |
| `index.md` | Added cosserat-rod (simulation methods), antman-chap4 (source summaries), Antman partial-ingest note |
| `log.md` | This entry |

---

## 2026-04-29 — Tutorials created

Three tutorials written from scratch for college-level audience (general physics/maths background, no prior knitting knowledge).

**Tutorials created** (3):

| File | Description |
|---|---|
| `tutorials/stress.md` | Cauchy stress tensor; normal vs shear stress; equilibrium; yield stress; force-per-width convention; 3 worked problems |
| `tutorials/strain.md` | Engineering strain, stretch ratio, true strain; strain tensor; Poisson ratio; yarn-length conservation; 3 worked problems |
| `tutorials/stress-strain-curves.md` | Reading the curve; ductile vs J-shaped; two-regime constitutive model; anisotropy; hysteresis and return point memory; 3 worked problems |

---

## 2026-04-29 — Wiki lint and repair

No new sources ingested. Lint audit found and fixed 13 issues across 19 files.

**New page created** (1):

| Page | Description |
|---|---|
| `stress.md` | Concept: Cauchy stress tensor; normal/shear stress; yield stress; force-per-width convention in knitting |

**Pages updated** (18):

| Page | Fix |
|---|---|
| `index.md` | Added stress.md to Background mechanics |
| `strain.md` | Added [[stress]] and [[poincloux-prx-2018]] to Related pages |
| `deformation.md` | Added [[stress]] and [[witten-2007]] to Related pages |
| `hookes-law.md` | Added [[stress]] to Related pages |
| `likharev-chap7.md` | Added [[stress]] to Related pages |
| `constitutive-model.md` | Added [[witten-2007]] to Related pages |
| `yarn.md` | Added [[jamshaid-mishra-2024]] to Related pages |
| `poisson-ratio.md` | Added [[singal-naturecomm-2024]] to Related pages |
| `wale-and-course.md` | Added [[dimitriyev-notes-2019]] to Related pages |
| `singal-naturecomm-2024.md` | Added [[ding-2023]] to Related pages; clarified rib 180% figure vs. J&M 200% upper limit |
| `jamshaid-mishra-2024.md` | Clarified rib 200% as upper limit vs. Singal same-stress measurement |
| `crackling-dynamics.md` | Added [[dresselhaus-2025]] and [[physics-world-2019]] to Related pages |
| `knitted-fabrics.md` | Added [[dresselhaus-2025]] to Related pages |
| `knit-elasticity.md` | Added [[physics-world-2019]] to Related pages |
| `ding-2023.md` | Clarified "warp direction" → "warp / wale / y direction" and "Weft direction" → "Weft (course / x) direction" |
| `work-hardening.md` | Expanded Mullins effect mention with definition; flagged as needing verification |
| `stitch-topology.md` | Clarified Markande & Matsumoto 2020 as secondary citation; noted source not yet ingested |
| `log.md` | This entry |

---

## 2026-04-30 — Two new tutorials created

No new sources ingested.

**Tutorials created** (2):

| File | Description |
|---|---|
| `tutorials/yarn-bending-energy.md` | Bending energy formula; bending rigidity $B = EI$; cantilever measurement; multi-filament softening; role in low-stress knit regime; 3 worked problems |
| `tutorials/yarn-compression-energy.md` | Contact geometry at stitch crossings; Hertz contact model; two-regime fabric mechanics; capstan friction and its consequences (hysteresis, crackling, return point memory); 3 worked problems |

---

## 2026-04-29 — New concept page: tangent modulus

No new sources ingested.

**New page created** (1):

| Page | Description |
|---|---|
| `tangent-modulus.md` | Concept: dσ/dε as a function of strain; contrast with Young's modulus and secant modulus; formula for the knitting constitutive model; divergence in strain-stiffening regime; hysteresis implications |

**Pages updated** (2):

| Page | Changes |
|---|---|
| `index.md` | Added tangent-modulus.md under Background mechanics |
| `log.md` | This entry |

---

## 2026-04-17 — Fourth ingest session

**Sources ingested** (4 PDFs newly identified in `raw/`):

- `raw/Grandgeorge et al. - 2021 - Mechanics of two filaments in tight orthogonal con.pdf` (PNAS 2021, EPFL Reis group)
- `raw/Kaldor et al. - Simulating Knitted Cloth at the Yarn Level.pdf` (ACM SIGGRAPH 2008, Cornell)
- `raw/RevModPhys.79.643.pdf` (Witten 2007 — Stress focusing in elastic sheets)
- `raw/Landau and Lifshitz - Theory of Elasticity.pdf` (L&L Vol. 7) — noted as reference only; not fully ingested

**New pages created** (4):

| Page | Description |
|---|---|
| `grandgeorge-2021.md` | Source summary: elastic orthogonal clasp; diamond contact region; friction capstan; relevance to knitting |
| `yarn-contact.md` | Concept: yarn-yarn contact mechanics; orthogonal clasp; Hertz vs. clasp models; friction basis of hysterons |
| `kaldor-2008.md` | Source summary: SIGGRAPH yarn-level simulation; B-spline/ICD; knit patterns from topology |
| `witten-2007.md` | Source summary: stress focusing in elastic sheets; d-cones; ridges; Föppl–von Kármán |

**Pages updated** (5):

| Page | Changes |
|---|---|
| `yarn-simulation.md` | Added Kaldor 2008 as predecessor; expanded comparison table to three frameworks |
| `return-point-memory.md` | Added orthogonal clasp as physical basis of hysterons; links to yarn-contact and grandgeorge-2021 |
| `crackling-dynamics.md` | Added orthogonal clasp identification of stick-slip mechanism; links to yarn-contact and grandgeorge-2021 |
| `index.md` | Added yarn-contact (mechanics section), kaldor-2008, grandgeorge-2021, witten-2007, L&L reference |
| `log.md` | This entry |
