# L02 — Neural Networks from Scratch to Frameworks

**Course:** ITAI 2376 — Deep Learning | Houston City College  
**Submitted:** January 26, 2026  

---

## Overview

This lab bridged the gap between understanding neural networks conceptually and implementing them using modern frameworks. Starting from a manual implementation and progressing to TensorFlow/Keras, the lab built intuition for what frameworks are actually doing under the hood.

## What Was Covered

- Built a simple neural network from scratch using NumPy (forward pass, loss calculation, backpropagation, weight updates)
- Reproduced the same network in TensorFlow/Keras to compare implementations
- Explored how activation functions (ReLU, sigmoid, softmax) affect learning behavior
- Analyzed training curves and the effect of learning rate on convergence

## Key Concepts

**Backpropagation from Scratch:** Implementing gradient descent manually — computing partial derivatives layer by layer — makes the chain rule concrete rather than abstract. This is the engine behind every modern deep learning framework.

**Framework Abstraction:** Keras condenses dozens of lines of manual NumPy code into a few lines, but the underlying math is identical. Understanding both levels is what separates engineers who can debug models from those who can only run them.

**Hyperparameter Sensitivity:** Small changes to learning rate produce dramatically different training behavior — too high causes divergence, too low causes slow or stuck training.

## Technologies Used

- Python, NumPy, TensorFlow 2.x, Keras
- Matplotlib (training curve visualization)
- Google Colab

## How to Run

Open `Module_02_Lab_YoanaCook_ipynb.ipynb` in Google Colab and run all cells top to bottom.
