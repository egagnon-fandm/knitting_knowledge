# Poincloux, Adda-Bedia & Lechenault — Crackling Dynamics in the Mechanical Response of Knitted Fabrics (PRL 2018)

**Summary**: Experimental demonstration that quasistatic tensile testing of a knitted fabric produces avalanche-like slip events with power-law size distributions (exponent ≈ −3/2), consistent with mean-field soft amorphous material models, despite the topologically ordered structure of the fabric.

**Sources**: `raw/Poincloux_PRL_2018.pdf`, `raw/Poincloux_PRL_2018_Supplemental.pdf`

**Last updated**: 2026-04-13

---

## Citation

Poincloux, S., Adda-Bedia, M., & Lechenault, F. (2018). Crackling dynamics in the mechanical response of knitted fabrics. *Physical Review Letters*, **121**, 058002. DOI: 10.1103/PhysRevLett.121.058002

## Key contributions

1. First experimental evidence of crackling noise in a structurally ordered soft material (knitted fabric).
2. Three independent, consistent measurements of avalanche size: force drops ($\Delta f$), vorticity events ($S_\omega$), deviatoric strain events ($S_d$).
3. Power-law exponent ≈ −3/2, matching mean-field prediction for soft amorphous materials.
4. Demonstration that internal (optical) and external (force) measurements track the same events.
5. Theoretical explanation of avalanche propagation direction from knit elasticity model.

## Experimental setup

- **Sample**: $83 \times 83$ stitch nylon monofilament (150 μm), single-bed machine
- **Stretching**: Cyclic wale-direction elongation between $L_i = 215$ mm and $L_f = 234$ mm; measurements in $[L_m, L_f] = [230, 234]$ mm
- **Speed**: Quasistatic, $v = 1$–$10$ μm/s during measurement, $v = 0.5$ mm/s outside
- **Force**: Instron with 50 N load cell at high acquisition frequency
- **Imaging**: 7360 × 4912 pixel images every $\Delta L = 0.2$ mm

## Analysis methods

**Nonaffine displacement field**: Total displacement minus best-fit affine (linear) field: $\vec{u} = \vec{u}_\text{tot} - \vec{u}_\text{lin}$

**Vorticity**: $\omega = \partial_x u_y - \partial_y u_x$ — marks rotational slip events

**Deviatoric strain**: $\varepsilon_d = \sqrt{(\partial_x u_x - \partial_y u_y)^2 + (\partial_x u_y + \partial_y u_x)^2}$ — marks shear slip events

Event size $S_\omega$ measured by integrating $|\omega|$ over connected stitches above threshold.

## Results

### Power law distributions

| Quantity | Exponent |
|---|---|
| Force drops $\Delta f$ | $-1.50 \pm 0.03$ |
| Vorticity $S_\omega$ | $-1.51 \pm 0.05$ |
| Deviatoric strain $S_d$ | $-1.61 \pm 0.03$ |

Scaling is robust across: threshold value, loading speed, stretching range (source: Poincloux_PRL_2018.pdf).

### Internal-external correspondence

A scatter plot of $\Sigma S_\omega$ vs. $\Sigma \Delta f$ (summed over events between images) shows a clear linear trend with slope $E_p = 0.12$ N, establishing statistical correspondence between optical and force measurements.

### Avalanche propagation

Positive events (ω > 0) propagate preferentially along the $-\pi/4$ diagonal of the stitch lattice. Explained by the elastic model: a local vorticity perturbation generates vorticity maxima at ±π/4 from the source.

## Interpretation

The knitted fabric fits the **elastoplastic model** framework for soft amorphous solids:
- Elastic matrix with spatially distributed plastic thresholds (set by local friction)
- Stress redistribution from plastic events can trigger further events
- Avalanches propagate through stress redistribution

Key distinction: unlike amorphous solids, the fabric has **structural order** (no positional disorder) — the crackling arises purely from **disorder in friction thresholds**, making it an unusually clean test system.

## Related pages

- [[crackling-dynamics]]
- [[knit-elasticity]]
- [[poincloux-prx-2018]]
- [[return-point-memory]]
- [[deformation]]
- [[stress-strain-curve]]
