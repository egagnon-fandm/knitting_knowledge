# Xiong et al. 2026 — Tensile Behavior of Cotton Ring-Spun Yarn with Twisted Staple Fibers

**Summary**: An experiment-and-simulation study of cotton ring-spun yarn showing that twist angle and inter-fiber friction coefficient are the two dominant factors governing tensile modulus. A modified rule-of-mixtures incorporating a friction correction factor $\eta_\mu = 1 + \alpha\mu_f\sin^2\theta$ outperforms the classical formula and matches FE simulations within 2%.

**Sources**: `raw/Xiong et al. - 2026 - An Experiment and Simulation Study on the Tensile Behavior of Cotton Ring-Spun Yarn with Twisted Sta.pdf`

**Last updated**: 2026-05-17

---

## Citation

Xiong, X., Wu, S., Zeng, L., Zhou, J., Hou, Z., Li, X., Chen, M., Shen, C., Fan, F. (2026). An experiment and simulation study on the tensile behavior of cotton ring-spun yarn with twisted staple fibers. *Materials*, 19, 560. Wuhan Textile University / Shandong Rifa Textile.

## Experimental setup

Four cotton ring-spun yarn types were characterized by SEM:

| Type | Diameter (mm) | Tex | Twist (turns/cm) | Twist angle |
|---|---|---|---|---|
| Y1 | 0.112 | 14.8 | 6.7 | 13.2° |
| Y2 | 0.146 | 18.5 | 8.5 | 21.4° |
| Y3 | 0.169 | 28.1 | 10.4 | 28.9° |
| Y4 | 0.208 | 36.9 | 14.1 | 42.7° |

Cotton fibers: mean diameter 15 μm, arranged in ideal helical trajectories (concentric layers with uniform pitch). Tests: ASTM D2256, gauge lengths 50–250 mm, speeds 1–3 mm/s, 20 repeats each.

**Key experimental finding**: tensile strength and modulus are **not sensitive** to yarn length (50–250 mm range) or tensile speed (1–3 mm/s range). Variation < 5% across all conditions. This confirms that cotton yarn behaves as a linear elastic material at these low strain rates, and that fiber length effects and boundary conditions are minor.

## FE model

- Software: Abaqus 2024/Explicit.
- Fiber material: anisotropic (transversely isotropic): $E_1 = 1520$ MPa (longitudinal), $E_2 = E_3 = 196.7$ MPa (transverse), $G_{13} = 85.3$ MPa, $G_{23} = 56.2$ MPa, $\nu_{12} = \nu_{13} = 0.30$, $\nu_{23} = 0.32$.
- Fiber geometry: circular cross-section, each fiber = 4800 solid elements (C3D8R), element length 20 μm, cross-section element size 2.9 μm (convergence tested).
- Fiber count: 37 (Y1/S1) to 102 (Y4/S4) fibers per yarn model.
- Contact: Coulomb friction; friction coefficients 0.2–0.6 tested; $\mu_f = 0.5$ matches experiment with < 2% error.
- Boundary conditions: bottom face fixed; top face displaced axially; cross-sections coupled to rigid reference points.

## Results: twist angle effect

Tensile modulus **decreases significantly** with increasing twist angle:

| Model | Twist angle | Tensile modulus (MPa) |
|---|---|---|
| S1 | 13.2° | ~1100–1140 |
| S2 | 21.4° | ~1060–1070 |
| S3 | 28.9° | ~800–830 |
| S4 | 42.7° | ~590–620 |

The modulus drop is particularly sharp above 28.9°. The mechanism: at higher twist, fibers are more oblique to the load axis, and fiber slippage becomes more likely — low friction loads are borne less efficiently. Yarn diameter has **negligible influence** on tensile modulus when twist angle is held constant.

## Results: friction coefficient effect

- Tensile modulus increases with friction coefficient but saturates.
- At low twist (13.2°): small friction effect because radial contact forces are small.
- At high twist (42.7°): friction effect is large; $\mu_f \geq 0.4$ provides "mutual locking" — further increase in $\mu_f$ yields diminishing returns.
- Physically: high twist generates large radial compressive forces proportional to $\sin^2\theta$; Coulomb friction resists fiber slippage proportionally.
- Best experimental match: $\mu_f = 0.5$ (< 2% error across all yarn types).

## Stress distribution

In yarn cross-section, maximum stress concentrates in the **central region** and decreases toward the outer layer. For high-twist yarns (S3, S4), the outer layer has much lower stress than the inner — a more non-uniform distribution that explains their lower overall modulus and strength. Low-twist yarns (S1, S2) have more uniform stress → higher tensile modulus.

## Modified rule-of-mixtures

Classical rule-of-mixtures:

$$E_y = \eta_0 V_f E_f, \quad \eta_0 = \cos^2\theta$$

does not account for friction. Modified version with friction correction factor $\eta_\mu$:

$$E'_y = \eta_0 \eta_\mu V_f E_f$$

$$\eta_\mu = 1 + \alpha \mu_f \sin^2\theta$$

where $\alpha$ is a correction factor (set to 1 for small strains), and $\mu_f$ is the inter-fiber friction coefficient. The $\sin^2\theta$ weighting follows from the fact that normal contact force $q_n \propto \sin^2\theta$, and tangential (friction) force $q_\tau = \mu_f q_n \propto \mu_f \sin^2\theta$.

This formula is significantly more accurate than the unmodified rule-of-mixtures, particularly at high twist angles where friction effects are largest.

## Relation to other yarn mechanics results

- Confirms and quantifies the role of inter-fiber friction suggested qualitatively by [[cornelissen-2009]] for bending behavior.
- Cotton fiber longitudinal modulus $E_1 = 1520$ MPa consistent with the transversely isotropic characterization in [[du-pasquier-2025]] ($E_\text{transverse} \approx E_1/8$).
- Wet behavior studied in [[pillay-1963]]: wetting increases yarn strength partly by increasing inter-fiber friction — consistent with the large friction sensitivity shown here at high twist.

## Related pages

- [[yarn]]
- [[cornelissen-2009]]
- [[du-pasquier-2025]]
- [[pillay-1963]]
- [[yarn-simulation]]
