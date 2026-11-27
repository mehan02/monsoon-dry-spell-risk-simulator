# Monsoon Dry-Spell Risk Simulation in Colombo and Hambantota

This project studies monsoon dry-spell risk in Colombo and Hambantota, Sri Lanka, using historical daily precipitation and stochastic simulation. It compares first-order and second-order Markov-chain models for wet-day occurrence, fits distributions to wet-day rainfall amounts, and evaluates simulated seasonal dry-spell statistics against historical observations.

## Google Colab notebook

**Open the project notebook in Google Colab:**

[SE4042 Monsoon Dry-Spell Simulation – Colab](https://colab.research.google.com/drive/1be2XYEVDYAYhvU9g68FUrforvt-3fqmk?usp=sharing)
[SE4042 Monsoon Dry-Spell Simulation – WebDemo](https://mehan02.github.io/monsoon-dry-spell-risk-simulator/)

### Run in Colab

1. Open the Colab link above.
2. If you only have viewing access, choose **File → Save a copy in Drive** to create your own editable copy.
3. In the notebook, choose **Runtime → Run all**. Run cells from top to bottom; the notebook retrieves historical precipitation data from the Open-Meteo Historical Weather API, so an internet connection is required.
4. Wait for the data retrieval, model fitting, simulation, verification tests, plots and result tables to finish.
5. Review the printed verification checks and generated results. If a cell fails, read the error message and rerun after correcting the issue or restarting the runtime.

The notebook is designed to run in Colab without manually uploading the rainfall dataset. The analysis uses a fixed seed configuration for reproducibility, while the experiment also uses multiple seeds to estimate uncertainty.

## Run locally

### Requirements

- Python 3.9 or later recommended
- Internet connection (historical precipitation data is retrieved from the Open-Meteo API)
- Jupyter Notebook or JupyterLab

### 1. Download the notebook

Download the `.ipynb` notebook from the project files or from Google Colab using **File → Download → Download .ipynb**.

### 2. Create and activate a virtual environment

**macOS / Linux**

```bash
python3 -m venv .venv
source .venv/bin/activate
```

**Windows (PowerShell)**

```powershell
py -m venv .venv
.venv\Scripts\Activate.ps1
```

### 3. Install dependencies

```bash
python -m pip install --upgrade pip
python -m pip install numpy pandas matplotlib scipy requests jupyter
```

### 4. Launch Jupyter

From the folder containing the downloaded notebook, run:

```bash
jupyter notebook
```

Alternatively, launch JupyterLab:

```bash
jupyter lab
```

Open the notebook in the browser, select the Python environment you created, and use **Run → Run All Cells** (or the equivalent menu command). Execute cells in order from the beginning so variables and functions are defined before they are used.

## Project scope and methods

- **Locations:** Colombo and Hambantota, Sri Lanka
- **Data:** Daily precipitation from the Open-Meteo Historical Weather API (ERA5-based historical data)
- **Study period:** December 1990 to September 2020
- **Wet-day threshold:** Daily precipitation of at least 1 mm
- **Seasons:** Southwest monsoon (May–September) and northeast monsoon (December–February)
- **Occurrence models:** First-order and second-order Markov chains
- **Rainfall amount models:** Gamma and lognormal distributions fitted to wet-day amounts using threshold-truncated likelihood
- **Experiments:** Seasonal dry-spell statistics, including the probability of at least one dry spell of seven or more consecutive days and mean longest dry-spell length
- **Uncertainty:** Replicated simulations using multiple random seeds and confidence intervals across seed-level estimates
- **Verification:** Transition-matrix checks, synthetic parameter recovery, theoretical versus simulated checks and dry-spell edge cases

## Data source

Historical precipitation is requested from the Open-Meteo Historical Weather API. Data access requires an internet connection. The notebook contains the data request and processing steps, including the locations and date range used.

- Open-Meteo Historical Weather API: https://open-meteo.com/en/docs/historical-weather-api

## Reproducibility

The notebook sets a seed for reproducibility and runs replicated simulations across a collection of seeds. Exact outputs may vary if the notebook, libraries, API data or execution environment change. For reproducible results, rerun all cells in sequence in a fresh runtime and retain the generated output tables and plots with the notebook.

## Notes

This is an academic simulation project. The results describe model-based estimates for the locations and seasonal definitions studied. They should not be interpreted as deterministic weather forecasts or as a substitute for official climate-risk assessments.
