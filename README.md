# Dorsal-Vein-Authentication-System
A Secure Biometric Identification System using CNN-SVM Hybrid Architecture.
A biometric authentication system that identifies individuals using the unique vein patterns on the back (dorsal side) of their hand. The system combines classical image processing for vein extraction with a CNN + SVM hybrid classification pipeline.
Traditional authentication methods like passwords and PINs are increasingly vulnerable to theft and misuse. This project leverages dorsal hand vein patterns as a biometric identifier — a non-intrusive, spoof-resistant, and highly unique trait captured using near-infrared (NIR) imaging.
The system works in two stages:

Vein Pattern Extraction — A classical image processing pipeline extracts the vein map from a raw hand image.
Classification — A CNN acts as a feature extractor, and an SVM performs the final identity classification.
Features

1. Mexican Hat kernel-based hair removal from hand images
2. Multi-directional curvature computation using Gaussian derivatives (0°, 90°, 45°, −45°)
3. Probabilistic vein scoring and center connection
4. Adaptive median-based binarization
5. CNN with dropout regularization for feature learning
6. SVM classifier with probability estimation for identity verification
7. Streamlit-based web UI for real-time authentication
8. Plotly confusion matrix and full classification report

Raw Hand Image (NIR)
        │
        ▼
  Remove Hair (Mexican Hat Kernel Convolution)
        │
        ▼
  Normalize Data [0, 255]
        │
        ▼
  Compute Curvature κ (Gaussian 2nd Derivative, 4 Directions)
        │
        ▼
  Compute Vein Score (Probabilistic Ridge Scoring)
        │
        ▼
  Connect Centres (Link Vein Segments Horizontally, Vertically, Diagonally)
        │
        ▼
  Binarize (Median Threshold → Binary Vein Mask)
        │
        ▼
  Vein Pattern Image
        │
        ▼
  CNN Feature Extractor (3 Conv Layers + Dropout)
        │
        ▼
  SVM Classifier (Linear Kernel + Probability Estimation)
        │
        ▼
  Identity / Access Decision

Optimizer: Adam
Loss: Sparse Categorical Crossentropy
Epochs: 10
Batch Size: 16
Input Size: 224 × 224 × 3

SVM

Kernel: Linear
Probability estimation: Enabled (probability=True)
Input: CNN softmax output vector (85-dimensional)
Authentication threshold: Confidence > 5% → Access Granted

Result 

CNN (standalone) is 86% &
CNN + SVM (hybrid) is 92%

