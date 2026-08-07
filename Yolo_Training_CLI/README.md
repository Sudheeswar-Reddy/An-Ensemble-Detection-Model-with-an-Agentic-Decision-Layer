# Ultralytics YOLO Object Detection Training

This repository contains three different training configurations for training object detection models using the **Ultralytics YOLO framework**.

The provided configurations are:

- **YOLO11m**
- **YOLO26m**
- **RT-DETR-L**

All training commands use the Ultralytics Command Line Interface (CLI) and are configured for long-duration training on a custom dataset.

---

# Table of Contents

- Prerequisites
- Installation
- Dataset Structure
- Training Configurations
  - YOLO11m
  - YOLO26m
  - RT-DETR-L
- Hyperparameter Explanation
- Training Outputs
- Resuming Training
- References

---

# Prerequisites

Before training, ensure you have:

- Python 3.9+
- NVIDIA GPU with CUDA support (recommended)
- CUDA-compatible PyTorch
- Ultralytics installed

Install Ultralytics:

```bash
pip install ultralytics
```

Verify installation:

```bash
yolo checks
```

---

# Dataset Structure

Ultralytics expects the dataset to be organized as:

```
dataset/
│
├── images/
│   ├── train/
│   ├── val/
│   └── test/
│
├── labels/
│   ├── train/
│   ├── val/
│   └── test/
│
└── data.yaml
```

Example `data.yaml`

```yaml
path: dataset

train: images/train
val: images/val
test: images/test

names:
  0: defect
```

Replace the dataset path in the training command with your own `data.yaml`.

---

# Training Configurations

## 1. YOLO11m

YOLO11m is a medium-sized model in the YOLO11 family. It offers a balance between inference speed and detection accuracy, making it suitable for most object detection tasks.

Training command used in this project: :contentReference[oaicite:0]{index=0}

```bash
yolo detect train ^
  model=yolo11m.pt ^
  data="path\to\data.yaml" ^
  imgsz=640 ^
  batch=8 ^
  epochs=200 ^
  patience=30 ^
  optimizer=AdamW ^
  lr0=0.001 ^
  cos_lr=True ^
  warmup_epochs=5 ^
  hsv_h=0.0 hsv_s=0.0 hsv_v=0.3 ^
  degrees=0.0 shear=0.0 perspective=0.0 ^
  fliplr=0.5 flipud=0.0 ^
  mosaic=1.0 ^
  close_mosaic=15 ^
  cache=disk ^
  device=0 ^
  workers=4 ^
  seed=0 ^
  verbose=True ^
  plots=True ^
  save_period=10 ^
  project="path/to/results" ^
  name="YOLO11m"
```

---

## 2. YOLO26m

YOLO26m is a larger model than YOLO11m and contains more parameters. It generally provides higher accuracy at the cost of increased GPU memory usage and longer training time.

Training command used in this project: :contentReference[oaicite:1]{index=1}

```bash
yolo detect train ^
  model=yolo26m.pt ^
  data="path\to\data.yaml" ^
  imgsz=640 ^
  batch=8 ^
  epochs=200 ^
  patience=30 ^
  optimizer=AdamW ^
  lr0=0.001 ^
  cos_lr=True ^
  warmup_epochs=5 ^
  hsv_h=0.0 hsv_s=0.0 hsv_v=0.3 ^
  degrees=0.0 shear=0.0 perspective=0.0 ^
  fliplr=0.5 flipud=0.0 ^
  mosaic=1.0 ^
  close_mosaic=15 ^
  cache=disk ^
  device=0 ^
  workers=4 ^
  seed=0 ^
  verbose=True ^
  plots=True ^
  save_period=10 ^
  project="path/to/results" ^
  name="YOLO26m"
```

---

## 3. RT-DETR-L

RT-DETR (Real-Time Detection Transformer) is a transformer-based object detector integrated into the Ultralytics framework. Unlike traditional YOLO models, RT-DETR removes Non-Maximum Suppression (NMS) during inference while maintaining real-time performance.

Training command used in this project: :contentReference[oaicite:2]{index=2}

```bash
yolo detect train ^
  model=rtdetr-l.pt ^
  data="path\to\data.yaml" ^
  imgsz=640 ^
  batch=8 ^
  epochs=200 ^
  patience=30 ^
  optimizer=AdamW ^
  lr0=0.0001 ^
  cos_lr=True ^
  warmup_epochs=5 ^
  hsv_h=0.0 hsv_s=0.0 hsv_v=0.3 ^
  degrees=0.0 shear=0.0 perspective=0.0 ^
  fliplr=0.5 flipud=0.0 ^
  cache=disk ^
  device=0 ^
  workers=4 ^
  seed=0 ^
  verbose=True ^
  plots=True ^
  save_period=10 ^
  project="path/to/results" ^
  name="Yolo_RT-DETR"
```

---

# Hyperparameter Explanation

The following hyperparameters are used in the training commands.

| Parameter | Description |
|-----------|-------------|
| `model` | Pretrained model used for transfer learning. |
| `data` | Path to the dataset configuration file (`data.yaml`). |
| `imgsz` | Input image resolution used during training. |
| `batch` | Number of images processed in each iteration. |
| `epochs` | Maximum number of training epochs. |
| `patience` | Early stopping patience. Training stops if validation metrics do not improve. |
| `optimizer` | Optimization algorithm. AdamW was used in these experiments. |
| `lr0` | Initial learning rate. |
| `cos_lr` | Enables cosine learning rate scheduling. |
| `warmup_epochs` | Number of warm-up epochs before reaching the full learning rate. |
| `hsv_h` | Hue augmentation factor. |
| `hsv_s` | Saturation augmentation factor. |
| `hsv_v` | Brightness augmentation factor. |
| `degrees` | Maximum rotation augmentation. |
| `shear` | Shear transformation amount. |
| `perspective` | Perspective transformation amount. |
| `fliplr` | Probability of horizontal image flipping. |
| `flipud` | Probability of vertical image flipping. |
| `mosaic` | Enables Mosaic augmentation (YOLO models only). |
| `close_mosaic` | Disables Mosaic augmentation during the final training epochs (YOLO models only). |
| `cache` | Dataset caching mode. `disk` stores cached images on disk instead of RAM. |
| `device` | GPU device ID used for training. |
| `workers` | Number of dataloader worker processes. |
| `seed` | Random seed for reproducibility. |
| `verbose` | Displays detailed training logs. |
| `plots` | Saves training curves and evaluation plots. |
| `save_period` | Saves model checkpoints every specified number of epochs. |
| `project` | Directory where training results are stored. |
| `name` | Name of the experiment folder. |

---

# Running Training

Open a terminal in the project directory and execute one of the commands above.

Example:

```bash
yolo detect train ...
```

During training, Ultralytics automatically creates a results directory similar to:

```
results/
└── YOLO11m/
```

or

```
results/
└── YOLO26m/
```

or

```
results/
└── Yolo_RT-DETR/
```

The folder typically contains:

```
weights/
    best.pt
    last.pt

results.csv
results.png
confusion_matrix.png
PR_curve.png
F1_curve.png
args.yaml
```

---

# Resuming Training

Training can be resumed from the last checkpoint:

```bash
yolo detect train resume model=path/to/last.pt
```

---

# Documentation

This project uses the Ultralytics framework.

Official Documentation

https://docs.ultralytics.com/

Training Configuration

https://docs.ultralytics.com/usage/cfg/

Hyperparameters

https://docs.ultralytics.com/guides/hyperparameter-tuning/

RT-DETR Documentation

https://docs.ultralytics.com/models/rtdetr/

YOLO Models

https://docs.ultralytics.com/models/

---

# Notes

- Replace `path/to/data.yaml` with the location of your dataset configuration.
- Replace `path/to/results` with the directory where you want training outputs to be stored.
- Ensure the required pretrained model weights (`yolo11m.pt`, `yolo26m.pt`, or `rtdetr-l.pt`) are available or downloadable by Ultralytics.
- For reproducible experiments, keep the random seed fixed.
- Hyperparameter definitions and recommended configurations are based on the official Ultralytics documentation.