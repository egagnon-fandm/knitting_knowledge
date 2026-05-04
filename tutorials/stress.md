# Stress

**Last updated**: 2026-04-29

---

When you pull on a rubber band or compress a foam block, you apply external forces. Inside the material, those forces are transmitted from one region to another through internal contact forces. **Stress** is the measure of those internal forces — force per unit area — and it is one of the two fundamental quantities in solid mechanics (the other being strain).

## What is stress?

Stress is the limit of contact force per unit area as the area element shrinks to a point:

$$\sigma = \lim_{\Delta A \to 0} \frac{\Delta F}{\Delta A}$$

The SI unit is the **pascal**: 1 Pa = 1 N/m². Engineering materials are typically characterised in MPa (10⁶ Pa) or GPa (10⁹ Pa).

## Normal vs. shear stress

The orientation of the force relative to the surface determines its type:

- **Normal stress** ($\sigma_n$): force component *perpendicular* to the surface. Positive = tension (pulling apart); negative = compression.
- **Shear stress** ($\tau$): force component *parallel* to the surface. Shear distorts shape without changing volume.

For a bar of cross-sectional area $A$ under axial load $F$:

$$\sigma = \frac{F}{A}$$

This is the simplest stress calculation and the starting point for most structural analysis.

## The stress tensor

At any point inside a 3D body, the stress state depends on which plane you examine. The full description is the **Cauchy stress tensor** $\boldsymbol{\sigma}$ — a $3 \times 3$ symmetric matrix:

$$\boldsymbol{\sigma} = \begin{pmatrix} \sigma_{xx} & \sigma_{xy} & \sigma_{xz} \\ \sigma_{xy} & \sigma_{yy} & \sigma_{yz} \\ \sigma_{xz} & \sigma_{yz} & \sigma_{zz} \end{pmatrix}$$

**Reading the indices.** Each entry $\sigma_{jj'}$ carries two pieces of information encoded in its two indices:

- The **second index $j'$** identifies the plane being examined: the surface whose outward normal points in the $j'$-direction. For example, $j' = x$ refers to the face of an infinitesimal cube that faces in the $x$-direction.
- The **first index $j$** identifies the direction of the force (per unit area) acting on that face.

**Same indices ($j = j'$, diagonal entries — normal stress).** When both indices are the same, the force is *perpendicular* to the face. $\sigma_{xx}$ is the $x$-force per unit area on the $x$-face: a pure push or pull along $x$. Positive = tension (faces being pulled apart); negative = compression (faces being squeezed). These three entries, $\sigma_{xx}$, $\sigma_{yy}$, $\sigma_{zz}$, describe how the material is being stretched or compressed along each axis independently.

**Different indices ($j \neq j'$, off-diagonal entries — shear stress).** When the indices differ, the force is *parallel* to the face rather than perpendicular to it. $\sigma_{xy}$ is the $x$-force per unit area on the $y$-face: the face is being slid in the $x$-direction. This sliding distorts the shape of the element (turning a cube into a parallelogram) without changing its volume. Symmetry ($\sigma_{jj'} = \sigma_{j'j}$) means $\sigma_{xy}$ and $\sigma_{yx}$ are equal, so sliding the $y$-face in $x$ produces the same stress as sliding the $x$-face in $y$ — a consequence of torque balance on the element.

The traction (force per area) on a surface with outward unit normal $\hat{n}$ is:

$$\mathbf{t} = \boldsymbol{\sigma} \cdot \hat{n}$$

Symmetry ($\sigma_{ij} = \sigma_{ji}$) follows from the requirement that no infinitesimal element experiences a net torque, leaving 6 independent components.

## Yield stress

Materials behave elastically — returning to their original shape on unloading — only up to a stress limit called the **yield stress** $\sigma_y$:

- **Below $\sigma_y$**: elastic behaviour; stress and strain are proportional (Hooke's law: $\sigma = E\varepsilon$).
- **Above $\sigma_y$**: permanent (plastic) deformation begins; energy is dissipated.

For mild steel, $\sigma_y \approx 250$ MPa. For soft materials such as yarn or biological tissue, there is no sharp yield point — the transition to irreversible behaviour is gradual.

## Stress in knitted fabrics

Knitted fabrics are thin and porous. Because the fabric thickness is ill-defined and mostly air, stress is reported as **force per unit width** (N/m) rather than force per unit area (Pa):

$$\sigma_\text{fabric} = \frac{F}{w}$$

where $w$ is the fabric width perpendicular to the applied force. This is sometimes called *areal stress* or *line tension*.

Knitted fabrics are also **anisotropic**: the stress response along the wale direction (columns) differs from the course direction (rows) by a factor of 10 or more depending on the stitch pattern. The stress at any given strain also depends on loading history — fabric memory effects (see Dresselhaus et al. 2025) mean that loading and unloading follow different curves.

## Example problems

### Problem 1 — Axial stress in a steel rod

A steel rod of diameter $d = 4$ mm is loaded in tension by $F = 6$ kN. Compute the axial stress and determine whether the rod yields (yield stress of mild steel $\approx 250$ MPa).

**Solution:**

Cross-sectional area:
$$A = \frac{\pi d^2}{4} = \frac{\pi (4 \times 10^{-3})^2}{4} = 1.257 \times 10^{-5} \text{ m}^2$$

Axial stress:
$$\sigma = \frac{F}{A} = \frac{6000}{1.257 \times 10^{-5}} = 477 \text{ MPa}$$

Since 477 MPa $>$ 250 MPa, the rod **yields**. A thicker rod (diameter $\gtrsim 5.5$ mm) would be needed to stay elastic.

---

### Problem 2 — Force per unit width in a knitted fabric

A rib-stitch fabric sample 60 mm wide is pulled in the course direction with $F = 3.6$ N. What is the stress in conventional fabric units?

**Solution:**

$$\sigma = \frac{F}{w} = \frac{3.6 \text{ N}}{0.060 \text{ m}} = 60 \text{ N/m}$$

If the same test on a stockinette sample requires $F = 10$ N to reach the same strain, the stockinette Young's modulus is $10/3.6 \approx 2.8\times$ larger. This is consistent with stockinette having stiff (even) connecting segments in the course direction, while rib has soft (odd) segments.

---

### Problem 3 — Normal and shear stress on an inclined plane

A bar under uniaxial tension $\sigma_0$ is cut along a plane whose normal makes angle $\theta$ with the load axis. Find the normal and shear stress on that plane. At what angle is the shear stress maximum?

**Solution:**

With $\boldsymbol{\sigma} = \text{diag}(\sigma_0, 0, 0)$ and $\hat{n} = (\cos\theta,\, \sin\theta,\, 0)$:

$$\mathbf{t} = \boldsymbol{\sigma} \cdot \hat{n} = (\sigma_0 \cos\theta,\; 0,\; 0)$$

Normal component:
$$\sigma_n = \mathbf{t} \cdot \hat{n} = \sigma_0 \cos^2\theta$$

Shear component:
$$\tau = \sqrt{|\mathbf{t}|^2 - \sigma_n^2} = \sigma_0 \cos\theta \sin\theta = \frac{\sigma_0}{2}\sin 2\theta$$

Maximum shear stress occurs at $\theta = 45°$: $\tau_\text{max} = \sigma_0/2$.

This is why ductile metals fail along 45° slip planes — and why crackling avalanches in knitted fabrics propagate preferentially along ±45° diagonals of the stitch lattice.
