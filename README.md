# Quantum State Tomography with Conditional Generative Adversarial Networks (QST-CGAN)

This repository contains a data-driven approach to Quantum State Tomography (QST) using Conditional Generative Adversarial Networks (CGANs). The project was developed at the University of Milan and is inspired by the work of S. Ahmed et al., *"Quantum State Tomography with Conditional Generative Adversarial Networks"*, Phys. Rev. Lett. (2021).

## Overview

Quantum State Tomography is essential for characterizing and validating quantum hardware by reconstructing the density matrix of a quantum system from experimental measurements. Classical methods often suffer from exponential dimensional growth and extreme sensitivity to statistical noise (shot noise). 

This project overcomes these limitations by training a generative model (QST-CGAN) capable of reconstructing physically valid quantum states from noisy experimental measurements.

## Key Features

* **Dataset Generation:** Simulates realistic quantum measurements on 2-qubit systems across Pauli bases (Z, X, Y) with simulated shot noise (1024 shots) and uniform depolarizing noise.
* **Physics-Informed Layers:** 
  * *Density Matrix Layer:* Enforces physical constraints (positive semi-definite, trace = 1) using Cholesky decomposition.
  * *Expectation Layer:* Mathematically simulates the measurement process using Born's rule to compute expected probabilities.
* **Hyperparameter Optimization:** Utilizes `Optuna` to dynamically find the optimal network topology (hidden nodes) and training parameters (learning rates, $\lambda$ weight for the physical loss).
* **Early Stopping:** Automatically halts training to prevent overfitting by monitoring the Mean Squared Error (MSE) on a validation set.

## Results

* **High Fidelity:** Achieves an average reconstruction fidelity of **0.9989 ± 0.0015** on the test set.
* **Noise Resilience:** Maintains robust performance (Fidelity > 0.9950) even in critical regimes with as few as 64 measurement shots per base.
* **Generalization:** Successfully preserves the degree of purity of the original quantum states.

## Requirements

The project is built using Python. The required dependencies are:

* `torch` (PyTorch)
* `qutip` (Quantum Toolbox in Python)
* `numpy`
* `matplotlib`
* `scikit-learn`
* `optuna`

## Repository Structure

* `qst.ipynb`: The main Jupyter Notebook containing the dataset generation, model architecture, training loop, and evaluation/visualization of the results.
* `Quantum State Tomography with Conditional Generative Adversarial Networks.pdf`: The official project presentation slides detailing the theoretical background, network architecture, and experimental results.
* 
## Usage

1. Clone this repository.
2. Install the required dependencies.
3. Open the `qst.ipynb` notebook.
4. Run the cells sequentially to generate the dataset, perform Optuna hyperparameter search (optional), train the QST-CGAN, and visualize the reconstructed quantum states.
