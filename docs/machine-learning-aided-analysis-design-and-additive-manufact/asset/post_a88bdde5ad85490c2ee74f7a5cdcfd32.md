
## Table 10.2 Mid-span deflections (mm) considering high-density layer uncertainty ($\alpha_2 = 1, \beta_1 = 1$).

| $\alpha_1$ | 0 | 0.25 | 0.5 | 0.75 | 1 |
|---|---|---|---|---|---|
| 0 | 1.412 | 1.378 | 1.344 | 1.313 | 1.283 |
| 0.1 | 1.405 | 1.374 | | 1.316 | 1.288 |
| 0.2 | 1.398 | 1.371 | | 1.319 | 1.294 |
| 0.3 | 1.391 | 1.367 | | 1.322 | 1.300 |
| 0.4 | 1.384 | 1.364 | | 1.325 | 1.307 |
| 0.5 | 1.378 | 1.361 | | 1.328 | 1.313 |
| 0.6 | 1.371 | 1.357 | | 1.332 | 1.319 |
| 0.7 | 1.364 | 1.354 | | 1.335 | 1.325 |
| 0.8 | 1.357 | 1.351 | | 1.338 | 1.332 |
| 0.9 | 1.351 | 1.348 | | 1.341 | 1.338 |
| 1 | 1.344 | 1.344 | | 1.344 | 1.344 |

## Table 10.3 Mid-span deflections (mm) considering low-density layer uncertainty ($\alpha_1 = 1, \beta_2 = 1$).

| $\alpha_2$ | 0 | 0.25 | 0.5 | 0.75 | 1 |
|---|---|---|---|---|---|
| 0 | 1.358 | 1.351 | 1.344 | 1.337 | 1.331 |
| 0.1 | 1.357 | 1.351 | | 1.339 | 1.332 |
| 0.2 | 1.356 | 1.350 | | 1.338 | 1.333 |
| 0.3 | 1.354 | 1.349 | | 1.340 | 1.335 |
| 0.4 | 1.353 | 1.349 | | 1.341 | 1.336 |
| 0.5 | 1.351 | 1.348 | | 1.337 | 1.337 |
| 0.6 | 1.350 | 1.347 | | 1.342 | 1.330 |
| 0.7 | 1.349 | 1.346 | | 1.342 | 1.340 |
| 0.8 | 1.347 | 1.346 | | 1.343 | 1.342 |
| 0.9 | 1.346 | 1.345 | | 1.344 | 1.343 |
| 1 | 1.344 | 1.344 | | 1.344 | 1.344 |

elements (SOLID186). As can be seen, a high level of agreement demonstrates the validity of the present formulations.

```
For homogeneous beam $\Delta = \frac{PL^3}{48EI}$ (10.19)
```

where $E^*$ is based on Eq. (10.15) and $I = bh_h^3/12$.

AI-enhanced FE multiscale modeling

**Table 10.4** Mid-span deflections (mm) considering uncertainties of both layers.

| $\alpha_1, \alpha_2$ | 0 | 0.25 | 0.5 | 0.75 | 1 |
|---|---|---|---|---|---|
| 0 | 1.428 | 1.385 | 1.344 | 1.306 | 1.270 |
| 0.1 | 1.419 | 1.381 | | 1.310 | 1.277 |
| 0.2 | 1.410 | 1.377 | | 1.314 | 1.284 |
| 0.3 | 1.402 | 1.372 | | 1.317 | 1.291 |
| 0.4 | 1.393 | 1.368 | | 1.321 | 1.299 |
| 0.5 | 1.385 | 1.364 | | 1.325 | 1.306 |
| 0.6 | 1.377 | 1.360 | | 1.329 | 1.314 |
| 0.7 | 1.368 | 1.356 | | 1.333 | 1.321 |
| 0.8 | 1.360 | 1.352 | | 1.337 | 1.329 |
| 0.9 | 1.352 | 1.348 | | 1.340 | 1.337 |
| 1 | 1.344 | 1.344 | | 1.344 | 1.334 |

![](img/90ed165a39fa708ec43da79319c25_271_0.png) (A) High-density layer

![](img/90ed165a39fa708ec43da79319c25_271.png) (B) Low-density layer

(C) Uncertainties of both layers

**Figure 10.10** Upper and lower bounds of uncertain mid-span deflections.

FG porous composite structures The structural uncertainty of the target FG porous beam is examined on the basis of varying mid-span deflections subject to a fixed load (see Fig. 10.8), considering the CNN-predicted Young's moduli with triangular fuzzy numbers, Tables 10.2–10.4 tabulate the deflection results in terms of the uncertainties induced from high-density layer, low-density layer, and both layers, while the corresponding upper and lower bounds are depicted in Fig. 10.10, B, and C, respectively. It is found that the fuzziness of high-density layer produces a larger deflection range (1.283–1.412, $\alpha_1 = 0$) than that related with low-density layer (1.331–1.358, $\alpha_2 = 0$), as evidenced by the upper and lower bounds. In meanwhile, while accounting for the uncertainties of both layers simultaneously, the deflection range is further extended with distinctly separated layers (1.270–1.428, $\alpha_1=\alpha_2=0$). This indicates that the uncertainty impacts stiffness more significantly than the low-density layer one, despite the obvious difference in the layer thickness, the high-density layer is thicker than its low-density counterpart. The design of this FG porous beam is rather similar to a sandwich configuration, and hence the strong facings contribute to the overall structural rigidity in a more effective manner than the soft lightweight core.

## 10.4 Conclusions

This chapter proposes a novel framework for AI-enhanced multiscale modeling of FG porous structures. A database contains FE RVES with various cell morphologies and corresponding to the practical closed-cell aluminum foams. The deep learning CNN model is designed and trained to predict the effective Young's modulus of RVEs simply based on their images. The structural uncertainty originated from CNN results (~5.926%) is revealed with a bending assessment on the FG porous three-layer beam. The findings show that the developed method has a great potential to quickly and accurately evaluate the structural performance according to the mesoscopic characteristics of foams extracted from images, bypassing the detailed mechanical modeling. The consequent behavior can be quantitatively measured.

In the study here, 2D images provide a relatively easy path for the establishment of the relationship between foam morphologies and properties. However, 3D analysis generally gives more in-depth insights into micro- and macroproperties of cellular composites and the connection may also be captured by CNN models. This will be included into the future research.

## Acknowledgments

The author Chen acknowledges the financial support from the Australian Research Council (ARC DECRA DE220100876).

## References

- [1] Alantali A, Alia RA, Umer R, Cantwell WJ. Energy absorption in aluminium honeycomb cores reinforced with carbon fiber reinforced composite tubes. J Sandw Struct Mater 2017:2801–15.
- [2] Wang C, Cheng H, Gong X, Zhang Y. Lightweight carbon fiber reinforced silica-phenolic resin aerosol nanocomposite facile preparation, properties and application to thermal protection. Compos Part A: Appl Sci Mater 2018:112:28–39.
- [3] Ahmad H, Madsen AA, Poron. ... considering the CNN-predicted Young's moduli with triangular fuzzy numbers, Tables 10.2–10.4 tabulate the deflection results in terms of the uncertainties induced from high-density layer, low-density layer, and both layers, while the corresponding upper and lower bounds are depicted in Fig. 10.10, B, and C, respectively. (Note: The OCR text for reference 3 was fragmented/merged with body text).
