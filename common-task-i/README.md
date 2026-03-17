# DeepLense Common Task I

Multi-class gravitational lensing classification on `.npy` images using transfer learning in PyTorch.

## Objective

Classify each sample into one of three classes:

- `no` 
- `sphere`
- `vort`

- Notebook: [DeepLense_common_task_i.ipynb](DeepLense_common_task_i.ipynb)

## Dataset

The notebook uses the DeepLense dataset in `.npy` format and loads data from class folders.

- Training: 30,000 samples total (10,000 per class)
- Validation: 7,500 samples total (2,500 per class)
- Internal split used in notebook: 90% train, 10% validation from training folder

## Method

- Framework: PyTorch + Torchvision
- Input handling: `.npy` images converted to tensors
- Channel handling: single-channel inputs are repeated to 3 channels for ImageNet backbones
- Image size: `224 x 224`
- Augmentation (train)
- Optimizer: Adam (`lr=1e-4`, `weight_decay=1e-4`)
- Scheduler: ReduceLROnPlateau
- Loss: CrossEntropyLoss
- Epochs: 15
- Batch size: 32

## Models Evaluated

- ResNet50
![resnet50-results](resnet50-results.png)

- EfficientNet-B0
![efficientnet-results](efficientnet-results.png)


- DenseNet121
![densenet-results](densenet-results.png)


- MobileNetV3-Large
![mobilenet-results](mobilenet-results.png)


- (Model builders also included for ConvNeXt-Tiny, VGG16, and ViT-B/16)

## Key Results (Validation)

| Model | Val Accuracy | Macro AUC |
|---|---:|---:|
| ResNet50 | 80.40% | 0.941 |
| EfficientNet-B0 | 93.13% | 0.9883 |
| DenseNet121 | **96.27%** | **0.9956** |
| MobileNetV3-Large | 92.67% | 0.9863 |

### Best Model

**DenseNet121** achieved the strongest overall performance:

- Validation Accuracy: **96.27%**
- Macro AUC: **0.9956**
- Balanced class-wise precision/recall with minimal overfitting trend
