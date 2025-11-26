# Thesis M2 — Precipitation Nowcasting with HDRain Data

## Overview
This repository hosts the Master’s internship thesis (Computer Science, Université Paris-Saclay, academic year 2024–2025) completed at HDRain by Cheikh Ahmed Tidiane Mané. The report covers the evaluation and adaptation of precipitation nowcasting models using HDRain’s high-resolution data.

## Repository contents
- `thesis.pdf`: full 45-page report generated with LaTeX.

## Thesis highlights
- Context: comparison of very-short-term forecasting (nowcasting) models for high-resolution precipitation data derived from satellite TV signal attenuation.
- Data pipeline: generation of a raw NetCDF (`input.nc`), preprocessing (reprojection to 1 km, reflection padding to 928×928, log(x+0.01) normalization), and streaming writes to limit memory.
- Models evaluated: advection, RainNet (CNN-based), PySTEPS (probabilistic), and a zero predictor baseline.
- Evaluation: MAE/MSE (global and rain-only), CSI, POD, FAR, multi-class confusion matrices across lead times from 5 to 80 minutes.
- Results: RainNet and PySTEPS outperform advection and the zero baseline. RainNet better detects light rain; PySTEPS is stronger on moderate/heavy rain but raises more false alarms.
- RainNet finetuning on HDRain data: marginal or no gains, with long-horizon degradation due to heavy padding, distribution shift, and limited data volume.
- Training RainNet from scratch (256×256 tiles): does not surpass the pre-trained model, indicating the need for new architectures or more data.
- Operational decision: HDRain adopts PySTEPS for a performance/feasibility balance; future work includes hybrid advection+DL models, spatiotemporal transformers, and richer HDRain datasets.

## Quick read
- Open `thesis.pdf` with your PDF reader.
- Terminal text preview: `pdftotext -f 1 -l 2 thesis.pdf -`.

## Citation
> Cheikh Ahmed Tidiane Mané, *Évaluation et adaptation de modèles de nowcasting des précipitations dans le contexte des données HDRain*, Master Informatique, Université Paris-Saclay, 2025.
