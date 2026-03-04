# recalcitrant-seed-drying-simulator
simulator and analysis workflow for mango recalcitrant seed dehydration, estimating critical moisture content and linking moisture loss to germination decline, electrolyte leakage, and respiration.

# Mango Recalcitrant Seed Drying, Simulated Physiology Dataset and Analysis

This repository contains a **reproducible, workflow** that simulates a mango recalcitrant-seed drying experiment and performs advanced analysis and visualization.

The simulation is designed to mirror typical wet-lab seed physiology measurements across drying treatments and time, including:
- Moisture content (% FW basis)
- Germination (%)
- Leachate electrical conductivity (normalized proxy of electrolyte leakage)
- Respiration rate (mg CO₂ g⁻¹ h⁻¹)

It also includes downstream analysis:
- Logistic fitting for **critical moisture content (CMC)**
- Time-to-threshold metrics (T50, T10)
- Regression models for treatment effects (drying mode × endocarp)
- Correlation structure mapping
- PCA + clustering for “injury state” stratification
- Publication-style figures

## Study design

### Treatments
- **ADWE**: Air drying, with endocarp
- **ADWO**: Air drying, without endocarp
- **SDWE**: Sun drying, with endocarp
- **SDWO**: Sun drying, without endocarp

### Time points (hours)
`0, 8, 24, 32, 48, 56, 72, 80, 96, 104`

### Replicates
`n = 3` replicates per treatment × time point (modifiable)

## Repository structure
```
├── mango_recalcitrant_simulation_analysis.py   # main script (or notebook cells pasted into .ipynb)
├── sim_outputs/
│   ├── mango_recalcitrant_drying_simulated.csv
│   ├── cmc_logistic_fits.csv
│   └── time_to_threshold_metrics.csv
├── README.md
├── modelcard.md
└── datasheet.md
```
## Requirements

- Python 3.9+
- numpy
- pandas
- matplotlib
- scipy
- scikit-learn
- statsmodels

## Install:
```
pip install numpy pandas matplotlib scipy scikit-learn statsmodels
```
## run as a script
python mango_recalcitrant_simulation_analysis.py

## Outputs will be saved to:
	•	sim_outputs/mango_recalcitrant_drying_simulated.csv
	•	sim_outputs/cmc_logistic_fits.csv
	•	sim_outputs/time_to_threshold_metrics.csv

## Outputs

1) Simulated dataset

mango_recalcitrant_drying_simulated.csv contains one row per replicate per time point.

Columns include:
	•	treatment, drying, endocarp, time_h, rep
	•	moisture_pct, germination_pct, conductivity_uS, respiration_mgCO2_g_h
	•	viable (operational label)
	•	PC1, PC2, cluster (computed later)

2) CMC estimates

cmc_logistic_fits.csv includes treatment-specific logistic fit parameters:
	•	CMC_est, CMC_se, slope_est, slope_se

3) Time-to-threshold metrics

time_to_threshold_metrics.csv includes:
	•	T50_h, T10_h

## Notes on interpretation

This is a simulation, not a direct replacement for experimental data.
	•	Absolute numeric values depend on parameterization and units used in a lab protocol.
	•	The workflow is intended for hypothesis testing, experimental planning, and demonstrating analysis methods.
## License
MIT 

## Citation

**Petalcorin, M.I.R.** (2026). Endocarp-modulated drying kinetics predict a critical moisture threshold, membrane failure, and metabolic collapse in recalcitrant mango seeds. GitHub. https://github.com/mpetalcorin/recalcitrant-seed-drying-simulator
