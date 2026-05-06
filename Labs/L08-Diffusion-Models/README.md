# L08 — Diffusion Models

**Course:** ITAI 2376 — Deep Learning | Houston City College  
**Submitted:** March 21, 2026  

---

## Overview

This lab implemented a complete diffusion model pipeline from scratch — including the forward noise process, a U-Net denoising architecture, and image generation via iterative denoising. The model was trained on MNIST digit data using a T4 GPU on Google Colab.

McManus's feedback: *"Yoana, great submission. You ran MNIST on the T4 GPU, trained successfully to epoch 27 with a final training and validation loss of 0.0560 and 0.0561, ran CLIP..."*

## What Was Covered

- Implemented the **forward diffusion process**: progressively adding Gaussian noise to images over 100 timesteps using the closed-form equation `x_t = √ᾱ_t · x₀ + √(1−ᾱ_t) · ε`
- Built a **U-Net architecture** with skip connections, GELUConvBlocks, and time/class conditioning
- Implemented the **training loop**: random timestep sampling, noise prediction, MSE loss
- Generated MNIST digits via iterative denoising from pure noise
- Evaluated generated image quality using **CLIP embeddings**
- Visualized the noise progression and denoising trajectory

## Key Concepts

**Forward Diffusion:** Noise is added gradually, not all at once. Each step changes the image by a small amount, enabling the model to learn to undo each small step — a far more tractable problem than reversing complete destruction.

**U-Net for Denoising:** U-Net's encoder-decoder structure with skip connections is ideal because the output must match the input resolution (predicting noise at every pixel), while the multi-scale processing captures both fine details and global structure simultaneously.

**Score Matching:** The model doesn't generate images directly — it learns to predict the noise that was added at each timestep. Generation is then the iterative reversal of this process.

## Training Results

- Trained to epoch 27 on T4 GPU
- Final training loss: 0.0560
- Final validation loss: 0.0561 (near-perfect generalization, no overfitting)

## Technologies Used

- Python, PyTorch, einops
- U-Net with GELU activations, GroupNorm, time/class conditioning
- CLIP (OpenAI) for generation quality evaluation
- Google Colab (T4 GPU)

## How to Run

Open `MD_Notebook_Yoana_Cook_ITAI.ipynb` in Google Colab:
1. Runtime → Change runtime type → GPU (T4)
2. Run all cells top to bottom
3. Training takes approximately 20–30 minutes on a free T4
