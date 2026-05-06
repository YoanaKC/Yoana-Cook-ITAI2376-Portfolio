# L03 — CNN & Transfer Learning (VGG16)

**Course:** ITAI 2376 — Deep Learning | Houston City College  
**Submitted:** February 5, 2026  

---

## Overview

This lab implemented both a Convolutional Neural Network (CNN) built from scratch and a transfer learning model using the pre-trained VGG16 architecture. McManus's feedback: *"Wow Yoanna, Outstanding Job! You clearly put serious effort into this lab. Your CNN from scratch and transfer learning implementation both demonstrate that you..."*

## What Was Covered

- Designed and trained a CNN from scratch for image classification
- Applied transfer learning using VGG16 with fine-tuning on a custom dataset
- Compared performance between the from-scratch CNN and the transfer learning approach
- Visualized feature maps to understand what convolutional filters detect
- Analyzed accuracy/loss curves across training epochs

## Key Concepts

**Convolutional Layers:** Unlike fully connected layers, convolutional layers preserve spatial relationships in images. Each filter slides across the image detecting specific features — edges, textures, shapes — at increasing levels of abstraction in deeper layers.

**Transfer Learning:** VGG16's early layers detect universal low-level features (edges, gradients) regardless of the original training domain. Freezing these layers and only training the final classifier layers is far more efficient than training from scratch, especially with limited data.

**Feature Map Visualization:** Inspecting intermediate layer activations reveals what the network has learned to detect — a powerful debugging and interpretability tool.

## Results

Transfer learning with VGG16 significantly outperformed the from-scratch CNN in both accuracy and training speed, demonstrating the practical value of pre-trained weights on real classification tasks.

## Technologies Used

- Python, TensorFlow 2.x, Keras
- VGG16 (ImageNet weights)
- NumPy, Matplotlib, OpenCV
- Google Colab (T4 GPU)

## How to Run

Open `Module_03_Lab_Yoana_Cook.ipynb` in Google Colab:
1. Runtime → Change runtime type → GPU (T4)
2. Run all cells top to bottom
3. All outputs and visualizations are pre-rendered in the notebook
