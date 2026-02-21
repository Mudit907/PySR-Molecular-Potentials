# Symbolic Discovery of Inter-atomic Potentials (SDIP)

[![Python](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/)
[![PySR](https://img.shields.io/badge/ML-Symbolic%20Regression-orange.svg)](https://github.com/MilesCranmer/PySR)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

## 📌 Project Overview
This repository implements a **Physics-Informed Machine Learning** pipeline designed to extract human-readable mathematical laws from noisy molecular dynamics data. While Deep Neural Networks (DNNs) excel at interpolation, they often fail to respect physical boundaries in "Out-of-Distribution" scenarios. 

This project utilizes **Symbolic Regression (PySR)** to discover the underlying functional forms of inter-atomic potentials, specifically targeting the recovery of **Lennard-Jones** style interactions from stochastic datasets.

## 🚀 Key Research Contributions

* **Symmetry-Preserving Engineering:** Transformed raw Cartesian coordinates into pairwise distance matrices to enforce rotational and translational invariance.
* **The "Danger Zone" Benchmark:** Demonstrated that symbolic models correctly capture **Pauli Repulsion** ($E \propto r^{-n}$) in extrapolation zones where standard Neural Networks (MLPs) produce non-physical linear artifacts.
* **Pareto Optimization:** Leveraged evolutionary algorithms to identify the "Optimal Trade-off" between equation complexity and mean squared error (MSE).
* **Noise Resilience:** Successfully recovered the $1/r$ functional signal from datasets containing up to 20% additive Gaussian noise.

## 📊 Results & Visualization

### 1. The Pareto Front
We identify the "Physical Law" not by the lowest error alone, but by the "elbow" in the Pareto Front, where accuracy meets mathematical simplicity.

### 2. Extrapolation Power (The Special Sauce)
This plot illustrates why this work is superior to "Black Box" AI. In the **unseen "Danger Zone"** (where atoms get dangerously close), the Symbolic Model respects physics while the Neural Network fails.


## 🛠️ Technical Stack
* **Symbolic Engine:** [PySR](https://github.com/MilesCranmer/PySR) (High-performance Symbolic Regression via Julia)
* **Learning Baselines:** Scikit-Learn (MLPRegressor)
* **Scientific Computing:** NumPy, SymPy, Pandas
* **Data Visualization:** Matplotlib, Seaborn

## 📖 Methodology
1.  **Data Generation:** Synthetic potentials were generated using a modified 12-6 Lennard-Jones basis with added stochastic noise.
2.  **Feature Transformation:** Coordinates $R \in \mathbb{R}^{3}$ were mapped to a distance manifold $d_{ij} = ||r_i - r_j||$.
3.  **Evolutionary Search:** Populations of mathematical expressions were evolved over 100+ generations using tournament selection.
4.  **Validation:** Models were validated using parity plots and residual distribution analysis.

---
**Author:** Mudit Srivastava
**Topic:** Machine Learning for Physics / Molecular Modeling
