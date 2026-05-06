# A03 — Deep Learning for an 11-Year-Old: Understanding Backpropagation

**Course:** ITAI 2376 — Deep Learning | Houston City College  
**Team:** Team 02 (Francisco Medina, Rida Kashan, Richard Rodriguez, Yoana Cook)  
**Submitted:** April 8, 2026

---

## Overview

A professionally designed presentation that explains backpropagation — one of deep learning's most mathematically dense concepts — using child-friendly analogies and visuals, without sacrificing conceptual accuracy. The challenge: make it genuinely understandable to an 11-year-old while remaining technically correct.

## The Approach

Rather than simplifying to the point of inaccuracy, the presentation maps each technical concept to a concrete real-world analogy:

| Technical Concept | Analogy Used |
|------------------|--------------|
| Forward pass | Making a guess on a quiz |
| Loss / error | Measuring how wrong the guess was |
| Backpropagation | Tracing backward to find who is most responsible for a burnt cake |
| Gradient descent | Nudging connection weights by tiny amounts |
| Training epochs | Practicing until you can ride a bike without wobbling |

## Slides Covered

1. How humans learn vs. how computers learn
2. What a neural network is (web of connected nodes)
3. How neural networks make guesses
4. Making mistakes and measuring error
5. The "Oops Moment" — error as a number that drives learning
6. Backpropagation: sending error backward layer by layer
7. The forward/backward pass diagram with explicit weight adjustment flow
8. Fixing mistakes step by step (gradient descent)
9. Trying again and getting smarter (training loop)
10. Conclusion: the full loop in plain English
11. References (6 academic sources, no Wikipedia)

## Key Takeaway

Backpropagation = guess → measure error → send it back → adjust → repeat. The power is that it doesn't just say "that was wrong, try again" — it pinpoints exactly which connections caused the error and by exactly how much.

## Files

- `A03_team02_YoanaCook_ITAI2376.pdf` — Full presentation (18 slides)

## Technologies Referenced

TensorFlow automatic differentiation, chain rule, gradient descent, MSE loss
