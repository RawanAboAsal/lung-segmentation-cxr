# Modular Deep Learning Framework for Lung Segmentation

A Comparative Study of CNN Encoders and UNet Variants for Lung Segmentation in Chest X-rays

## Overview

This project presents a modular deep learning framework for automated lung segmentation using chest X-ray (CXR) images. It systematically compares various CNN-based encoder architectures within a UNet-style segmentation pipeline. The model incorporates Transformer Attention Modules, Spatial Enhancement Modules, and Multi-Scale Fusion to improve segmentation precision and model robustness.

The framework is designed to be backbone-independent, supporting various encoders such as EfficientNetB0, MobileNetV2, InceptionResNetV2, DenseNet121, VGG16, and ResNet34-UNet.

## Key Features

- Modular and configurable UNet-style architecture
- Plug-and-play support for multiple CNN backbones
- Transformer Attention Module (TAM) for global context modeling
- Spatial Enhancement Module (SEM) for refined local features
- Multi-scale feature fusion for fine-grained segmentation
- Comprehensive evaluation using accuracy, loss, and training time

## Dataset

- Dataset: Shenzhen Chest X-ray Dataset
- Samples: 704 grayscale images (336 TB cases and 368 normal cases)
- Preprocessing:
  - Images resized to 256×256
  - Normalized to [0, 1] range
- Ground Truth: Pixel-wise binary lung masks

## Architecture

Input Image
     ↓
CNN Encoder (EfficientNet, MobileNetV2, etc.)
     ↓
Spatial Enhancement Module (per skip connection)
     ↓
Transformer Attention Module (at bottleneck)
     ↓
Decoder + Multi-Scale Fusion
     ↓
Final Segmentation Mask
## Experimental Results

| Model              | Train Accuracy | Train Loss | Training Time | Test Accuracy | Test Loss |
|-------------------|----------------|------------|----------------|---------------|-----------|
| EfficientNetB0    | 98.39%         | 0.0401     | 1.00 min       | 96.69%        | —         |
| MobileNetV2       | 98.41%         | 0.0386     | 1.32 min       | 97.71%        | 0.0679    |
| InceptionResNetV2 | 98.74%         | 0.0305     | 7.02 min       | 97.75%        | 0.0993    |
| DenseNet121       | 98.60%         | 0.0339     | 4.52 min       | 97.90%        | 0.0617    |
| VGG16             | 98.92%         | 0.0257     | 11.5 min       | 98.04%        | 0.0634    |
| ResNet34-UNet     | 98.81%         | 0.0286     | 2.22 min       | 98.03%        | 0.0632    |
