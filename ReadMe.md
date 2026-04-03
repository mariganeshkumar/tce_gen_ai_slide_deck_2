# TCE Gen AI Slide Deck - Variational Autoencoders

This repository contains the LaTeX source code for the "Variational Autoencoders: Theory and Applications" slide deck.

## Compilation Instructions

The slide deck is compiled using **[Tectonic](https://tectonic-typesetting.github.io/)**, a modern and lightweight TeX engine that automatically downloads required packages on-demand.

### Prerequisites

You need `tectonic` installed on your system. On macOS (with Homebrew), you can install it using:

```bash
brew install tectonic
```

### Compiling the Slides

To generate the PDF, run the following command in the root of the repository:

```bash
tectonic main.tex
```

If `tectonic` is not in your `PATH` (e.g., on macOS with Apple Silicon installed via Homebrew), you may need to specify the full path:

```bash
/opt/homebrew/bin/tectonic main.tex
```

This will produce a `main.pdf` file in the same directory.

## Features

- **Beamer & Metropolis Theme**: Professional and clean presentation style.
- **TikZ Diagrams**: Custom figures for autoencoder architectures, probabilistic modeling, and VAE frameworks.
- **Mathematical Notation**: Detailed equations for ELBO, Kullback-Leibler divergence, and Gaussian parameterization.

## Project Structure

- `main.tex`: The primary LaTeX source file.

---
*Note: This project was originally imported from Overleaf and has been optimized for local compilation using Tectonic.*
