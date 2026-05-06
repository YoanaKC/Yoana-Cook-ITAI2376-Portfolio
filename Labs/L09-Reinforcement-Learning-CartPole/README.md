# L09 — Reinforcement Learning: Teach an Agent to Balance a Pole

**Course:** ITAI 2376 — Deep Learning | Houston City College  
**Submitted:** March 30, 2026

---

## Overview

This lab implemented a Q-Learning agent to solve the CartPole-v1 environment — a classic reinforcement learning benchmark where an agent learns to balance a pole on a moving cart through trial, error, and reward-based learning.

McManus's feedback noted: *"...reflects the depth brought to every assignment. All code cells run, outputs are visible, and show genuine..."*

## What Was Covered

**Part 1 — Random Agent Baseline**
- Ran a random agent in CartPole to observe unguided failure behavior
- Analyzed state space (cart position, velocity, pole angle, angular velocity) and action space (push left/right)

**Part 2 — Q-Learning Agent**
- Trained a Q-Learning agent for 500 episodes
- Built a Q-table mapping state-action pairs to expected rewards
- Implemented epsilon-greedy exploration with decay (ε: 0.5 → 0.01)
- Compared different exploration rates through controlled experimentation
- Wrote and tested hypothesis before running experiments

**Part 3 — RLHF Connection**
- Connected CartPole's reward loop to Reinforcement Learning from Human Feedback (RLHF)
- Analyzed how the same RL principles underlying CartPole training are used to align LLMs like GPT and Claude
- Applied RLHF concepts to GridGuard-AI agent design

## Key Concepts

**Q-Table:** Stores expected cumulative reward for every (state, action) pair. Updated via the Bellman equation: `Q(s,a) ← Q(s,a) + α[r + γ·max Q(s',a') − Q(s,a)]`

**Exploration vs. Exploitation:** High epsilon = random exploration (discovers new strategies). Low epsilon = exploiting learned knowledge. Annealing epsilon over training balances both phases.

**RLHF Connection:** The reward signal in CartPole (stay upright = +1) is structurally identical to human preference feedback in RLHF. The LLMs powering GridGuard-AI's agents were all trained using this same feedback loop.

## Connection to Final Project

Understanding the RL reward loop directly informed the design of GridGuard-AI's dispatch agent, which must balance competing objectives (grid stability, cost, compliance) — a multi-objective reward problem.

## Technologies Used

- Python, OpenAI Gymnasium (CartPole-v1)
- NumPy, Matplotlib
- Google Colab

## How to Run

Open `L09_YoanaCook_ITAI_2376.ipynb` in Google Colab and run all cells top to bottom.
