# README for Mod_2_notebook_1_Manual_Calibration_of_an_SIR_Model_Part_1

## Overview

This document is a notebook that guides you through the process of manually calibrating a simple SIR (Susceptible-Infectious-Recovered) model to fit real-world epidemic data. The notebook is part of a series of exercises designed to help you understand how to adjust model parameters to match observed data.

## Contents

1. **Introduction to Manual Calibration**
   - Explanation of the SIR model and its parameters.
   - Overview of the epidemic data provided.

2. **Data Visualization**
   - Plotting the epidemic curve to visualize the data.

3. **Model Setup**
   - Code for the SIR model using the `deSolve` package in R.
   - Initial state values and parameters.

4. **Manual Calibration Process**
   - Step-by-step instructions on how to manually adjust the parameters \(\beta\) (transmission rate) and \(\gamma\) (recovery rate) to fit the model to the data.
   - Examples of different parameter combinations and their effects on the model output.

5. **Visualization of Model Fit**
   - Plotting the model output alongside the observed data to assess the fit.
   - Iterative process of adjusting parameters to improve the fit.

6. **Conclusion**
   - Summary of the best parameter values found through manual calibration.
   - Reflection on the process and its implications for model accuracy.

## Usage

To use this notebook, you will need:

- **R** installed on your machine.
- The following R packages installed:
  - `deSolve`
  - `reshape2`
  - `ggplot2`

### Steps to Run the Notebook

1. **Install Required Packages**:
   ```R
   install.packages("deSolve")
   install.packages("reshape2")
   install.packages("ggplot2")
   ```

2. **Load the Packages**:
   ```R
   library(deSolve)
   library(reshape2)
   library(ggplot2)
   ```

3. **Run the Code Cells**:
   - Follow the instructions in the notebook to adjust the parameters \(\beta\) and \(\gamma\).
   - Visualize the model fit by running the plotting code.

4. **Experiment with Parameters**:
   - Try different values for \(\beta\) and \(\gamma\) to see how they affect the model output.
   - Compare the model predictions with the observed data to find the best fit.

## Example

Here is an example of how to set up and run the SIR model with initial parameters:

```R
# PACKAGES
require(deSolve)
require(reshape2)
require(ggplot2)

# INPUT
initial_state_values <- c(S = 762,
                          I = 1,
                          R = 0)

# Adding the parameters vector
parameters <- c(beta = 0.6,
                gamma = 0.1)

times <- seq(from = 0, to = 6, by = 0.1)

# MODEL FUNCTION
sir_model <- function(time, state, parameters) {
  with(as.list(c(state, parameters)), {
    N <- S + I + R
    lambda <- beta * I / N
    
    # The differential equations
    dS <- -lambda * S
    dI <- lambda * S - gamma * I
    dR <- gamma * I
    
    # Output
    return(list(c(dS, dI, dR)))
  })
}

# MODEL OUTPUT
output <- as.data.frame(ode(y = initial_state_values,
                            times = times,
                            func = sir_model,
                            parms = parameters))

# PLOT OF THE MODEL FIT
ggplot() +
  geom_line(data = output, aes(x = time, y = I)) +
  geom_point(data = data, aes(x = time, y = number_infected), colour = "red") +
  xlab("Time (days)") +
  ylab("Number of infected people") +
  labs(title = paste("Model fit to the epidemic curve with beta =", parameters["beta"], "and gamma =", parameters["gamma"]))
```

## Conclusion

This notebook provides a hands-on introduction to the process of manually calibrating an SIR model. By adjusting the parameters \(\beta\) and \(\gamma\), you can learn how to fit the model to real-world data and understand the dynamics of infectious disease spread.

For further exploration, consider automating the calibration process using optimization techniques, which will be covered in later exercises.

---

Feel free to contribute or suggest improvements to this notebook by opening an issue or pull request on GitHub.
