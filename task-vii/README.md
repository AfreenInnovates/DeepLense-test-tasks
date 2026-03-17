# DeepLense Task VII - Physics-Informed Lensing Classification

This project implements **Physics-Informed Neural Networks (PINNs)** to classify gravitational lensing images into three classes:

- **no** - no lensing
- **sphere** - spherical lens
- **vort** - vortex lens

The model combines **deep CNN feature extraction** with **physics constraints derived from gravitational lensing equations**.

Notebook: [DeepLense_task_vii.ipynb](DeepLense_task_vii.ipynb)

## Dataset

Total images: **37,500**


Images are stored as `.npy` arrays and normalized before training.


## Model

Two **PINN architectures** were implemented:

### 1. EfficientNet-PINN
- EfficientNet-B0 backbone
- Classification head
- Physics head predicting lens potential **ψ**

![efficientnet-results.png](efficientnet-results.png)

<br>

### 2. DenseNet-PINN
- DenseNet-121 backbone
- Classification head
- Physics head for potential field

The physics head enforces **gravitational lensing constraints** during training.

![densenet-results.png](densenet-results.png)


## Physics Loss

The loss combines:

Total Loss =
Classification Loss

λ₁ Poisson Loss

λ₂ Smoothness Loss


- **Poisson loss** enforces the lensing Poisson equation  
- **Smoothness loss** regularizes the predicted potential field


## Results

### EfficientNet-PINN

AUC ≈ 0.990 (macro averaged) <br>
Accuracy ≈ 0.938


### DenseNet-PINN
AUC ≈ 0.9957 (macro averaged) <br>
Accuracy ≈ 0.965