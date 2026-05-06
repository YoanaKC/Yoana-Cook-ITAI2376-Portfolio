# L05 — RNN and Transformers

**Course:** ITAI 2376 — Deep Learning | Houston City College  
**Submitted:** February 24, 2026

---

## Overview

This lab explored sequential data modeling through two architectures that represent the evolution of the field: Recurrent Neural Networks (RNNs) and the Transformer architecture that has since replaced them for most NLP tasks.

## What Was Covered

- Implemented a Recurrent Neural Network for sequence modeling tasks
- Explored the vanishing gradient problem that limits standard RNNs
- Implemented LSTM (Long Short-Term Memory) cells to handle longer sequences
- Explored the Transformer architecture: self-attention, positional encoding, encoder-decoder structure
- Compared RNN and Transformer approaches on sequence tasks

## Key Concepts

**RNN Sequential Processing:** RNNs process input one token at a time, passing a hidden state forward. This creates a memory of past inputs but makes training difficult on long sequences because gradients shrink (or explode) as they backpropagate through many timesteps.

**LSTM Gates:** LSTMs solve the vanishing gradient problem by adding a cell state with explicit gates (input, forget, output) that control what information is kept, discarded, or passed forward. This is the architecture underlying GridGuard-AI's load forecasting component.

**Self-Attention:** Transformers abandon sequential processing entirely. Every token attends to every other token simultaneously, capturing long-range dependencies in a single step. This is what powers GPT, BERT, and the LLMs used in GridGuard-AI's agent reasoning layer.

## Connection to Final Project

The LSTM architecture studied in this lab is directly implemented in GridGuard-AI's Grid Monitor agent, which uses an LSTM model to forecast ERCOT grid load 4 hours ahead with a mean absolute error of 2.37% of peak load.

## Technologies Used

- Python, TensorFlow 2.x, Keras
- NumPy, Matplotlib
- Google Colab

## How to Run

Open `L05_Yoana_Cook_ITAI2376.ipynb` in Google Colab and run all cells top to bottom.
