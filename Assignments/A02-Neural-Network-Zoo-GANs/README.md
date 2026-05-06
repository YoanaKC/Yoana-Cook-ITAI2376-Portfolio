# A02 — Neural Network Zoo: Generative Adversarial Networks (GANs)

**Course:** ITAI 2376 — Deep Learning | Houston City College  
**Team:** Team 02 (Francisco Medina, Rida Kashan, Richard Rodriguez, Yoana Cook)  
**Submitted:** January 31, 2026

---

## Overview

An interactive presentation exploring Generative Adversarial Networks through the metaphor of the mimic octopus — a natural creature that generates convincing imitations of other species to survive, mirroring how a GAN's generator learns to fool its discriminator.

## The Analogy

The **mimic octopus** (*Thaumoctopus mimicus*) survives by imitating lionfish, flatfish, and sea snakes convincingly enough to fool predators. This maps directly to GAN architecture:

| Octopus | GAN |
|---------|-----|
| Mimic generates a disguise | Generator produces fake samples |
| Predator evaluates authenticity | Discriminator classifies real vs. fake |
| Octopus improves imitation from feedback | Generator improves from discriminator's signals |
| Eventually indistinguishable | Generator output matches real data distribution |

## What Was Covered

- Neural network foundations and how GANs fit within the broader deep learning landscape
- GAN architecture: Generator network, Discriminator network, adversarial training loop
- The Nash equilibrium concept — when training converges and why it's difficult to achieve
- Real-world GAN applications: art generation, medical imaging, data augmentation, deepfakes
- Ethical implications of generative AI

## Key Concepts

**Adversarial Training:** The generator and discriminator are trained simultaneously in opposition. The generator tries to maximize the discriminator's error; the discriminator tries to minimize it. This adversarial dynamic drives both networks to improve.

**Mode Collapse:** A common GAN failure mode where the generator learns to produce only a narrow range of outputs that fool the discriminator, rather than the full diversity of the training distribution.

**Applications:** GANs power image synthesis (DALL-E predecessors), medical scan augmentation, video game texture generation, and face anonymization tools.

## Files

- `A02_Team2_ITAI2376.html` — Interactive ocean-themed presentation (open in any browser)
- `A02_Team2_Reflection_YoanaCook.docx` — Individual reflection on neural network types and GAN research

## How to View

Open `A02_Team2_ITAI2376.html` in any web browser. Use arrow keys or navigation buttons to advance slides.
