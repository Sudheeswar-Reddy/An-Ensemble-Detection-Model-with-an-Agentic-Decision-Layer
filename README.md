# Adaptive Ensemble Detection Framework for Photovoltaic Electroluminescence (EL) Defect Detection

## Overview

This repository contains the ongoing development of an **ensemble-based object detection framework** for **Photovoltaic Electroluminescence (EL) defect detection**. The primary objective of this project is to design and evaluate a **novel detection ensemble model** by combining multiple state-of-the-art YOLO detection models and, subsequently, integrating an **Agentic AI decision-making layer** to improve detection accuracy, robustness, and adaptability.

Unlike traditional approaches that rely on a single detector, this project investigates how multiple object detection models can collaboratively identify defects while reducing false positives and false negatives. After the ensemble is finalized, an Agentic AI layer will be introduced to intelligently reason over the outputs of the detectors and make the final decision.

---

# Problem Statement

Develop a **new ensemble object detection framework** using multiple YOLO-based detection models for photovoltaic electroluminescence defect detection.

The proposed framework aims to:

- Improve defect detection accuracy compared to a single detector.
- Reduce false positives and false negatives.
- Exploit the complementary strengths of different YOLO architectures.
- Design and evaluate different ensemble strategies (Parallel or Cascade).
- Integrate an Agentic AI layer that performs intelligent reasoning over detector outputs to produce the final prediction.

---

# Dataset

This project uses the **PVEL-AD (Photovoltaic Electroluminescence Anomaly Detection)** dataset.

### Dataset Download

https://drive.google.com/file/d/1EtteKnLhSFQ3XMCRXt5wKY-lDkIP7299/view?usp=drive_link

### Original Repository

https://github.com/binyisu/PVEL-AD

The original repository contains additional information regarding:

- Dataset structure
- Annotation format
- Class information
- Data splits
- Experimental setup

Please refer to the original repository for complete dataset documentation.

---

# Current Project Status

The project is currently in the detector training and evaluation phase.

## Completed

- Dataset preparation and preprocessing
- Training of **YOLO11m**
- Training of **YOLO26m**
- Collection and analysis of training results
- Comparison of detector performance

## Ongoing

- Training **RT-DETR (Transformer-based Detector)**

## Planned

- Compare YOLO and RT-DETR performance
- Design the final ensemble architecture
- Implement the selected ensemble
- Integrate an Agentic AI reasoning layer
- Evaluate the complete system

---

# Models Trained

## 1. YOLO11m

- Detection Model
- Training completed successfully
- Approximate training time:
  - **15 Hours**

---

## 2. YOLO26m

- Detection Model
- Training completed successfully
- Approximate training time:
  - **16 Hours 30 Minutes**

---

# Hardware Used

All experiments were performed on:

- **GPU:** NVIDIA RTX 4050 Laptop GPU
- **VRAM:** 6 GB
- **Batch Size:** 8

The entire training pipeline has been developed and executed using this hardware configuration.

---

# Training Details

All command-line interfaces (CLIs), hyperparameters, training commands, and additional implementation notes are available in the **Yolo_Training_CLI** directory.

The folder contains its own README with detailed explanations of:

- Training commands
- Hyperparameters
- Dataset configuration
- Training configuration
- Resume commands
- Additional implementation notes

---

# Results

The training results of the completed models are available inside the **Results** directory.

The folder currently contains:

- YOLO11m training results
- YOLO26m training results
- Performance metrics
- Evaluation plots
- Training curves

These results serve as the basis for selecting the final ensemble strategy.

---

# Future Work

The next phase of the project focuses on completing RT-DETR training and designing the final ensemble architecture.

The following ensemble strategies are currently under consideration:

- Parallel Ensemble
- Cascade Ensemble
- Confidence-based Dynamic Ensemble
- Hybrid Ensemble

The final architecture will be selected after a detailed comparison of:

- YOLO11m
- YOLO26m
- RT-DETR

using their detection accuracy, precision, recall, mAP scores, inference time, and robustness.

---

# Agentic AI Layer

A key objective of this project is the integration of an **Agentic AI layer** after the ensemble stage.

Rather than directly accepting detector outputs, the Agentic AI module will:

- Analyze predictions from multiple detectors
- Resolve conflicts between model outputs
- Evaluate confidence scores
- Apply reasoning strategies
- Produce the final defect detection decision

This transforms the framework from a conventional ensemble into an intelligent decision-making system capable of adaptive reasoning.

---

# Repository Structure

```text
.
├── Dataset/
├── Results/
│   ├── YOLO11m/
│   └── YOLO26m/
│
├── Yolo_Training_CLI/
│   ├── README.md
│   ├── YOLO11m_CLI.txt
│   ├── YOLO26m_CLI.txt
│   └── RT-DETR_CLI.txt
│
├── Ensemble/
│
├── Agentic_AI/
│
├── Docs/
│
└── README.md
```

---

# Repository Status

| Component | Status |
|-----------|--------|
| Dataset Preparation | ✅ Completed |
| YOLO11m Training | ✅ Completed |
| YOLO26m Training | ✅ Completed |
| Result Analysis | ✅ Completed |
| RT-DETR Training | 🔄 In Progress |
| Ensemble Design | ⏳ Pending |
| Agentic AI Layer | ⏳ Pending |
| Final Evaluation | ⏳ Pending |

---

# Acknowledgements

This work builds upon the publicly available **PVEL-AD** dataset and associated resources provided by the original authors.

- Dataset Repository: https://github.com/binyisu/PVEL-AD
- Dataset Download: https://drive.google.com/file/d/1EtteKnLhSFQ3XMCRXt5wKY-lDkIP7299/view?usp=drive_link

We gratefully acknowledge the authors for making this benchmark dataset publicly available for research.