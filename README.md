# 🎨 Multimodal GAN for Text + Image Based Generation

This repository contains a **Multimodal Generative Adversarial Network (GAN)** that combines **text embeddings** and **image features** to generate new synthetic images.  
The project explores how GANs can leverage multiple data modalities to produce richer, more expressive outputs.

---

## 📌 Project Overview

Traditional GANs use **only noise (z)** as input.  
This project extends the architecture by introducing:

- **Text embeddings** (from a pretrained NLP model)
- **Image features** (from a CNN encoder)
- **Concatenated multimodal latent vector** fed into the generator

This gives the model better understanding of both **what to generate (text)** and **how it should look (image features)**.

---

## 🧠 Key Concepts

### 1️⃣ **Multimodal Learning**  
Incorporates information from different sources:
- Visual (image)
- Textual (prompt embedding)

### 2️⃣ **GAN Architecture**
The project uses:

- **Generator (G):**  
  Takes concatenated `[z + text_emb + image_features]`  
  and generates an image.

- **Discriminator (D):**  
  Judging real vs. fake images  
  using both the generated image and text conditioning.

---

## 🔧 Main Components in the Notebook

### ✔️ Data Preprocessing
- Load images  
- Load corresponding text/prompt  
- Use pretrained model (like BERT/CLIP) for text embeddings  
- Normalize images  
- Batch the training data  

### ✔️ Taking Embeddings
- Convert each text caption into a vector  
- Extract CNN feature maps from input images  
- Concatenate all embeddings for multimodal input  

### ✔️ Multimodal Generator
Includes:
- Dense layers  
- UpSampling + ConvTranspose layers  
- Activation functions (ReLU/LeakyReLU)  
- Output: Generated image  

### ✔️ Discriminator
Includes:
- Conv layers  
- Downsampling  
- Conditional text/image fusion  
- Output: Real/Fake probability  

### ✔️ Training Loop
- Train D to distinguish real from fake  
- Train G to fool D  
- Compute losses  
- Save generated sample images  

---

## 📁 Repository Structure
📂 Multimodal-GAN
│
├── Multimodal_GAN.ipynb # Main notebook
├── README.md # Documentation
├── requirements.txt # Install all needed libraries
└── samples/ # Generated images (optional)

## WorkFlow
Text Caption  → Text Encoder →  Text Embedding
Image Input   → CNN Encoder  →  Image Features
Noise (z)     → Random Vector

[z + text_emb + img_features] → Generator → Fake Image
Real or Fake? → Discriminator

