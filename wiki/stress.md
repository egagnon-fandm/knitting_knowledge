# Stress

**Summary**: Stress is the internal force per unit area within a deformable body — the continuum-mechanics concept conjugate to [[strain]]. It is described by the Cauchy stress tensor, with normal components (tension/compression) and shear components.

**Sources**: `raw/Chap7.pdf` (Likharev), `raw/Landau and Lifshitz - Theory of Elasticity.pdf`, `raw/Singal_NatureComm_2024.pdf`

**Last updated**: 2026-05-03

---

## Definition

Stress quantifies how forces are transmitted through a material at a point. For a surface element with outward unit normal $\hat{n}$, the **traction** (contact force per unit area) is:

$$\mathbf{t} = \boldsymbol{\sigma} \cdot \hat{n}$$

where $\boldsymbol{\sigma}$ is the **Cauchy stress tensor** — a symmetric second-rank tensor. Units: Pa = N/m².

## Normal and shear stress

The stress tensor has two physically distinct contributions:

- **Normal stress** $\sigma_{nn}$: force per area perpendicular to the surface. Positive = tension, negative = compression. Changes the volume of an element.
- **Shear stress** $\sigma_{nt}$: force per area tangential to the surface. Distorts shape without changing volume.

In a Cartesian frame, each entry $\sigma_{jj'}$ encodes two pieces of information:

- The **second index $j'$** identifies the face being examined — the surface whose outward normal points in the $j'$-direction.
- The **first index $j$** identifies the direction of the force per unit area acting on that face.

$$\boldsymbol{\sigma} = \begin{pmatrix} \sigma_{xx} & \sigma_{xy} & \sigma_{xz} \\ \sigma_{xy} & \sigma_{yy} & \sigma_{yz} \\ \sigma_{xz} & \sigma_{yz} & \sigma_{zz} \end{pmatrix}$$

**Same indices ($j = j'$, diagonal entries)**: the force is perpendicular to the face — pure tension ($> 0$) or compression ($< 0$) along that axis. The three diagonal entries $\sigma_{xx}, \sigma_{yy}, \sigma_{zz}$ describe independent stretching or squeezing along each axis.

**Different indices ($j \neq j'$, off-diagonal entries)**: the force is parallel to the face — shear. $\sigma_{xy}$ is the $x$-force per unit area on the $y$-face. Symmetry $\sigma_{jj'} = \sigma_{j'j}$ holds because torque balance on any infinitesimal element requires the shear couple on opposite faces to cancel, leaving only 6 independent components.

## Cauchy stress tensor and equilibrium

From [[likharev-chap7]] §7.2, Newton's law for a continuum element gives:

$$\rho \frac{\partial^2 q_j}{\partial t^2} = \sum_{j'} \frac{\partial \sigma_{jj'}}{\partial r_{j'}} + f_j$$

In static equilibrium, the stress divergence balances any body force $f_j$. The elastic energy density is $u = \frac{1}{2}\sum_{j,j'}\sigma_{jj'} s_{jj'}$, coupling stress and [[strain]] through [[hookes-law]].

See [[landau-chap2]] §§16–19 for the 3D treatment including rod and plate stress fields. For the isotropic tensor form, see [[likharev-chap7]] §7.3.

## Yield stress

The **yield stress** $\sigma_y$ is the stress at which a material transitions from elastic (recoverable) to plastic (permanent) [[deformation]]. Below $\sigma_y$, unloading returns the material to its original shape. For metals, $\sigma_y$ is a well-defined threshold and its increase under plastic cycling is [[work-hardening]]. For soft materials such as yarn and knitted fabrics, the transition is gradual and rate-dependent — there is no sharp yield point.

## Stress in knitted fabrics

In knitting research, stress is reported as **force per unit width** (N/m) rather than force per unit area (Pa). This convention arises because fabric thickness is ill-defined and varies with loading. The two-regime constitutive model (source: Singal_NatureComm_2024.pdf):

$$\sigma(\varepsilon) = Y\varepsilon + \beta(1 - \alpha\varepsilon)^{-2}$$

describes the low-stress (bending-dominated) and high-stress (contact-dominated) regimes. See [[constitutive-model]] for the full treatment.

Because knitted fabrics are anisotropic, the stress–strain response differs along the [[wale-and-course]] directions — Young's moduli can differ by orders of magnitude between directions depending on stitch pattern. See [[knit-elasticity]].

Under cyclic loading, stress at a given strain depends on loading history ([[return-point-memory]]), and discrete stick-slip events produce abrupt stress drops that follow power-law statistics ([[crackling-dynamics]]).

## Related pages

- [[strain]]
- [[deformation]]
- [[hookes-law]]
- [[stress-strain-curve]]
- [[constitutive-model]]
- [[knit-elasticity]]
- [[wale-and-course]]
- [[return-point-memory]]
- [[crackling-dynamics]]
- [[work-hardening]]
- [[likharev-chap7]]
- [[landau-chap2]]
