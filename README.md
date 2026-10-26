# Statistical Process Control and Yield Analysis of Fab Sensor Data (SECOM)

**Remade project.** Based on the idea of [ragonxdragon/secom-spc](https://github.com/ragonxdragon/secom-spc) (SPC and an honest fail-prediction study on SECOM). This version is a rewrite with its own analysis: missingness and duplicate-sensor audit, p-chart of yield, FDR-controlled sensor screening, detrending against neighbouring runs, AR(1)-residual control charts, and a time-ordered model evaluation with a permutation test.

**Data:** UCI SECOM (McCann & Johnston, 2008, CC BY 4.0): 1,567 production runs, 590 in-line sensors, 104 failures (6.6%). Downloaded automatically and checked by SHA-256.

## Key results
- Yield is not stable: the fail rate falls from **8.6% to 4.7%** over the quarter (Fisher p = 0.002), a time trend that confounds sensor comparisons.
- 13 sensors pass Benjamini–Hochberg FDR and an effect-size bar, but only **6 (5 independent signals)** survive detrending.
- Shewhart limits over-alarm: one autocorrelated sensor puts **29%** of runs beyond 3σ (0.27% expected); AR(1)-residual charts cut this to about 7%.
- A time-ordered fail predictor is **no better than chance** (PR-AUC 0.066 vs 0.055, permutation p ≈ 0.35), so monitoring is recommended over deploying a model.

## Run
```bash
pip install -r requirements.txt
jupyter notebook secom_spc_yield_analysis.ipynb   # Restart & Run All, a few minutes on a laptop
```
