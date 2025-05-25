# Soil Image Classification Challenge – Annam.ai @ IIT Ropar

This repository contains solutions to two parts of the **Soil Image Classification Challenge** organized by [Annam.ai](https://annam.ai/) at IIT Ropar.

- **Part 1:** Soil Image Classification Challenge  
- **Part 2:** Soil Image Classification Challenge

---

## 📁 Contents

- `soil-classification-annam-ai.ipynb`: notebook (Part 1)  
- `soil-classification-part-2-annam-ai.ipynb`: notebook (Part 2)  
- `submission.csv`: Final predictions in required format (can be renamed based on the part)

---

## 🧠 Approach

### 🔹 Common Steps

1. **Import Libraries**  
   Libraries used: `PyTorch`, `torchvision`, `tqdm`, `sklearn`, `pandas`, `matplotlib`.

2. **Dataset Loading and Preprocessing**  
   - Custom PyTorch `Dataset` class using image paths and labels from CSV.
   - Augmentations: Random flips, rotations, resizing, normalization (ImageNet mean/std).

3. **Model Architecture**  
   - Base: `ResNet18` pretrained on ImageNet.
   - Final `fc` layer replaced:
     - **Part 1 (Binary):** `nn.Linear(..., 2)`
     - **Part 2 (Multiclass):** `nn.Linear(..., 4)`

4. **Training Setup**
   - Loss Function: `CrossEntropyLoss`
   - Optimizer: `Adam`
   - Scheduler: `StepLR`
   - Tracked metrics: **Weighted F1-score** (via `sklearn.metrics.f1_score`)
   - Early stopping based on validation F1

---

## 📊 Results

| Task            | Model    | Metric        | F1 Score   |
|-----------------|----------|---------------|------------|
| Part 1 (Binary) | ResNet18 | Weighted F1   | ~1.000     |
| Part 2 (Multi)  | ResNet18 | Weighted F1   | ~0.541     |

---

## 🏁 How to Run

1. **Clone the repository**
```bash
git clone https://github.com/CAT-ROM/soil-classification-annam-ai.git
cd soil-classification-annam-ai
