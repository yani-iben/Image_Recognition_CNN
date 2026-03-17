# UVA Landmark Recognition: Architectural Evolution

This project focuses on building a deep learning image recognition system to classify **18 different historical buildings and landmarks** at the University of Virginia (UVA) Grounds. The project demonstrates the progression from a simple baseline CNN to a high-performing architecture utilizing residual connections and advanced optimization techniques.

## Project Overview
UVA's Grounds are famous for their Jeffersonian architecture. This repository contains a PyTorch implementation of three distinct Convolutional Neural Network (CNN) architectures designed to recognize these structures.

* **Dataset:** ~13,000 images across 18 classes (subset: 379MB).
* **Target:** Exceed 94% accuracy (Bonus threshold).
* **Framework:** PyTorch & Torchvision.

---

## Model Architectures

### 1. MyCNN1: The Baseline
A simple sequential architecture to establish a performance floor.
* **Design:** 4 Convolutional modules (Conv -> BatchNorm -> ReLU -> MaxPool).
* **Pooling:** Global Average Pooling to ensure compatibility with various input sizes.
* **Result:** Established initial learning but showed limitations in feature depth.

### 2. MyCNN2: Stacking & Depth
An evolution focused on increasing the model's capacity to learn complex textures.
* **Design:** Stacked two convolutional layers per block before pooling.
* **Refinements:** Increased channel depth (up to 512) and used a lower learning rate ($0.0005$) for stability.
* **Regularization:** Strategic Dropout ($0.4$) to prevent memorization.

### 3. MyCNN3: Residual Learning (Best Model)
A sophisticated architecture implementing **Skip Connections** (Residual Blocks) to allow for deeper feature extraction without gradient degradation.
* **Design:** Custom `ResidualBlock` class combining a convolutional path with a shortcut path.
* **Optimization:** Switched to `AdamW` and implemented a `StepLR` scheduler.
* **Early Stopping:** Monitoring validation accuracy to prevent overfitting and save the best weights.
* **Accuracy:** Achieved a peak validation accuracy of **88.42%**.

---

## Performance Comparison

| Model | Architecture | Key Features | Val Accuracy |
| :--- | :--- | :--- | :--- |
| **MyCNN1** | Simple CNN | Baseline | ~63% |
| **MyCNN2** | Deep CNN | Stacked Layers | ~84% |
| **MyCNN3** | **ResNet-style**| **Residual Blocks & AdamW** | **88.42%** |

---

## Getting Started

### Prerequisites
* Python 3.8+
* PyTorch
* Torchvision
* Matplotlib / Seaborn
* Scikit-learn

### Installation & Usage
1. Clone the repository:
   ```bash
   git clone [https://github.com/yourusername/uva-landmark-recognition.git](https://github.com/yourusername/uva-landmark-recognition.git)
