# Cornelissen & Akkerman — Analysis of Yarn Bending Behaviour (2009)

**Summary**: Experimental and theoretical study of multi-filament yarn bending in the context of composite fabric forming, comparing Euler-Bernoulli beam theory (EBT) and Timoshenko beam theory (TBT) against cantilever measurements; identifies intra-yarn friction as the cause of unexplained softening in multi-filament deflection.

**Sources**: `raw/Cornelissen_Analysis_of_yarn_bending_behaviour_2009.pdf`

**Last updated**: 2026-04-13

---

## Citation

Cornelissen, B., & Akkerman, R. (2009). Analysis of yarn bending behaviour. University of Twente, Netherlands. (Published in context of composite fabric forming research.)

## Purpose and context

This paper is not about knitted fabrics but about **composite fabric preforming** — the process of draping woven fiber bundles over molds before resin infusion. Bending stiffness of individual yarns is a critical input parameter for forming simulations.

Relevance to knitting research: the cantilever bending measurement protocol and beam theory analysis are directly applicable to characterizing knitting yarns (as used by [[ding-2023]]).

## Beam theories for yarn bending

### Euler-Bernoulli beam theory (EBT)

Bending moment $M$ proportional to curvature:
$$M = EI \cdot \kappa$$

For a cantilever beam under distributed gravity load $q = \pi r^2 \rho g$ (weight per unit length), tip deflection:
$$\delta_\text{EBT} = \frac{q L^4}{8EI}$$

Flexural rigidity: $G_0 = EI = \frac{\pi d^4 E}{64}$ where $d$ is yarn diameter, $E$ is Young's modulus.

EBT assumes: plane sections remain plane; no shear deformation; small deflections.

### Timoshenko beam theory (TBT)

Adds shear contribution:
$$\delta_\text{TBT} = \delta_\text{EBT} + \frac{qL^2}{2GA_s}$$

where $G$ is the shear modulus and $A_s = \kappa_s A$ is the shear area ($\kappa_s$ = shear correction factor).

For typical yarn geometries, TBT gives a negligible correction over EBT for **single filaments** (shear is small compared to bending). The ratio $\delta_\text{TBT}/\delta_\text{EBT} \approx 1 + C(d/L)^2$ → shear matters only for very short, thick beams.

## Cantilever test setup

- One end clamped horizontally, free end droops under gravity
- Measurement: horizontal span $\lambda$ and vertical drop $\delta$
- High-resolution photography with checkerboard background (0.25 mm/pixel)
- Bending stiffness extracted by matching measured deflection to beam model:
$$E^b = \frac{q\lambda^4}{8\delta I}$$

This is the same protocol used by [[ding-2023]] to calibrate their acrylic yarn ($E^b = 0.249$ MPa).

## Material: E-glass yarn

| Property | Value |
|---|---|
| Number of filaments | 1100 |
| Filament diameter | 15.3 μm |
| Young's modulus (filament) | 73 GPa |

E-glass is a stiff engineering fiber, far stiffer than the acrylic yarns used in knitting research. The paper's focus on filament-level mechanics nonetheless provides generalizable insight.

## Key findings

### Single filament behavior

A single glass filament deflects in close agreement with EBT predictions. The TBT correction is negligible. This validates EBT as the correct model when filaments act as independent elastic rods.

### Multi-filament yarn behavior

The yarn as a whole deflects **significantly more** than EBT predicts for the equivalent cross-section. This means the effective bending stiffness is lower than the sum of individual filament stiffnesses.

**Explanation**: Intra-yarn friction. During bending, filaments must slide past each other. When friction is low, filaments slide freely and each bends individually rather than as a unit — equivalent bending stiffness scales as $N \cdot EI_\text{filament}$ rather than $E \cdot (N \cdot I_\text{filament})$. (These are equal only if all filaments share a single neutral axis, which requires perfect bonding or zero sliding.)

For a yarn of $N$ filaments each of radius $r_f$:
- Perfect bonding (no sliding): $EI_\text{total} = E \cdot I_\text{composite} \gg N \cdot EI_\text{filament}$
- Free sliding: $EI_\text{total} = N \cdot EI_\text{filament}$, which can be orders of magnitude smaller

The observed deflection is between the two limits, indicating partial sliding governed by static and kinetic friction between filaments.

### Nonlinear bending behavior

The bending stiffness of multi-filament yarns is **nonlinear and loading-history dependent**. At low curvatures (small deflection), static friction locks filaments together and bending is stiffer. As curvature increases, filaments progressively unlock and slide, reducing effective stiffness.

This has direct implications for knitting simulations: using a single constant $E^b$ is an approximation valid only within a limited curvature range.

## Implications for knitting research

1. **Measurement protocol**: The cantilever test is the standard method for characterizing yarn bending stiffness in simulations ([[ding-2023]], [[singal-naturecomm-2024]]).
2. **EBT sufficiency**: For most knitting simulation purposes, EBT is adequate for the yarn as a whole, with $E^b$ treated as an effective (measured) parameter that implicitly accounts for inter-filament sliding.
3. **Friction at multiple scales**: Just as yarn-yarn contacts create hysteresis at the fabric scale ([[return-point-memory]]), filament-filament contacts within a yarn create nonlinearity at the yarn scale.
4. **Inextensibility assumption**: Cornelissen's work focuses on bending; the related inextensibility assumption used in [[yarn-simulation]] (Dimitriyev/Singal) is separately justified by the very high tensile stiffness of fibers compared to the bending stiffness.

## Related pages

- [[yarn]]
- [[yarn-simulation]]
- [[ding-2023]]
- [[knit-elasticity]]
