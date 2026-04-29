# Hooke's Law

**Summary**: Hooke's law states that stress is proportional to strain in the linear elastic regime, expressed in full generality as σ = c:ε (stiffness tensor). It fails for large deformations and for soft materials such as rubbers and yarns, which are non-Hookean.

**Sources**: `raw/Hooke_law.md` (Wikipedia), `raw/Chap7.pdf` (Likharev)

**Last updated**: 2026-04-16

---

## Scalar form

For a spring or 1D elastic body:

$$F = kx \qquad \text{(restoring force = stiffness × displacement)}$$

For a uniform rod of cross-section A and length L, this generalizes to:

$$\sigma = E\varepsilon, \qquad \varepsilon = \frac{\Delta L}{L}$$

where E is Young's modulus. The spring constant k = EA/L.

## Tensor form

For a 3D elastic medium, stress and strain are each second-rank tensors. Hooke's law becomes:

$$\sigma_{ij} = \sum_{k,l} c_{ijkl}\,\varepsilon_{kl}$$

where **c** is the **stiffness tensor** (fourth-rank, 81 → 21 independent components due to symmetry). The inverse relation uses the **compliance tensor** **s**: ε = s:σ.

### Isotropic materials

For isotropic media only two constants are needed, the bulk modulus K and shear modulus μ (= G):

$$\sigma_{jj'} = 2\mu\left(s_{jj'} - \tfrac{1}{3}\delta_{jj'}\,\text{Tr}(\mathbf{s})\right) + 3K\left(\tfrac{1}{3}\delta_{jj'}\,\text{Tr}(\mathbf{s})\right)$$

Equivalently expressed via **Young's modulus E** and **Poisson's ratio ν**:

$$\varepsilon_{ij} = \frac{1}{E}\bigl(\sigma_{ij} - \nu(\text{Tr}(\boldsymbol{\sigma})\delta_{ij} - \sigma_{ij})\bigr)$$

Conversion formulas: $E = 9K\mu/(3K+\mu)$, $\nu = (3K-2\mu)/(2(3K+\mu))$.

### Orthotropic materials

Knitted fabrics are orthotropic (different stiffness along wale vs. course). Hooke's law for orthorhombic symmetry has 9 independent constants: three Young's moduli (E_x, E_y, E_z), three shear moduli (G_xy, G_yz, G_zx), and three Poisson's ratios. In Voigt notation this gives a 6×6 compliance matrix (source: Hooke_law.md).

---

## Limits of validity

Hooke's law is only valid in the **linear elastic regime** (small strains, below the yield point or plasticity threshold):

- **Steel**: Hookean throughout its elastic range (below ~0.1% strain)
- **Aluminium**: Hookean only for a limited portion of the elastic range
- **Rubber**: non-Hookean — its elasticity is stress-dependent and sensitive to temperature and loading rate (source: Hooke_law.md)
- **Yarn**: non-Hookean — behaves like rubber; measured response is nonlinear even at small fabric strains

For large deformations, generalized models are used:
- **Neo-Hookean solid**: simplest large-deformation extension (one additional parameter)
- **Mooney-Rivlin solid**: two-parameter model for rubber-like materials

---

## Connection to knitted fabric models

Knitted fabrics violate Hooke's law in two distinct ways:

1. **Geometric nonlinearity at low stress**: the stitch acts as a mechanism (yarn bends and rotates freely) so the effective stiffness comes from bending and contact energies, not from a simple modulus. The linear regime slope Y in [[constitutive-model]] is not a material Hookean constant but a structural quantity.

2. **Strain stiffening at high stress**: the high-stress term ~β(1−αε)^{−2} in [[constitutive-model]] is strongly non-Hookean — stress diverges as yarn segments become fully taut.

For the linear continuum mechanics backdrop used in the analytical models, see [[likharev-chap7]].

---

## Related pages

- [[stress]]
- [[constitutive-model]]
- [[stress-strain-curve]]
- [[deformation]]
- [[strain]]
- [[poisson-ratio]]
- [[yarn]]
- [[likharev-chap7]]
