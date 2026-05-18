# Htike, Kang & Sukigara 2016 — Tensile Property of Highly Twisted Cotton Yarns Under Varied Relative Humidity

**Summary**: Cyclic tensile tests on four highly twisted cotton yarns at 10–90% RH and water-immersed reveal that both twist level and humidity increase yarn extensibility while decreasing resilience and recovery; the weft-direction extensibility of crepe fabric (16–26%) falls in the same range as outer-knitted fabrics.

**Sources**: `raw/Htike et al. - 2016 - Tensile property of highly twisted cotton yarns under varied relative humidity.pdf`

**Last updated**: 2026-05-18

---

## Citation

Htike, H. H., Kang, J., & Sukigara, S. (2016). Tensile property of highly twisted cotton yarns under varied relative humidity. *International Journal of Clothing Science and Technology*, 28(4), 390–399. Kyoto Institute of Technology.

## Motivation

Japanese cotton crepe fabric *chijimi* achieves high extensibility (16–26% in the weft direction) by using high-twist weft yarns. Because extensibility and recovery change with environmental humidity, this study characterizes the tensile response of four highly twisted cotton yarns across 10–90% RH and water immersion.

## Samples

Four 100% cotton ring-spun yarns:

| Sample | Count (Tex) | Twist (T/m) | Twist factor K | Twist angle (°) | Breaking strength (N) | Breaking elongation (%) |
|---|---|---|---|---|---|---|
| Y1 | 14.8 | 1,000 | 3,847 | 24.3 | 2.19 | 5.0 |
| Y2 | 14.8 | 2,200 | 8,464 | 44.8 | 1.97 | 10.6 |
| Y3 | 29.5 | 1,300 | 7,067 | 39.6 | 5.09 | 9.9 |
| Y4 | 9.8 | 3,000 | 9,411 | 47.8 | 1.77 | 8.8 |

Y1 is the warp yarn; Y2 is the weft yarn in chijimi. K is defined as $K = T \sqrt{\text{Tex}}$.

Twist angle $\theta = \tan^{-1}(2\pi r T)$ where $r$ is yarn radius.

## Protocol

- Samples dried at 100°C (3 min), conditioned at each RH level (1 hr at 40–90% RH), then tested at 25°C.
- Three cyclic force-extension tests to 1 N per yarn, speed 0.1 mm/s.
- Characteristic values extracted: EM-1 (1st-cycle extensibility), EM-2, EM-3 (subsequent cycles), WT (tensile energy), RT-1 (resilience = energy recovery ratio), Δε (residual strain = EM-1 − EM-2).

## Results

### Extensibility (EM-1) vs. humidity

All yarns become more extensible as RH increases. For Y1 and Y2 (same yarn count, different twist):

$$\frac{\text{EM-1(Y2)}}{\text{EM-1(Y1)}} = \frac{E_1(\text{Y1})}{E_2(\text{Y2})} \approx 3.08 \quad \text{(constant at 40–90\% RH)}$$

This ratio follows directly from $\sigma = E\varepsilon$: higher twist lowers the longitudinal modulus $E$, which increases extensibility under a fixed load. At 10% RH the ratio drops to ~2.67 because Y2's twist angle changes less at very low humidity.

At very high humidity (>70% RH for Y2, >60% RH for Y4), *yarn snarling* is observed: over-twist torque relaxes by forming local coils. The snarled sections have higher twist angles and contribute additional extensibility.

### Resilience (RT-1) vs. humidity

- Resilience **decreases** with RH for all samples.
- Y1 (lower twist) has higher resilience than Y2 at all RH.
- At 90% RH, ~50% of EM-1 becomes residual strain — the yarn does not recover from the first extension.
- At water-immersion, RT values for Y1 and Y2 converge (twist effect on recovery disappears).

### Residual strain (Δε)

- Higher for Y2 than Y1 at all RH; the gap widens with humidity.
- At 90% RH, Δε ≈ 50% of EM-1 for all samples.
- Physical origin: under high humidity, fiber-fiber friction changes because water lubricates some contact points but also swells fibers, and the irreversible rearrangement of the twist structure after the first cycle leaves a permanent set.

### Fabric extensibility

Plain-woven crepe fabric (Y1 warp, Y2 weft):
- **Weft direction** (Y2 twist dominates): EM-1 = 16–26%, comparable to outer-knitted fabrics.
- **Warp direction** (Y1 twist): EM-1 < 2% across all humidity conditions.
- Recovery in the weft direction decreases with humidity: a 10% drop in RT at 40% RH → further drops at 80 and 90% RH.

The conclusion is that the weft yarn twist level dominates both extensibility and humidity sensitivity of chijimi fabric.

## Comparison with Pillay 1963

[[pillay-1963]] studied 24s (24.6 tex) yarns at TM 3.75–6.0 (twist factors ~1,865–2,985) — lower twist factors than Y2 and Y4 here. Pillay reported *stiffness increases* with wetting; here, at the much higher twist factors of Y2–Y4, moisture increases extensibility. The regimes are different: Pillay's yarns are in the normal twist range for weaving, while Htike's Y2 and Y4 are in the high-twist "crepe" regime where untwisting under tension is the dominant deformation mechanism.

Both studies agree that twist interacts with moisture to produce a complex, non-monotonic response — validating that yarn twist is as important an environmental variable as humidity.

## Relevance to knitting research

- Fabric-level extensibility of weft-direction chijimi (16–26%) falls squarely in the range of knitted fabric extensibility, confirming that high-twist weave is a structural analog to the loop-based extensibility of knits.
- First-cycle hysteresis and residual strain in these yarns mirrors the cycling behavior of knitted fabrics reported in [[return-point-memory]] and [[crackling-dynamics]] — the yarn level contributes to fabric-level history-dependence.
- Cotton yarns for knitting should not be assigned fixed modulus values; environmental humidity shifts both extensibility and recovery substantially.

## Related pages

- [[yarn]]
- [[pillay-1963]]
- [[xiong-2026]]
- [[return-point-memory]]
- [[crackling-dynamics]]
- [[knitted-fabrics]]
