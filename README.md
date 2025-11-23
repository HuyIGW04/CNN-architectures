# CIFAR-10 Trainable CNN System

## Objective
This project implements a trainable Convolutional Neural Network (CNN) for color image classification on the CIFAR-10 dataset. Utilizing the VGG-16 architecture as a baseline, I conducted a comparative analysis of various optimization techniques to evaluate their impact on model performance


## Model Architecture
The model consists of **5 main blocks**:
- **4 Convolutional Blocks**
- **1 Dense Block (Classifier)**

Each convolutional block includes:
- **2 Convolutional Layers**
- **1 MaxPooling Layer (2×2)**

The classifier block includes:
- **3 Fully-Connected (Dense) Layers**


## Initialization  
- Weights are initialized using **He Initialization**[^1], a widely used and effective initialization technique in TensorFlow.
- Primary activation: **ReLU**
- **Adam** optimizer[^2]  
- Learning rate: `1e-3`
- Default normalization scales input pixel values to the range **[0, 1]**


## Training Enhancements

### Z-Score Normalization  
Replaces the initial `[0, 1]` scaling with **Z-Score normalization** in the first normalization layer.

### Batch Normalization  
Improves training stability by reducing internal covariate shift.

### Advanced Activation – SwiGLU  
- Integrates **SwiGLU** (2020)[^3] as an enhanced activation mechanism to improve expressiveness.

### Skip Connections  
Adds skip connections to mitigate vanishing gradients and improve gradient flow.

## Experiments

The results are recorded in the table below:

| Model | Train Accuracy | Test Accuracy | Status |
| :--- | :---: | :---: | :---: |
| **1. VGG-16 (Standard)** | 98.03% | 70.20% | |
| **2. VGG-16 + Z-Score Initialization** | 98.97% | 76.57% | ✅ |
| **3. VGG-16 + Batch Normalization** | **99.60%** | **86.25%** | ✅ |
| **4. VGG-16 + SwiGLU Activation** | 99.32% | 75.97% | ✅ |
| **5. VGG-16 + Skip Connection** | 99.78% | 76.63% | ✅ |

**Conclusion:** The results demonstrate that **Batch Normalization** yields the superior performance on the CIFAR-10 dataset.


[^1]: He Initialization — widely used weight initialization method designed to keep variance consistent across layers.  
[^2]: Adam Optimizer — combines momentum and adaptive learning rate techniques for efficient training.  
[^3]: *SwiGLU: A New Activation Function* — Paper reference: https://arxiv.org/pdf/1702.03118
