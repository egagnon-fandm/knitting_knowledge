# Knitted Fabrics

**Summary**: A knitted fabric is a 2D surface created by interlocking loops of yarn into a periodic network of stitches, whose mechanical properties are emergent from stitch topology rather than yarn composition.

**Sources**: `raw/Singal_NatureComm_2024.pdf`, `raw/Poincloux_PRX_2018.pdf`, `raw/Poincloux_PRL_2018.pdf`, `raw/Dresselhaus et al. - 2025 - Return point memory in knitted fabrics.pdf`, `raw/notes_for_Tim.pdf`, `raw/Knitting Science, Technology, Process and Materials.pdf`, `raw/Knit and stretch – Physics World.pdf`

**Last updated**: 2026-05-17

---

## What is a knitted fabric?

Knitting transforms yarn — a 1D material — into a 2D fabric by morphing it into a periodic pattern of self-crossing loops called **stitches**. Unlike weaving (where warp and weft threads are independent), knitted fabrics consist of a single continuous yarn per row, which interlocks with neighboring rows through topologically constrained contact points.

### Weft vs. warp knitting

**Weft knitting** (the focus of this wiki): yarn is fed in the width (crosswise) direction; one yarn can form an entire row of loops. Machines: V-bed flat knitting machines or circular knitting machines. Most garments and all research fabrics in this wiki are weft-knitted.

**Warp knitting**: yarn runs lengthwise in a zig-zag pattern; every needle receives its own yarn. Fabrics are dimensionally more stable but less extensible. Subtypes: Tricot, Raschel. Primarily used for technical textiles, lace, and geotextiles. (source: Jamshaid & Mishra 2024)

**Key distinction from weaving**: in woven fabrics, extension requires stretching or compressing the yarns themselves — elongation is limited to a few percent. In knitted fabrics, loops can unfurl and reorient geometrically, enabling strains of 100–300% without plastically deforming the yarn (source: Physics World 2019).

The fundamental building blocks are two stitches: the **knit stitch** (K) and the **purl stitch** (P), which are geometrically identical but related by a 180° rotation about the fabric's y-axis. By combining Ks and Ps in different patterns, one can produce fabrics with markedly different mechanical responses (source: Singal_NatureComm_2024.pdf).

## Knitted fabrics as mechanical metamaterials

A key insight: the elastic properties of a knitted fabric are **emergent** from stitch topology and cannot be attributed to the yarn alone. Stitch pattern and yarn properties are quasi-independent "knobs." This means:

- Choosing stitch pattern → programs local elastic response
- Works regardless of fiber composition (acrylic, cotton, wool, cashmere, bamboo all tested in Singal 2024)
- Can create seamless composites where different regions have different stiffnesses

This positions knitting as an **additive manufacturing technique** for mechanical metamaterials (source: Singal_NatureComm_2024.pdf).

## Key mechanical features

1. **Extreme extensibility**: A knit fabric can sustain strains of order 100% or more while the constituent yarn elongates by only a few percent. This originates from the topology of loops, not yarn elasticity.
2. **Anisotropy**: Most fabrics respond differently along the course (row) and wale (column) directions. See [[wale-and-course]].
3. **Strain stiffening**: After initial compliant extension (bending-dominated), the response stiffens sharply as yarn becomes taut (contact-dominated). See [[constitutive-model]].
4. **Hysteresis and memory**: Loading and unloading curves differ due to friction at yarn contacts. Fabrics exhibit **return point memory** under cyclic loading. See [[return-point-memory]].
5. **Crackling dynamics**: Under quasistatic stretching, stick-slip events at contact points generate an intermittent, avalanche-like mechanical response. See [[crackling-dynamics]].

## Topological protection

The connectivity (topology) of the stitch network is locked: stitches cannot exchange neighbors without cutting the yarn. This gives knitted fabrics **topologically protected structural order** — unlike granular materials or foams, structural rearrangement does not occur during normal deformation (source: Poincloux_PRL_2018.pdf).

## Applications

- Soft robotics and actuators
- Wearable electronics and strain sensors
- Medical bandages, surgical grafts, mesh implants
- Energy harvesting from human motion
- Engineered tissue scaffolds
- Architecture (tensile structural support)
- Therapeutic garments (see [[singal-naturecomm-2024]])

## Manufacturing and pre-tension

Fabrics knitted on industrial machines (V-bed, circular) are produced under tension. When the fabric is taken off the machine, it relaxes and adopts a reference state that depends on manufacturing tension. This **residual pre-tension** affects the reference geometry and must be accounted for in simulation (source: Ding et al. 2023, [[ding-2023]]). Experimentally, fabrics are typically left 24–48 hours to relax before mechanical testing (source: Jamshaid & Mishra 2024).

## Heterogeneous fabrics

Industrial garments routinely combine regions of different yarn or stitch pattern (e.g., to vary stiffness across a compression sleeve). Du Pasquier et al. 2025 showed that **material transitions obey simple mechanical analogies** (source: Chen_2025_Multilevel_Mechanical_Modeling_Weft_Knit.pdf §4):

- **Parallel configuration** (interface parallel to load): overall response = weighted average of the two homogeneous regions. The interface does not introduce additional compliance.
- **Series configuration** (interface perpendicular to load): each region deforms according to its own homogeneous behavior; the interface displacement is tracked by DIC.

This means a heterogeneous garment can be modeled as a patchwork of homogeneous HGO elements joined by spring-in-series/parallel constraints — no mesoscale interface model is needed. Demonstrated by optimizing a compression sleeve to deliver spatially uniform pressure across a variable-circumference arm (see [[du-pasquier-2025]]).

## Related pages

- [[stitch-types]]
- [[yarn]]
- [[wale-and-course]]
- [[knit-elasticity]]
- [[stitch-topology]]
- [[crackling-dynamics]]
- [[return-point-memory]]
- [[constitutive-model]]
- [[yarn-simulation]]
- [[jamshaid-mishra-2024]]
- [[physics-world-2019]]
- [[ding-2023]]
- [[dresselhaus-2025]]
- [[du-pasquier-2025]]
- [[hgo-strain-energy]]
