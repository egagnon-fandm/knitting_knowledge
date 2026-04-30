# Wiki Index

Knowledge base for research on knitted, woven, and crafted materials.

---

## Background mechanics

- [Stress](stress.md) — force per unit area; Cauchy stress tensor; yield stress; force-per-width convention in knitting
- [Strain](strain.md) — dimensionless measure of deformation; engineering strain, stretch ratio, strain tensor
- [Stress-strain curve](stress-strain-curve.md) — relationship between applied stress and resulting strain; linear elastic, strain-stiffening, hysteresis
- [Deformation](deformation.md) — elastic vs. plastic, affine/non-affine, displacement gradient tensor
- [Poisson's ratio](poisson-ratio.md) — transverse-to-axial strain ratio; ~0.46 for stockinette
- [Hooke's law](hookes-law.md) — linear elasticity; tensor form; limits for rubber/yarn (non-Hookean); neo-Hookean extensions
- [Tangent modulus](tangent-modulus.md) — dσ/dε at a given strain; contrast with Young's modulus and secant modulus; diverges in strain-stiffening regime
- [Work hardening](work-hardening.md) — yield-strength increase from plastic deformation; Hollomon's law; contrast with knitted fabric cycling

## Knitting fundamentals

- [Knitted fabrics](knitted-fabrics.md) — overview; knits as mechanical metamaterials; extensibility, anisotropy, topological protection
- [Stitch types](stitch-types.md) — knit (K) and purl (P) stitches; stockinette, garter, rib, seed; even/odd segment symmetry
- [Yarn](yarn.md) — hierarchical fiber structure; bending modulus, compressibility, loop length; inextensibility assumption
- [Wale and course](wale-and-course.md) — two principal directions; stitch dimensions c and w; catenary geometry; unit cell

## Mechanics of knitted fabrics

- [Knit elasticity](knit-elasticity.md) — emergent Young's modulus; two regimes (bending vs. contact); effective stretching modulus; normalized rigidity
- [Stitch topology](stitch-topology.md) — even/odd connecting yarn segments; Reduced Symmetry model; entangled regions; knot theory link
- [Constitutive model](constitutive-model.md) — full stress-strain relation σ(ε) = Yε + β(1−αε)⁻²; first-principles Lagrangian; FEA application
- [Crackling dynamics](crackling-dynamics.md) — stick-slip avalanches; power-law distributions (~−3/2); vorticity and deviatoric strain fields; propagation along diagonals
- [Return point memory](return-point-memory.md) — RPM under cyclic loading; rate-independent hysteresis; Preisach model; yarn contacts as hysterons
- [Yarn contact mechanics](yarn-contact.md) — orthogonal clasp geometry; diamond contact region; friction capstan; physical basis of hysterons

## Simulation methods

- [Yarn simulation](yarn-simulation.md) — Bézier, B-spline, and yarn-level frameworks; comparison table; Kaldor/Dimitriyev/Ding
- [Kirchhoff rod](kirchhoff-rod.md) — inextensible director-frame rod model; bending/torsion rigidity; solitary wave (crease) solution
- [Cosserat rod](cosserat-rod.md) — geometrically exact extensible+shearable rod; stretch ν, shear η, bending μ; generalizes Kirchhoff; monotonicity condition

## Source summaries

- [Poincloux PRX 2018](poincloux-prx-2018.md) — geometry and elasticity of stockinette; first-principles model; Poisson ratio 0.46
- [Poincloux PRL 2018](poincloux-prl-2018.md) — crackling dynamics; avalanche statistics; power-law exponent −3/2
- [Singal NatureComm 2024](singal-naturecomm-2024.md) — stitch-by-stitch mechanics; four fabrics; even/odd symmetry; constitutive model; therapeutic glove
- [Dimitriyev notes 2019](dimitriyev-notes-2019.md) — fabric simulation framework (Bézier, energy minimization); stockinette unit cell
- [Dresselhaus 2025](dresselhaus-2025.md) — return point memory; cyclic hysteresis; Preisach model; yarn contacts as hysterons
- [Ding et al. 2023](ding-2023.md) — B-spline dynamical simulation; pre-tension; friction; yarn rearrangement as anisotropy origin; design space
- [Cornelissen & Akkerman 2009](cornelissen-2009.md) — yarn bending; EBT vs TBT; cantilever test; intra-yarn friction effect
- [Jamshaid & Mishra 2024](jamshaid-mishra-2024.md) — textbook overview; weft vs warp; terminology; mechanics of jersey, rib, interlock
- [Physics World 2019](physics-world-2019.md) — popular science; knit vs weave; loop deformation mechanism; crackling
- [Likharev Chapter 7](likharev-chap7.md) — continuum mechanics textbook; strain/stress tensors; tensor Hooke's law; rod bending/torsion; elastic waves
- [Grandgeorge et al. 2021](grandgeorge-2021.md) — elastic orthogonal clasp; diamond contact region; friction capstan; yarn crossing mechanics
- [Kaldor et al. 2008](kaldor-2008.md) — SIGGRAPH yarn-level simulation; B-spline tubes; ICD integrator; garter/stockinette/rib emergence
- [Witten 2007](witten-2007.md) — stress focusing in elastic sheets; d-cones; stretching ridges; Föppl–von Kármán equations
- [Landau & Lifshitz Ch. II](landau-chap2.md) — equilibrium of rods and plates; biharmonic plate equation; Föppl–von Kármán large deflections; shell mechanics; rod bending/torsion rigidity; Euler buckling
- [Coleman et al. 1993](coleman-1993.md) — Kirchhoff-Clebsch rod dynamics; 3D bending+torsion; conservation laws; solitary wave crease solution
- [Antman Ch. 4](antman-chap4.md) — planar Cosserat rod theory; strain variables ν,η,μ; equilibrium equations; buckling phase portrait; Euler elastica
- Landau & Lifshitz — Theory of Elasticity (`raw/Landau and Lifshitz - Theory of Elasticity.pdf`) — full text; Ch. II ingested; remaining chapters (I, III–IX) not yet ingested
- Antman — Nonlinear Problems of Elasticity (`raw/Nonlinear_Problems_of_Elasticity.pdf`) — full text; Ch. 4 §§1–2 ingested; remaining sections and chapters not yet ingested
