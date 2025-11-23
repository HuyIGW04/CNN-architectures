# CIFAR-10 Trainable CNN System

## Objective
Set up a **trainable convolutional neural network (CNN)** for color image classification on the **CIFAR-10** dataset.

## Model Architecture

### Overall Structure
The model consists of **5 main blocks**:
- **4 Convolutional Blocks**
- **1 Dense Block (Classifier)**

### Convolutional Blocks (×4)
Each convolutional block includes:
- **2 Convolutional Layers**
- **1 MaxPooling Layer (2×2)**

### Dense Block (Classifier)
The classifier block includes:
- **3 Fully-Connected (Dense) Layers**


## Initialization  
Weights are initialized using **He Initialization**[^1], a widely used and effective initialization technique in TensorFlow.


## Activation Function  
- Primary activation: **ReLU**


## Optimizer  
- **Adam** optimizer[^2]  
- Learning rate: `1e-3`


## Data Normalization  
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


## Notes  
This README summarizes the core architecture and training improvements used to build a trainable CNN model for CIFAR-10.


[^1]: He Initialization — widely used weight initialization method designed to keep variance consistent across layers.  
[^2]: Adam Optimizer — combines momentum and adaptive learning rate techniques for efficient training.  
[^3]: *SwiGLU: A New Activation Function* — Paper reference: https://arxiv.org/pdf/1702.03118
