# L01 — Exploring Deep Learning Tools: A No-Code Introduction to TensorFlow and Keras

**Course:** ITAI 2376 — Deep Learning | Houston City College  
**Submitted:** February 14, 2026  

---

## Overview

This lab provided hands-on exposure to the foundational tools of the deep learning ecosystem — TensorFlow and Keras — without requiring low-level coding from scratch. The focus was on understanding the workflow of a deep learning project from data loading through model prediction.

## What Was Covered

- Loaded and explored the pre-trained VGG16 model and its architecture
- Understood the role of input, hidden, and output layers in a deep neural network
- Performed data loading and preprocessing for image classification
- Used the pre-trained model to make predictions on uploaded images
- Explored how input modifications (rotation, noise) affect model predictions
- Reflected on the relationship between preprocessing quality and model performance

## Key Concepts

**Transfer Learning:** VGG16 was pre-trained on ImageNet (1.2M images, 1000 classes). Using it without retraining demonstrates how pre-learned feature representations can be applied to new inputs immediately.

**Data Preprocessing:** Images must be resized to 224×224, converted to arrays, and normalized before VGG16 can process them — a critical step that directly affects prediction quality.

**Model Sensitivity:** Small input changes (rotation, noise) can significantly shift confidence scores, illustrating why robust preprocessing pipelines matter in production systems.

## Technologies Used

- Python, TensorFlow 2.x, Keras
- VGG16 (ImageNet pre-trained weights)
- Google Colab (T4 GPU)
- NumPy, Matplotlib

## How to Run

Open the notebook in Google Colab:
1. Upload `L01_YoanaCook_ITAI2376.ipynb`
2. Runtime → Change runtime type → GPU (T4)
3. Run all cells top to bottom
