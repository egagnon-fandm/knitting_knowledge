# Stitch Topology

**Summary**: The topology of stitches — specifically the symmetry of yarn segments connecting neighboring entangled regions — is the primary determinant of a fabric's linear elastic response. Same-type stitch pairs (K-K or P-P) produce stiff "even" connectors; alternating pairs (K-P) produce soft "odd" connectors roughly 10× more compliant.

**Sources**: `raw/Singal_NatureComm_2024.pdf`, `raw/Poincloux_PRX_2018.pdf`

**Last updated**: 2026-04-13

---

## Topology as a mechanical knob

Knitted fabrics are composed of a rectangular lattice of slip knots. The two elementary stitches (K and P) are topologically identical — just related by a 180° rotation. But when combined into a full fabric, they produce emergent mechanical differences through the topology of the yarn that connects them.

From a knot-theory perspective, textiles can be studied as tangles in tori. The ordering of crossings within a knot can significantly impact its mechanical properties (source: Singal_NatureComm_2024.pdf, which cites Markande & Matsumoto 2020 — that paper is not yet ingested in this wiki).

## Even and odd connecting segments

The central insight (Singal 2024): each pair of neighboring stitches is joined by a connecting yarn segment whose symmetry determines its stiffness.

### Even symmetry (K-K or P-P)
Two identical stitches share a connector with **even** (mirror) symmetry. Under extension, this segment must **curve** to accommodate the deformation — it acts as a relatively stiff spring:

$$Y_\text{even} \sim \frac{180 B}{\lambda^3 (1 - \delta_\text{even})}$$

### Odd symmetry (K-P or P-K)
Alternating stitches share a connector with **odd** (rotational) symmetry. Under extension, this segment can **rotate** like a moment arm — it is roughly **10× softer**:

$$Y_\text{odd} \sim \frac{12 B}{\lambda^3 (1 - \delta_\text{odd})}$$

where $\lambda$ is the segment length, $B$ is the yarn bending modulus, and $\delta$ are geometry-dependent correction factors (source: Singal_NatureComm_2024.pdf).

## Symmetry map of the four fabrics

| Fabric | x (course) segments | y (wale) segments |
|---|---|---|
| Stockinette | Even | Even |
| Garter | Even | Odd |
| Rib | Odd | Even |
| Seed | Odd | Odd |

Note: a pair of identical stitches in the y-direction is stiffer than an equivalent pair in the x-direction, because there are **two** connecting yarn segments in parallel in the y-direction (source: Singal_NatureComm_2024.pdf).

## Reduced Symmetry (RS) model

Using the "rule of mixtures" from fiber composite theory, Singal 2024 builds an **effective elastic model** from:
- Stitch unit elasticity
- Connecting segments of appropriate symmetry acting as springs in series/parallel

This Reduced Symmetry model estimates Young's moduli for all four fabrics from geometric parameters and bending modulus alone — no free fitting parameters. It agrees closely with experiments, though is systematically slightly stiffer (source: Singal_NatureComm_2024.pdf).

## Entangled regions

The microstructure has two types of regions:
- **Entangled regions**: where yarn from different loops crosses and contacts — contact interactions dominate stiffness
- **Unconstrained regions**: connecting segments — enable extensibility

Changing the ordering of yarn in an entangled region changes the fabric's topology. The transition from low-stress (bending-dominated) to high-stress (contact-dominated) behavior corresponds to curvature localizing to these entangled regions as yarn straightens in between (source: Singal_NatureComm_2024.pdf).

## Cross-overs in simulation

In yarn-level simulations (see [[yarn-simulation]]), entangled regions are represented as **cross-overs** with defined parity (handedness). Parity $p \in \{0, 1\}$ corresponds to the two types of crossing — equivalent to the K/P distinction (source: notes_for_Tim.pdf).

## Related pages

- [[stitch-types]]
- [[knit-elasticity]]
- [[knitted-fabrics]]
- [[yarn-simulation]]
- [[singal-naturecomm-2024]]
