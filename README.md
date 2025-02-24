# Manual Calibration of an SIR Model

This repository contains two Jupyter notebooks that demonstrate the manual calibration of a Susceptible-Infected-Recovered (SIR) model using epidemic data. The notebooks are part of a series that explores the process of fitting an SIR model to real-world data by adjusting the parameters β (infection rate) and γ (recovery rate).

## Notebook 1: Initial Calibration

### Overview
The first notebook introduces the SIR model and demonstrates how to manually calibrate it using early epidemic data. The goal is to find the best values for β and γ that fit the initial growth phase of the epidemic.

### Key Steps:
1. **Model Setup**: The SIR model is defined using a system of differential equations.
2. **Data Preparation**: Initial epidemic data is provided, showing the number of infected individuals over the first few days.
3. **Manual Calibration**: The parameters β and γ are manually adjusted to fit the model to the initial data.
4. **Visualization**: The model's output is plotted against the actual data to assess the fit.

### Key Findings:
- The initial calibration process reveals that multiple combinations of β and γ can fit the early epidemic data, indicating that more data is needed to uniquely determine these parameters.

## Notebook 2: Extended Calibration

### Overview
The second notebook extends the calibration process using a more comprehensive dataset that covers the entire epidemic curve. This allows for a more accurate determination of β and γ.

### Key Steps:
1. **Extended Data**: A full dataset of the epidemic, covering 14 days, is introduced.
2. **Model Recalibration**: The SIR model is run again with the previously found parameters to see if it fits the extended data.
3. **Refinement**: The parameters β and γ are further adjusted to better fit the entire epidemic curve.
4. **Visualization**: The model's output is plotted against the full dataset to evaluate the fit.

### Key Findings:
- The initial parameters found in Notebook 1 do not fit the later stages of the epidemic well, highlighting the importance of using comprehensive data for calibration.
- By manually adjusting β and γ, a better fit to the full epidemic curve is achieved.

## Usage
To run the notebooks, ensure you have the following Python packages installed:
- `deSolve`
- `reshape2`
- `ggplot2`

You can install these packages using the following R commands:
```R
install.packages("deSolve")
install.packages("reshape2")
install.packages("ggplot2")
```

## Contributing
Feel free to fork this repository and contribute by improving the model, adding new datasets, or enhancing the calibration process. Pull requests are welcome!
