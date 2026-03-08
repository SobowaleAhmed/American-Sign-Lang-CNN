# Project Description — American Sign Lang CNN

## What is American Sign Lang CNN?

**American Sign Lang CNN** is a deep learning project that trains a Convolutional Neural Network (CNN) to recognize American Sign Language (ASL) hand gestures. Given a 28×28 grayscale image of a hand sign, the model predicts which of 24 ASL letters is being shown.

The project is built using **PyTorch** and runs on **Google Colab** with GPU acceleration.

---

## Problem Statement

American Sign Language is the primary language of many Deaf and hard-of-hearing individuals. Automating the recognition of ASL gestures using computer vision can serve as a foundation for real-time sign language translation tools.

This project tackles a simplified version of that problem: classifying **static hand gesture images** into one of 24 ASL letter categories.

---

## Dataset

The **Sign Language MNIST** dataset is a direct drop-in replacement for the classic MNIST dataset, adapted for ASL recognition.

- Each image is **28×28 pixels**, grayscale
- Each pixel value is in the range **0–255**
- Labels represent letters **A–Y** (J and Z are excluded as they require motion)
- Training set: ~27,455 samples | Test set: ~7,172 samples

---

## Approach

### Preprocessing
- Pixel values normalized to [0, 1]
- Data reshaped from flat CSVs into (N, 1, 28, 28) tensors
- 80/20 train/validation split applied to the training set

### Model
A simple two-block CNN:
- **Block 1:** Conv2d → ReLU → MaxPool
- **Block 2:** Conv2d → ReLU → MaxPool
- **Classifier:** Flatten → Linear → ReLU → Dropout(0.4) → Linear

Dropout is used to reduce overfitting. The model has ~820,000 trainable parameters.

### Training
- **Optimizer:** Adam (lr = 1e-3)
- **Loss:** CrossEntropyLoss
- **Epochs:** 20
- **Batch Size:** 64
- **Hardware:** Google Colab T4 GPU

---

## Evaluation

The model is evaluated on:
- **Training & Validation curves** — to visually diagnose overfitting or underfitting
- **Test set accuracy** — final held-out performance
- **Confusion matrix** — per-letter breakdown of predictions
- **Classification report** — precision, recall, F1-score per class

### Diagnosis Logic

| Condition | Verdict |
|---|---|
| Train acc < 70% | Underfitting |
| Train acc − Val acc > 15% | Overfitting |
| Val acc ≥ 85% | Good Fit |
| Otherwise | Moderate Fit |

---

## Key Takeaways

- CNNs are well-suited for image classification tasks even at small scales (28×28)
- GPU acceleration significantly speeds up training compared to CPU
- Dropout and validation monitoring are essential tools for catching overfitting early
- The Sign Language MNIST dataset is clean and well-balanced, making it ideal for learning CNN fundamentals

---

## Built With

This project was completed as a checkpoint assignment in the **GoMyCode Deep Learning curriculum** and is part of the **American Sign Lang CNN** repository.
