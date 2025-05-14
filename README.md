# Deep Feature Graph-Cut Segmentation

### Note:
This is my final project for a computational vision course (CS484) that I took at the University of Waterloo Due to course policies, I am not permitted to release the code publicly. Only the project report is available in this repo. In case you are interested in learning more about the code and implementation details, kindly reach out to me at yhbarve@uwaterloo.ca

---

An **interactive image segmentation tool** that replaces raw RGB values with deep convolutional features (from a pretrained ResNet-50) in a graph-cut framework. Users paint foreground/background seeds in a Jupyter widget, and the tool computes an optimal s–t min-cut over the network of pixels.

---

## Project Overview

This is a final project for CS484 - Computational Vision. The key goals of the project are:

1. **Extracting per-pixel features** from a pretrained ResNet-50 (stripping off its classification head and upsampling its final convolutional feature map to the original image size).  
2. **Constructing a graph** whose nodes are image pixels, with:
   - **t-links** (pixel→foreground/background terminals) derived from squared-distance to user-painted seed centroids in feature space (hard constraints enforced with a large finite cost).  
   - **n-links** (pairwise pixel connections) weighted by a contrast function in deep-feature space:  
     \[
       w_{pq} = \lambda \, \exp\!\bigl(-\|f_p - f_q\|^2 / \sigma^2 \bigr).
     \]  
3. **Solving the min-cut** via the PyMaxflow library to produce a binary segmentation mask.  
4. Providing an **interactive Jupyter widget** for users to add or correct foreground/background strokes and see real-time updates.

A simpler **RGB-baseline** replaces the deep features with normalized RGB values for comparison.

---

## Motivation

- **Semantic awareness**: RGB values capture only color; deep features encode high-level shape, texture, and object information learned from millions of images.  
- **Interactivity**: Graph-cut with user seeds ensures precise control over fine details.

---

## Requirements

- Python 3.8+  
- PyTorch & TorchVision  
- NumPy  
- Matplotlib  
- scikit-image  
- PyMaxflow  
- A Jupyter environment (JupyterLab or notebook)

---
