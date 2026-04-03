# Suggested Improvements for Hands-On Sessions

This document outlines ideas to improve the hands-on sessions for Variational Autoencoders (VAE) and Conditional Variational Autoencoders (CVAE).

## 1. Visualizing the 2D Latent Space (`hands-on/VAE_hands_on.ipynb`)
Since the concept of a continuous latent space is central to VAEs, visualizing it helps students grasp the intuition.
*   **Grid Search Generation**: Add an optional task or demonstration where students set `latent_dim=2` and generate a grid of digits by scanning the 2D space (e.g., from -3 to 3 on both axes). This shows the smooth morphing of shapes.
*   **Scatter Plot**: Plot the test set samples in the 2D latent space colored by digit label. This illustrates how the VAE naturally clusters similar digits while maintaining a continuous space.

## 2. Style Transfer / Latent Analogy (`hands-on/CVAE_hands_on.ipynb`)
CVAEs disentangle style (latent variable $z$) and content (label $c$).
*   **Suggested Task**: Instruct students to take a latent vector $z$ that produces a specific style (e.g., a heavily slanted digit) and use it to generate different digits by changing only the condition $c$. This proves that $z$ captures style characteristics independent of the digit class.

## 3. Fashion-MNIST as a Stepping Stone to CIFAR-100
Both notebooks suggest extending the implementation to CIFAR-100 in TODO-3.
*   **Recommendation**: CIFAR-100 is quite challenging for a basic VAE because of the 3 color channels and complex shapes.
*   Add a note suggesting **Fashion-MNIST** as an alternative or intermediate step. It uses the same dimensions (28x28 grayscale) as MNIST but features complex clothing items, providing a higher challenge without requiring a drastic change in model architecture.

## 4. Interactive Exploration with Widgets
*   Suggest using `ipywidgets` for latent traversal or selecting digits to generate interactively, adding an engaging element to the notebook.

---

## 📝 Deployment Checklist
Before releasing to students, remember the guidelines from `docs/hands_on_formating.md`:
1.  **Clear all outputs** to keep file sizes small.
2.  **Verify notebook versions** are set correctly to avoid GitHub preview errors (`nbformat_minor: 5`).
3.  Ensure the submission deadline and link are updated in both files.
