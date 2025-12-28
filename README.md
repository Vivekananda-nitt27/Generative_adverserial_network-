# 🎨 Anime Image Generation using Generative Adversarial Networks (GAN)

## 📌 Overview
This project implements a **Generative Adversarial Network (GAN)** to generate realistic **anime-style images** from random noise. The system consists of two neural networks — a **Generator** and a **Discriminator** — trained in an adversarial manner on an anime image dataset.

The Generator learns to synthesize anime images that resemble real samples, while the Discriminator learns to distinguish between real and fake images. Over time, both networks improve through competition.

---

## 🧠 What is a GAN?
A Generative Adversarial Network consists of two models:

- **Generator (G):** Generates fake images from random noise
- **Discriminator (D):** Classifies images as real or fake

They play a **minimax game** defined as:

\[
\min_G \max_D \mathbb{E}_{x \sim p_{data}}[\log D(x)] + \mathbb{E}_{z \sim p_z}[\log(1 - D(G(z)))]
\]

The goal is for the generator to fool the discriminator by producing highly realistic images.

---

## 🧩 Model Architecture

### 🔹 Generator Network
- Input: Random noise vector (latent space)
- Uses convolutional and upsampling layers
- Gradually converts noise into anime images
- Final activation: `Tanh / Sigmoid` (based on normalization)

**Purpose:** Learn the data distribution of anime faces

---

### 🔹 Discriminator Network
- Input: Image (real or generated)
- Uses convolutional layers with downsampling
- Outputs probability of image being real
- Final activation: `Sigmoid`

**Purpose:** Act as a binary classifier

---

## ⚙️ Training Configuration

| Parameter | Value |
|---------|-------|
| Dataset | Anime Image Dataset |
| Epochs | 25 |
| Batch Size | 25 |
| Optimizer | Adam |
| Loss Function | Binary Cross-Entropy |
| Framework | PyTorch / TensorFlow |
| Hardware | CPU / GPU |

---

## 🔁 Training Workflow

1. Load anime image dataset
2. Normalize images
3. Sample random noise
4. Generate fake images using Generator
5. Train Discriminator on:
   - Real images (label = 1)
   - Fake images (label = 0)
6. Train Generator to fool Discriminator
7. Save generated images after each epoch
8. Repeat for all epochs

---


### 📌 Metric Interpretation
- **Generator Loss (6.7480):** Indicates the difficulty in fooling a strong discriminator.
- **Discriminator Loss (0.0151):** Very low value shows high classification accuracy.
- **Real Score (0.9963):** Discriminator correctly identifies real images.
- **Fake Score (0.0109):** Generated images are highly convincing.

---

## 🧮 Final Performance Matrix

| Metric | Value |
|------|------|
| Generator Loss | 6.7480 |
| Discriminator Loss | 0.0151 |
| Real Image Confidence | 0.9963 |
| Fake Image Confidence | 0.0109 |
| Epochs Completed | 25 |
| Batch Size | 25 |

---

## 🖼️ Generated Output

Generated images are saved automatically after training.



