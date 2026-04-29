# Poincloux, Adda-Bedia & Lechenault — Geometry and Elasticity of a Knitted Fabric (PRX 2018)

**Summary**: First-principles mechanical model for stockinette fabric, deriving elastic response from yarn bending energy + topological constraints + yarn length conservation, validated against tensile experiments on nylon monofilament.

**Sources**: `raw/Poincloux_PRX_2018.pdf`, `raw/Poincloux_PRL_2018_Supplemental.pdf`

**Last updated**: 2026-04-13

---

## Citation

Poincloux, S., Adda-Bedia, M., & Lechenault, F. (2018). Geometry and elasticity of a knitted fabric. *Physical Review X*, **8**, 021075. DOI: 10.1103/PhysRevX.8.021075

## Key contributions

1. **First-principles model**: Derives the mechanical response of stockinette from yarn bending energy, conservation of total yarn length, and kinematic constraints from stitch topology — no phenomenological fitting.
2. **Geometric characterization**: High-resolution imaging of a $51 \times 51$ stitch nylon fabric under wale-direction stretching to measure stitch size fields $\langle c \rangle$ and $\langle w \rangle$.
3. **Homogeneous deformation model**: Explicit formula for force vs. strain; effective stretching modulus $\tilde{Y}$ as the single parameter.
4. **Inhomogeneous deformation model**: Lagrangian field theory for spatially varying deformation; predicts full displacement field without free parameters (once geometry is characterized).
5. **Poisson ratio**: Measured $\nu \approx 0.46$ — near-incompressible despite hollow structure.

## Model setup

A stockinette stitch is described by its course and wale dimensions $c$ and $w$. The fabric deformation field $\vec{c}(x,y)$ and $\vec{w}(x,y)$ are continuous vector fields. Key parameters:

- $c^* = 3.93$ mm, $w^* = 2.08$ mm (reference dimensions)
- $\delta = 0.86$ (yarn length asymmetry; machining parameter)
- $\beta = \delta(w^*/c^*)^2 \approx 0.24$ (bending energy asymmetry)
- $\tilde{Y}$: effective stretching modulus (fitted once from loading data)

## Elastic energy of a stitch

The bending elastic energy in the 2D approximation:

$$\mathcal{E}_b \approx \mathcal{E}_c + \mathcal{E}_w = \tilde{B}\left(\frac{1}{c} + \frac{\beta}{w}\right)$$

where $\tilde{B}$ is an effective bending modulus.

## Yarn length conservation

The average effective stitch length $\langle \ell \rangle = \langle c \rangle + \delta \langle w \rangle$ is conserved:

$$\langle c \rangle + \delta \langle w \rangle = \ell^* = c^* + \delta w^*$$

This couples course and wale deformations.

## Experiments

- **Material**: Nylon monofilament, 150 μm diameter, $51 \times 51$ stitch fabric on a single-bed machine
- **Measurement**: Force measured by dynamometer; stitch positions tracked by digital camera (high-resolution imaging)
- **Protocol**: Cyclic wale-direction stretching; fabric held at its top/lower rows, allowing lateral sliding

## Key results

- Stiffening behavior separated into two phases: low-variability (ε < 0) and stiffening (ε > 0) starting at reference configuration $L_w = L_w^0$
- Model predicts force-strain curve with $\tilde{Y}^\uparrow = 3.8 \times 10^{-2}$ J/m (loading) and $\tilde{Y}^\downarrow = 0.8 \times 10^{-2}$ J/m (unloading)
- Predicted displacement fields match experiment at small strains; deviations grow at ε > 15% due to scale separation breakdown (stitch size approaches yarn diameter)
- Catenary shape predicted and observed

## Relationship to PRL 2018

The elastic model derived here (continuous, homogeneous fabric description) is used in Poincloux PRL 2018 to predict the propagation direction of crackling avalanches (see [[crackling-dynamics]]).

## Related pages

- [[knit-elasticity]]
- [[wale-and-course]]
- [[constitutive-model]]
- [[crackling-dynamics]]
- [[poisson-ratio]]
- [[yarn]]
- [[stitch-types]]
- [[poincloux-prl-2018]]
