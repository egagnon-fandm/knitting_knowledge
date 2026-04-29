# Deformation

**Summary**: Deformation is the change in shape or size of a body. It is classified as elastic (reversible) or plastic (permanent), and quantified via displacement fields and the deformation gradient tensor.

**Sources**: `raw/Deformation.md` (Wikipedia)

**Last updated**: 2026-04-13

---

## Elastic vs. plastic deformation

- **Elastic deformation**: Recoverable — the body returns to its original configuration when stress is removed. Governed by a compliance tensor.
- **Plastic deformation**: Permanent — occurs once stress exceeds the **yield stress** (elastic limit). Results from slip or dislocation mechanisms.
- **Viscous deformation**: The irreversible component of viscoelastic behavior.

For knitted fabrics, the distinction is subtle: the fabric recovers its shape elastically, but friction at yarn contacts introduces **irreversible stick-slip events** that appear plastic at the stitch scale. See [[crackling-dynamics]].

## Displacement field and deformation gradient

The deformation gradient tensor $\mathbf{F} = \nabla_\mathbf{X} \mathbf{x}$ relates positions in the reference (undeformed) configuration $\mathbf{X}$ to the deformed configuration $\mathbf{x}$. [[Strain]] measures are derived from $\mathbf{F}$.

## Homogeneous (affine) deformation

A deformation is **affine** (homogeneous) if $\mathbf{x} = \mathbf{F}(t) \cdot \mathbf{X} + \mathbf{c}(t)$ — the same linear transformation applies everywhere. Knitted fabrics under modest strains deform approximately affinely in the bulk, but show non-affine displacements near boundaries and at slip events. The **non-affine displacement field** is the key observable in crackling dynamics experiments (source: Poincloux PRL 2018).

## Plane deformation and isochoric deformation

- **Plane strain**: deformation confined to a plane — relevant for fabric mechanics where thickness changes are secondary.
- **Isochoric** (volume-preserving): det(**F**) = 1, equivalent to $\lambda_1 \lambda_2 = 1$ in 2D. Knitted stockinette has an effective [[poisson-ratio]] of ~0.46, close to but not quite incompressible (source: Poincloux PRX 2018).

## Related pages

- [[strain]]
- [[stress]]
- [[stress-strain-curve]]
- [[poisson-ratio]]
- [[crackling-dynamics]]
- [[knit-elasticity]]
- [[witten-2007]]
