# American Sign Lang CNN 🤟

> A Convolutional Neural Network (CNN) trained to classify American Sign Language (ASL) hand gestures from the Sign Language MNIST dataset.

---

## Overview

**American Sign Lang CNN** uses a simple but effective CNN architecture to recognize 24 ASL letters (A–Y, excluding J and Z which require motion) from 28×28 grayscale images. The project includes full training, evaluation, and a diagnosis of whether the model is overfitting, underfitting, or performing well.

---

## Model Architecture

```
Input (1 × 28 × 28)
   ↓  Conv2d(1 → 32, 3×3) + ReLU + MaxPool  →  32 × 14 × 14
   ↓  Conv2d(32 → 64, 3×3) + ReLU + MaxPool  →  64 × 7 × 7
   ↓  Flatten  →  3136
   ↓  Linear(3136 → 256) + ReLU + Dropout(0.4)
   ↓  Linear(256 → 24)
Output: 24 classes
```

---

## Dataset

- **Name:** Sign Language MNIST
- **Source:** [Kaggle — datamunge/sign-language-mnist](https://www.kaggle.com/datasets/datamunge/sign-language-mnist)
- **Files:** `train.csv`, `test.csv`
- **Format:** Each row = 1 label + 784 pixel values (28×28 flattened)
- **Classes:** 24 ASL letters (J and Z excluded — motion-based signs)

---

## Project Structure

```
American Sign Lang CNN/
├── ASL_CNN.ipynb       ← Main training notebook (Google Colab)
├── README.md           ← Project overview (this file)
├── description.md      ← Detailed project description
└── requirements.txt    ← Python dependencies
```

---

## How to Run

1. Upload `ASL_CNN.ipynb` to [Google Colab](https://colab.research.google.com)
2. Enable GPU: **Runtime → Change runtime type → T4 GPU**
3. Place your dataset zip in Google Drive and update `ZIP_PATH` in Cell 1:
   ```python
   ZIP_PATH = '/content/drive/MyDrive/your-zip-name.zip'
   ```
4. Run all cells top to bottom

---

## Results

The notebook evaluates the model and auto-diagnoses:

| Scenario | Indicator |
|---|---|
| ✅ Good Fit | Train ≈ Val accuracy, both ≥ 85% |
| ⚠️ Overfitting | Train acc >> Val acc (gap > ~15%) |
| ❌ Underfitting | Both accuracies below 70% |

Outputs include learning curves, a confusion matrix, and a full classification report.

---

## Tech Stack

- Python 3.10+
- PyTorch
- NumPy & Pandas
- Scikit-learn
- Matplotlib & Seaborn
- Google Colab (GPU runtime)

---

## Author

Built as part of the GoMyCode Deep Learning curriculum.

