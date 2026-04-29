# Work Hardening

**Summary**: Work hardening (strain hardening) is the process by which a material's yield strength increases during plastic deformation due to dislocation accumulation. Described empirically by Hollomon's power law σ = Kε_p^n. The phenomenon has a structural analogue in knitted fabrics, though the physical mechanism differs entirely.

**Sources**: `raw/Work_hardening.md` (Wikipedia)

**Last updated**: 2026-04-16

---

## Definition

Work hardening is the increase in **yield strength** of a ductile material after it has undergone plastic (permanent) deformation. It is distinct from elastic deformation, which is fully reversible. The strengthened material requires greater stress to continue deforming plastically.

Common in: metals (steel, copper, aluminium), some polymers. Not applicable to brittle materials.

---

## Physical mechanism (metals)

Before deformation, a crystalline lattice has few dislocations (~10^7–10^9 per m^2 → low strength). Plastic deformation creates new dislocations, raising the density toward ~10^14 per m^2. The accumulated dislocation strain fields impede further dislocation motion, raising the stress needed for additional plastic flow.

Shear strength:

$$\tau = \tau_0 + G\alpha b\,\rho_\perp^{1/2}$$

where G is shear modulus, b is the Burgers vector magnitude, ρ_⊥ is dislocation density, and α is a correction factor. Yield stress grows as the square root of dislocation density.

Work hardening is **reversed by annealing** (heating above the recrystallization temperature), which removes dislocations.

---

## Empirical relations

**Hollomon's equation** (power-law hardening):

$$\sigma = K\varepsilon_p^n$$

**Ludwik's equation** (includes initial yield stress):

$$\sigma = \sigma_y + K\varepsilon_p^n$$

where ε_p is plastic strain, K is the strength coefficient, and n is the **strain hardening exponent** (typically n ∈ [0.2, 0.5] for metals). Higher n means more hardening per unit strain.

After prior plastic deformation ε_0:

$$\sigma = \sigma_y + K(\varepsilon_0 + \varepsilon_p)^n$$

---

## Trade-off: strength vs. ductility

As yield strength increases through work hardening, ductility (capacity for further plastic deformation) decreases. An extreme case: a fully work-hardened bar has zero residual ductility — it fractures at the first additional plastic strain attempt.

---

## Contrast with knitted fabric hysteresis

Knitted fabrics also exhibit stiffening and hysteresis across load cycles, but the mechanism is entirely different:

| Feature | Work hardening (metals) | Knitted fabric cycling |
|---|---|---|
| Physical cause | Dislocation accumulation | Yarn contact rearrangement, inter-yarn friction |
| Reversibility | Reversed only by annealing | Partially reversible; RPM locks in new state |
| Directionality | Hardening (stiffens on re-load) | **Softening** on first unload (lower modulus); RPM memory at max strain |
| Temperature needed | Yes (anneal) | No |
| Governing framework | Crystal plasticity | Preisach model ([[return-point-memory]]) |

The key phenomenological difference: metals get **harder** with deformation history; knitted fabrics exhibit **return point memory** where stress on reload follows the prior unloading curve, not a harder new curve. Some softening on first straining also occurs — analogous to the Mullins effect in filled rubbers, where irreversible network rearrangements reduce the modulus on first extension (needs verification: no source in this wiki directly documents this for knitted fabrics).

The power-law hardening concept (stress ∝ strain^n) is nonetheless a useful reference point when fitting empirical loading curves of nonlinear fabrics, even though the underlying physics differs.

---

## Related pages

- [[stress-strain-curve]]
- [[return-point-memory]]
- [[deformation]]
- [[strain]]
