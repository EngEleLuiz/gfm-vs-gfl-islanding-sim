# Microgrid Control Dynamics: GFL vs. GFM

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![License](https://img.shields.io/badge/License-MIT-green)
![Status](https://img.shields.io/badge/Status-Completed-success)

## ⚡ Project Overview

This repository contains a technical analysis and dynamic simulation of power electronic inverters transitioning from **Grid-Connected** to **Islanded** mode. 

The project contrasts two dominant control architectures:
1.  **Grid-Following (GFL):** Relies on a Phase-Locked Loop (PLL) and current injection.
2.  **Grid-Forming (GFM):** Utilizes Virtual Synchronous Machine (VSM) and Droop Control concepts to establish voltage and frequency.

The simulation demonstrates the "Loss of Mains" event, highlighting the instability of GFL systems in weak/isolated grids versus the inherent stability of GFM controls.

## 📊 Simulation Results

*(Upload a screenshot of your Matplotlib plots here and link it)*
![Simulation Preview](simulation_results.png)

> **Key Observation:** The Grid-Following unit experiences rapid frequency drift upon islanding due to the loss of the PLL reference. The Grid-Forming unit instantly assumes the load, with frequency dynamics dictated by the virtual inertia constant ($J$) and damping ($D_p$).

## 🛠 Technical Implementation

The simulation is built entirely in Python using `scipy.integrate.solve_ivp` to solve the non-linear differential equations of the control loops.

### Control Models
* **GFL:** Modeled with a standard SRF-PLL (Synchronous Reference Frame Phase-Locked Loop) approximation.
* **GFM:** Modeled using the Swing Equation (Virtual Inertia) + Primary Droop ($P-\omega$) + Secondary AGC (Integral Restoration).

### Key Equations (Grid-Forming VSM)
The GFM dynamics are governed by the swing equation:

$$J \dot{\omega} = P_{set} - P_{meas} - D_p(\omega - \omega_{ref})$$

Where:
* $J$: Virtual Inertia
* $D_p$: Damping Factor
* $P_{set}$: Active Power Setpoint

## 🚀 How to Run

1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/yourusername/microgrid-dynamics-python.git](https://github.com/yourusername/microgrid-dynamics-python.git)
    ```
2.  **Install dependencies:**
    ```bash
    pip install numpy matplotlib scipy jupyter
    ```
3.  **Launch Jupyter:**
    ```bash
    jupyter notebook
    ```
4.  Open `Microgrid_Dynamics_Sim.ipynb` and run all cells.

## 📁 Repository Structure
