# Solving_Differential_Equations_Using_Machine_Learning

This repository contains the implementation of a Physics-Informed Neural Network (PINN) to approximate the wavefunctions of the quantum harmonic oscillator (QHO) for various angular frequencies (ω) and quantum numbers (n). The PINN framework integrates the Schrödinger equation directly into the loss function to guide the learning process with physical laws.

## Project Objective

To demonstrate that physics-guided deep learning can generalize quantum mechanical solutions across various states, accurately predicting the wavefunction ψ(q, n, ω) of a quantum harmonic oscillator without solving the Schrödinger equation analytically each time.

## Key Concepts

- **Physics-Informed Neural Network (PINN)**: Embeds the Schrödinger equation as a soft constraint during training.
- **Quantum Harmonic Oscillator (QHO)**: A fundamental quantum system with known analytical solutions.
- **Generalization**: Predicts wavefunctions for unseen quantum states using trained models.

## Model Architecture

- Input: `(n, q, ω)`
- Output: Wavefunction value `ψ(q, n, ω)`
- Layers: 3 hidden layers with 128 neurons each
- Activation: `tanh`
- Loss Function = Physics Loss + Data Loss + Boundary Loss + Normalization Loss
- Optimizer: Adam (Learning rate: 2e-3)
- Epochs: 80,000 | Batch Size: 256
- Framework: PyTorch

## Training & Testing

- Trained on: `n ∈ {0, 1, 3, 4, 6, 7}`, `ω ∈ [0.5, 1.5]`
- Tested on unseen `n ∈ {2, 5}`
- Domain: `q ∈ [-5, 5]`
- Symmetry enhancement (mirroring) improves accuracy on test data.

## Results

- Accurate prediction of wavefunctions for both trained and unseen quantum numbers.
- High R² scores showing reliable performance.
- PINNs with parity symmetry generalize better.
