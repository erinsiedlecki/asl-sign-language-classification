# ASL Gesture Classification

Deep learning project for American Sign Language (ASL) gesture classification using a custom CNN, EfficientNet-B0, and ResNet18 with a focus on transfer learning, generalization, and model evaluation.

---

## Overview

This project explores deep learning approaches for American Sign Language (ASL) gesture classification using image-based hand sign data. We compare a custom CNN trained from scratch against transfer learning approaches using EfficientNet-B0 and ResNet18. A major focus of the project was evaluating model generalization and preventing subject-level data leakage through volunteer-based train/test splitting.

---

## Motivation

American Sign Language (ASL) is the primary mode of communication for hundreds of thousands of deaf and hard-of-hearing individuals in the United States. Despite its widespread use, most hearing individuals do not understand ASL, creating communication barriers in healthcare, education, workplaces, and public services. This project explores how deep learning can be used to support automated ASL recognition from static hand gesture images.

---

## Dataset

We used the ASL-HG dataset, which contains 36,000 RGB images across 36 classes representing letters A–Z and digits 0–9. Images were collected from 10 volunteers under varied lighting conditions, backgrounds, viewing angles, and skin tones.

Initially, a standard random train/test split produced unrealistically high performance because images from the same volunteers appeared across all splits. To address this, we used a volunteer-based split:
- Train: Volunteers 0–6
- Validation: Volunteer 7
- Test: Volunteers 8–9

This approach forced the models to generalize to entirely unseen individuals and provided a more realistic evaluation of real-world performance.

---

## Models

### Model 1 — Custom CNN
- CNN trained from scratch
- Four convolutional blocks
- Batch normalization, dropout, max pooling
- Global average pooling

### Model 2 — EfficientNet-B0
- Transfer learning using pretrained ImageNet weights
- Compound scaling
- Full fine-tuning

### Model 3 — ResNet18
- Transfer learning using pretrained ImageNet weights
- Partial fine-tuning with frozen early layers
- Residual (skip) connections

---

## Methods

- Transfer learning
- Data augmentation
- Volunteer-based train/test splitting
- Cross-entropy loss evaluation
- Confusion matrix analysis
- Model comparison across architectures

Data augmentation included:
- random rotation
- random translation
- color jitter
- Gaussian blur
- random grayscale
- random perspective transformation
- random horizontal flipping

---

## Results

| Model | Test Accuracy |
|---|---|
| Custom CNN | 77.93% |
| EfficientNet-B0 | 84.36% |
| ResNet18 | 81.19% |

Key findings:
- Transfer learning improved overall classification accuracy
- All three models exhibited signs of overfitting
- Volunteer-based splitting produced more realistic performance estimates
- Most misclassifications occurred among visually similar gestures

The most important finding from this project was that evaluation methodology matters as much as model architecture. Early random splits produced near-perfect accuracy due to subject-level data leakage, while volunteer-based splits provided a more honest measure of generalization performance.

---

## Technologies

- Python
- PyTorch
- pandas
- NumPy
- matplotlib
- scikit-learn
- Google Colab

---

## Project Materials

- [Project Notebook](Notebooks/asl_gesture_classification.ipynb)
- [Final Report](Reports/Asl_Final_Report.pdf)
- [Final Presentation](Presentations/Asl_Final_Presentation.pdf)

---

## Team Project

Completed as part of the UVA M.S. in Data Science program in collaboration with teammates Natalie Seah and Bela Barton. My contributions included model experimentation, evaluation, visualization, and analysis.
