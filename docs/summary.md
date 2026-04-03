# Summary of main.tex - Variational Autoencoders: Theory and Applications

This document provides a summary of the LaTeX slide deck `main.tex`, which covers the theory and applications of Variational Autoencoders (VAEs).

## Table of Contents
1. [Autoencoders & Introduction to VAEs](#autoencoders--introduction-to-vaes)
2. [Detailed Exploration of VAEs](#detailed-exploration-of-vaes)
3. [Loss Functions & Reconstruction Quality](#loss-functions--reconstruction-quality)
4. [Conditional VAEs (CVAEs)](#conditional-vaes-cvaes)
5. [Hands-On Sessions & Summary](#hands-on-sessions--summary)

---

## Autoencoders & Introduction to VAEs
This section recaps basic autoencoders and introduces the motivation for VAEs.

*   **Basic Autoencoder Recap**: Unsupervised learning model with an Encoder ($x \mapsto z$) and a Decoder ($z \mapsto \hat{x}$). It uses a deterministic framework to minimize reconstruction error.
*   **Bottleneck**: Forces the network to learn efficient representations by reducing dimensionality.
*   **Applications**:
    *   *Data Compression*: Compressing high-dimensional images (e.g., billing images) to a low-dimensional latent space.
    *   *Unsupervised Pre-training*: Training an encoder on large unlabeled data and using it for downstream classification tasks with limited labeled data.
*   **Motivation for Probabilistic Modeling**: Deterministic autoencoders cannot effectively generate new samples or capture uncertainty.
*   **VAE Fundamentals**: Combines autoencoder architecture with probabilistic latent variable modeling and variational inference. It encodes inputs to a distribution rather than a point.

## Detailed Exploration of VAEs
This section deep dives into the theory and implementation of VAEs.

*   **Probabilistic Latent Variable Model**: Aims to maximize the likelihood of observed data $p(x) = \int p(z)p(x|z)dz$, which is intractable. Solved using variational approximation $q(z|x)$.
*   **Encoder Network**: Maps inputs to parameters of a Gaussian distribution: Mean vector $\mu(x)$ and Log-variance vector $\log \sigma^2(x)$.
*   **Reparameterization Trick**: Solves the problem of non-differentiable sampling by expressing $z = \mu + \sigma \odot \epsilon$, where $\epsilon \sim \mathcal{N}(0, I)$. This enables backpropagation through stochastic nodes.
*   **Decoder Network**: Maps latent code $z$ to parameters of the data distribution $p(x|z)$ (e.g., Bernoulli for binary data, Gaussian for continuous data).
*   **Latent Space Operations**: Covers sampling from VAE and smooth interpolation between points in latent space.
*   **Architectures**: Discusses Multi-Layer Perceptron (MLP) and Convolutional (CNN) architectures, activation functions, and general implementation considerations.

## Loss Functions & Reconstruction Quality
This section explains the objective function used to train VAEs.

*   **Evidence Lower Bound (ELBO)**: The tractable lower bound on log-likelihood that is optimized. Formula: $\text{ELBO} = \mathbb{E}_{q(z|x)}[\log p(x|z)] - D_{KL}(q(z|x) \| p(z))$.
*   **Reconstruction Loss**: Measures how well the model reconstructs data. Uses Binary Cross-Entropy for binary data and Mean-Squared Error for continuous data.
*   **KL Divergence Term**: Acts as a regularizer measuring how much the approximate posterior $q(z|x)$ differs from the prior $p(z)$. It encourages a smooth latent space.
*   **$\beta$-VAE**: Introduces a hyperparameter $\beta$ to balance reconstruction and disentanglement (independent factors in latent space).
*   **Pitfalls & Solutions**: Discusses *Posterior Collapse* (where the decoder ignores latent codes) and solutions like *KL Warm-up schedules*.

## Conditional VAEs (CVAEs)
This section introduces extensions to control the generation process.

*   **Motivation**: Controlled generation by feeding auxiliary information $c$ (labels, attributes).
*   **Formulation**: Modifies the model to use conditional prior $p(z|c)$, conditional likelihood $p(x|z,c)$, and conditional posterior $q(z|x,c)$.
*   **Conditional ELBO**: $\log p(x|c) \geq \mathbb{E}_{q(z|x,c)}[\log p(x|z,c)] - D_{KL}(q(z|x,c) \| p(z|c))$.
*   **Implementation**: Concatenating $c$ with inputs or latent codes in Encoder and Decoder.

## Hands-On Sessions
The repository includes two Jupyter notebooks for hands-on practice, implementing the concepts discussed in the slides.

### 1. VAE Hands-On (`VAE_hands_on.ipynb`)
This notebook guides students through the implementation of a Variational Autoencoder on the MNIST dataset.
*   **Implementations**:
    *   Comparison with a standard CNN-based Autoencoder.
    *   Custom loss functions for Reconstruction (BCE) and KL Divergence.
    *   KL Annealing schedule.
    *   CNN-based VAE model.
    *   Generative sampling from the prior and latent space interpolation.
*   **Student Tasks (TODOs)**:
    *   Explore $\beta$-VAE by varying the beta hyperparameter.
    *   Implement Latent Traversals to visualize what different dimensions capture.
    *   Extend the VAE implementation to the CIFAR-100 dataset.

### 2. CVAE Hands-On (`CVAE_hands_on.ipynb`)
This notebook extends the VAE framework to a Conditional VAE on the MNIST dataset.
*   **Implementations**:
    *   Conditioning the VAE on digit labels (0-9).
    *   Controlled generation of specific digits.
*   **Student Tasks (TODOs)**:
    *   Latent Traversals for CVAE.
    *   **Generate Roll Number**: A specific task instructing students to generate a sequence of digits corresponding to their roll number using the condition variable.
    *   CVAE on CIFAR-100.

## Summary: Recall the Journey
*   **The Baseline**: Standard Autoencoders map inputs to deterministic points. Good for compression, bad for generation.
*   **The Upgrade**: VAEs map inputs to probability distributions ($\mu, \sigma$) for a continuous latent space.
*   **The Hurdle**: How to backpropagate through a random sampling node?
*   **The Fix**: The Reparameterization Trick ($\mu + \sigma \cdot \epsilon$) isolates the randomness!
*   **The Goal**: ELBO balances reconstruction quality with latent space smoothness (KL divergence).
*   **The Extension**: CVAEs allow controlled generation by feeding a condition $c$.
