# FAMNet

Official repository for **FAMNet: Frequency-Adaptive Magnitude Deformable Network for Camouflaged Object Detection**.

## Method Overview

FAMNet is designed for camouflaged object detection, where foreground objects are visually similar to their surrounding background and often exhibit weak boundaries, complex textures, and ambiguous foreground-background transitions.

The core idea of FAMNet is to adapt deformable sampling according to local frequency information. In complex high-frequency regions, the model suppresses excessive deformation to preserve fine structures and avoid unstable sampling. In smoother low-frequency regions, the model allows broader contextual sampling to improve object-level consistency.

The frequency-adaptive magnitude deformation can be summarized as:

$$
\Delta'(p) = \lambda \cdot s(p) \cdot \tanh(\Delta_{\mathrm{raw}}(p))
$$

where $\Delta_{\mathrm{raw}}(p)$ denotes the raw deformable offset, $s(p)$ is the frequency-guided magnitude scaling factor, and $\lambda$ controls the global deformation scope.

FAMNet is further trained with a structure-aware weighted supervision objective that emphasizes locally ambiguous regions between predictions and ground-truth masks.

The total training objective is:

$$
\mathcal{L}_{total}
=
\mathcal{L}_{wbce}
+
\mathcal{L}_{wdice}
+
\mathcal{L}_{ual}
$$

## Prediction Maps

The prediction maps of FAMNet are available at:

[Google Drive: FAMNet Prediction Maps](https://drive.google.com/drive/folders/1p9lw4doD6SLu-ToXq2Bx172oeYgc_n2b?usp=sharing)
