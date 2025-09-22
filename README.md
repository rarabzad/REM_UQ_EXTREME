# UQ-flood: An Uncertainty Quantification Framework for Simulation-based Flood Frequency Analysis

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

## Overview

This repository contains the code and data for the paper **"An Uncertainty Quantification Framework for Simulation-based Flood Frequency Analysis"** by Romero-Cuellar et al. (2025, submitted to *Water Resources Research*).  
The UQ-flood framework integrates process-based hydrological modeling, stochastic weather generation, and residual error modeling to provide robust flood frequency estimates with quantified uncertainty.

## Key Features

- **Process-based hydrologic modeling** using HBV-EC within the Raven framework  
- **Residual Error Model (REM)** for uncertainty quantification at annual maxima scale  
- **Stochastic weather generation** using CoSMoS for long-term climate simulation  
- **Comparative analysis** against traditional statistical FFA methods (GEV distribution)  
- **Modular framework** applicable to diverse watershed conditions  

## Repository Structure

```

UQ-flood/
├── data/
│   ├── blackriver\_results.RData          # Main results and processed data
│   ├── ForcingFunctions.csv              # Meteorological forcing data
│   ├── Hydrographs\_baseline.csv          # Calibration period hydrographs
│   └── Hydrographs\_longterm.csv          # Long-term simulation results
├── src/
│   └── MasterScriptRepro.R               # Master reproduction script
├── docs/
│   ├── methodology.md                    # Detailed methodology
│   └── case\_studies.md                   # Case study descriptions
├── output/
│   ├── figures/                          # Generated figures and plots
│   └── results/                          # Analysis results
└── README.md

````

## Case Study: Black River Watershed

The primary case study focuses on the Black River near Washago, Ontario (Water Survey of Canada gauge 02EC002), featuring:  
- Watershed area: 1,506 km²  
- Streamflow record: 100+ years (1916–present)  
- Mixed hydrologic regime (nival fraction ≈ 0.7)  
- Minimal anthropogenic regulation  

## Quick Start

### Prerequisites
- R (version 4.0 or higher)  
- Required R packages (see Installation section)  

### Installation
1. Clone the repository:
```bash
git clone https://github.com/rarabzad/REM_UQ_EXTREME.git
cd UQ-flood
````

2. Install required R packages by running the package installation section in `MasterScriptRepro.R`.

### Basic Usage

Run the master script to reproduce the analysis:

```r
source("src/MasterScriptRepro.R")
```

This will:

1. Load and preprocess the data
2. Calibrate the hydrological model
3. Set up the residual error model
4. Generate stochastic weather sequences
5. Perform flood frequency analysis
6. Generate comparative plots and results

## Methodology

The UQ-flood framework consists of three main components:

### 1. Hydrological Model (HBV-EC)

* Lumped conceptual model implemented in Raven
* Calibrated using Kling-Gupta Efficiency (KGE) objective function
* Simulates snow accumulation/melt, soil moisture, and runoff generation

### 2. Residual Error Model (REM)

* Box-Cox transformation (λ=0.2) with AR(1) structure
* Flow-dependent error mean
* Developed specifically for annual maximum flows
* Generates probabilistic streamflow ensembles

### 3. Stochastic Weather Generator (CoSMoS)

* Multivariate non-Gaussian time series simulation
* Preserves marginal distributions and autocorrelation structures
* Generates 10,000+ years of synthetic climate data

## Key Results

The framework demonstrates:

* **Reduced uncertainty**: Narrower confidence intervals compared to traditional FFA
* **Data efficiency**: Reliable estimates with only 30 years of data
* **Bias correction**: Effective mitigation of systematic model errors
* **Process consistency**: Physically-based uncertainty quantification

## Outputs

The analysis generates several key outputs:

1. **Flood frequency curves** with uncertainty bounds
2. **Comparative plots** between UQ-flood and traditional methods
3. **Performance metrics** (KGE, NSE, PBIAS, CRPS)
4. **Uncertainty quantification** (95% prediction intervals)

## File Descriptions

### Data Files

* `blackriver_results.RData`: Results object with model outputs, REM parameters, and analysis results
* `ForcingFunctions.csv`: Historical meteorological data (precipitation, temperature)
* `Hydrographs_baseline.csv`: Observed and simulated streamflow for calibration
* `Hydrographs_longterm.csv`: Long-term simulation results (10,000 years)

### Code Files

* `MasterScriptRepro.R`: Main reproduction script with complete workflow

## Citation

If you use this code or data in your research, please cite:

```bibtex
@article{romerocuellar2025uqflood,
  title={An Uncertainty Quantification Framework for Simulation-based Flood Frequency Analysis},
  author={Romero-Cuellar, Jonathan and Craig, James R. and Tolson, Bryan A. and Arabzadeh, Rezgar},
  journal={Water Resources Research},
  year={2025},
  note={submitted}
}
```

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Acknowledgments [*tentative*]

This research was supported by the Natural Sciences and Engineering Research Council of Canada (NSERC) and the University of Waterloo

## Contact

* Jonathan Romero-Cuellar: [jromeroc@uwaterloo.ca](mailto:jromeroc@uwaterloo.ca) (corresponding author)

## Related Publications

For more details on the methodology, see:

* Romero-Cuellar et al. (2024) – Residual error modeling in hydrological prediction
* Hunter et al. (2021) – Error model formulations
* Papalexiou (2018) – CoSMoS weather generator



