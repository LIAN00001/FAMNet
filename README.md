# FAMNet

Official implementation of **FAMNet: Frequency-Adaptive Magnitude Deformable Network for Camouflaged Object Detection**.

## Introduction

Camouflaged object detection aims to segment objects that are highly similar to their surrounding background. This task is challenging because camouflaged regions often contain weak object boundaries, heterogeneous local textures, and ambiguous foreground-background transitions.

FAMNet addresses this problem by introducing a frequency-adaptive magnitude deformable mechanism for adaptive feature sampling. The method adjusts deformable sampling magnitudes according to local frequency responses, enabling more constrained sampling in complex high-frequency regions and broader contextual sampling in smoother regions. A structure-aware weighted supervision strategy is further used to emphasize locally ambiguous regions during training.

## Method Overview

The proposed framework contains two main components:

1. **Frequency-Adaptive Magnitude Deformable Convolution**

   The deformable offset magnitude is adaptively modulated according to local frequency information:

   $$
   \Delta'(p) = \lambda \cdot s(p) \cdot \tanh(\Delta_{\mathrm{raw}}(p))
   $$

   where $\Delta_{\mathrm{raw}}(p)$ denotes the raw deformable offset, $s(p)$ is the frequency-guided magnitude scaling factor, and $\lambda$ controls the global deformation scope.

2. **Structure-Aware Weighted Supervision**

   A spatial weight map is generated from local structural discrepancy between prediction and ground truth, assigning larger weights to locally ambiguous regions.

   The overall training objective is:

   $$
   \mathcal{L}_{total}
   =
   \mathcal{L}_{wbce}
   +
   \mathcal{L}_{wdice}
   +
   \mathcal{L}_{ual}
   $$

## Repository Structure

```text
FAMNet/
├── models/                 # Model definitions
├── datasets/               # Dataset loading and preprocessing
├── utils/                  # Utility functions
├── train.py                # Training script
├── test.py                 # Testing script
├── eval.py                 # Evaluation script
├── requirements.txt        # Python dependencies
└── README.md
