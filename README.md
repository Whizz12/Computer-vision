# 🚀 GAN & SRGAN for Image Generation and Super-Resolution

This repository contains PyTorch implementations of:
- **Vanilla GAN**: For generating synthetic images from random noise.
- **SRGAN (Super-Resolution GAN)**: For enhancing low-resolution images to high-resolution using a deep adversarial network.

---

## 📌 Table of Contents

- [Overview](#overview)
- [Model Architectures](#model-architectures)
- [Setup & Installation](#setup--installation)
- [Training](#training)
- [Testing](#testing)
- [Results](#results)
- [References](#references)
- [Contact](#contact)

---

## 🧠 Overview

### ✨ GAN (Generative Adversarial Network)
A framework with two competing networks:
- **Generator** creates realistic fake images from noise.
- **Discriminator** tries to distinguish real from fake images.

### 🔍 SRGAN (Super-Resolution GAN)
A GAN architecture that upsamples low-resolution images using:
- A deep **Residual Generator** with skip connections.
- A **PatchGAN-style Discriminator**.
- Perceptual loss based on a pretrained VGG network for better visual quality.

---

## 🏗️ Model Architectures

### GAN
- **Generator**: Fully connected layers (MLP) with ReLU and Tanh
- **Discriminator**: Fully connected layers with LeakyReLU and Sigmoid

### SRGAN
- **Generator**:
  - 9×9 Conv2D → PReLU
  - Residual Blocks: Conv2D → BN → PReLU → Conv2D → BN + Skip connection
  - Post-residual Conv + PixelShuffle (upsample)
  - Final 9×9 Conv2D to output RGB
- **Discriminator**:
  - 4 Convolutional layers with increasing filters (64 → 512)
  - LeakyReLU activations
  - Final Conv → Flatten → Fully connected → Sigmoid

---

## ⚙️ Setup & Installation

```bash
git clone https://github.com/yourusername/GAN-SRGAN.git
cd GAN-SRGAN
pip install -r requirements.txt

