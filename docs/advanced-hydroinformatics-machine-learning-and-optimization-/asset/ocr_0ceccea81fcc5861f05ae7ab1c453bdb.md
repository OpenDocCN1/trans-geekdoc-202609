# Table 9.1 (continued)

| Authors | Models | Predictand variable | IVS | Decomp algorithm | Mother wavelet | Number of decompositions | Data sets splitting procedure | Stopping criteria | Error |
|---|---|---|---|---|---|---|---|---|---|
| Adamowski 2008 | ANN; WANN | 1 day ahead stream flow prediction | Model-based | A-trous WT | not mentioned | 4 levels (until the lower resolution) | 10-fold cross-validation | No information | R²; RMSE; SEE |
| Venkata et al. | MARS; ANN; WANN AR | 1 month ahead rainfall prediction | Model based | DWT | Db; Morlet | 3 levels (exhaustive search) | The first 60% calibration and 40% data for validation | Cross-validation was performed | RMSE; R; COE |
| Cannas et al., 2005 | ANN; WANN1 WANN2 | 1 month ahead runoff prediction | Heuristic procedure | CWT, DWT | DB4 | 1 level (exhaustive search) | The first 40 yr for cal, the second 9 yr for val and the last 20 yr for testing | Cross-validation was used as stop criterion | NSE; RMSE; MAE; M4E |