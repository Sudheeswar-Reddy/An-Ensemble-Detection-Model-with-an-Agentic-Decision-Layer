# YOLO26m Training Results

## Model Overview

| Item | Value |
|------|-------|
| Model | YOLO26m |
| Task | Object Detection |
| Total Epochs | **113** (Epochs 0–112 shown) |
| Training Time | **16 Hours 42 Minutes** |

---

# Final Validation Metrics

| Metric | Value |
|--------|------:|
| Precision | **0.84054** |
| Recall | **0.76272** |
| mAP@0.50 | **0.79830** |
| mAP@0.50:0.95 | **0.54311** |

These values correspond to the final validation epoch shown in the uploaded `results.csv`.

---

# Training Summary

The training curves show continuous optimization across the recorded epochs.

## Training Losses

| Loss | Initial Trend | Final Value |
|------|---------------|------------:|
| Box Loss | Continuous decrease | **0.88873** |
| Classification Loss | Continuous decrease | **0.40594** |
| DFL Loss | Continuous decrease | **0.00455** |

### Observations

- Training box loss decreases steadily throughout training.
- Training classification loss continuously decreases.
- Training DFL loss also decreases across the training process.
- No loss divergence is visible in the provided training curves.

---

## Validation Losses

| Loss | Final Value |
|------|------------:|
| Box Loss | **1.10680** |
| Classification Loss | **0.75088** |
| DFL Loss | **0.00756** |

### Observations

- Validation box loss decreases during training and becomes relatively stable toward the end.
- Validation DFL loss follows a similar decreasing trend before stabilizing.
- Validation classification loss decreases during earlier epochs and increases slightly during the later epochs, as shown in the validation curve.

---

# Metric Progression

## Precision

Final Precision

**0.84054**

### Observations

- Precision increases substantially during the early epochs.
- Some fluctuations are present throughout training.
- The metric remains relatively stable during the later epochs.

---

## Recall

Final Recall

**0.76272**

### Observations

- Recall increases steadily during training.
- Later epochs show comparatively smaller improvements.
- The metric remains relatively stable near the end of training.

---

## mAP@0.50

Final

**0.79830**

### Observations

- Rapid improvement is visible during the initial training phase.
- Improvement slows during later epochs.
- The metric stabilizes near the final epochs.

---

## mAP@0.50:0.95

Final

**0.54311**

### Observations

- Continuous improvement is visible throughout training.
- Later epochs provide smaller incremental improvements.
- The metric stabilizes toward the end.

---

# Precision–Recall Analysis

Overall mAP@0.50

**0.837**

(Shown as **all classes 0.837 mAP@0.5** in the Precision–Recall curve.)

## Per-class AP@0.50

| Class | AP@0.50 |
|-------------------------|--------:|
| black_core | **0.982** |
| corner | **0.995** |
| crack | **0.725** |
| finger | **0.919** |
| fragment | **0.665** |
| horizontal_dislocation | **0.995** |
| printing_error | **0.995** |
| scratch | **0.000** |
| short_circuit | **0.995** |
| star_crack | **0.912** |
| thick_line | **0.869** |
| vertical_dislocation | **0.995** |

---

# Per-Class Performance

## High Performing Classes

| Class | AP@0.50 |
|-------------------------|--------:|
| corner | **0.995** |
| horizontal_dislocation | **0.995** |
| printing_error | **0.995** |
| short_circuit | **0.995** |
| vertical_dislocation | **0.995** |
| black_core | **0.982** |
| finger | **0.919** |
| star_crack | **0.912** |

These classes exhibit strong Precision–Recall performance according to the PR curve.

---

## Moderate Performance

| Class | AP@0.50 |
|----------------|--------:|
| thick_line | **0.869** |
| crack | **0.725** |
| fragment | **0.665** |

These classes demonstrate measurable detection capability while exhibiting lower AP values than the highest-performing categories.

---

## Class with AP = 0

The evaluation reports

- scratch

with

**AP@0.50 = 0.000**

No conclusion regarding the reason is drawn from the provided artifacts alone.

---

# Confidence Curve Analysis

## Best F1 Operating Point

Overall F1 reaches its maximum at

- **F1 = 0.81**
- **Confidence Threshold = 0.377**

This corresponds to the highest overall F1 reported on the F1–Confidence curve.

---

## Precision–Confidence

The Precision–Confidence curve shows

- Precision generally increases as confidence increases.
- Overall precision reaches **1.00** at a confidence threshold of **0.977**, as indicated in the plot.
- Individual classes exhibit different confidence-response behaviors.

---

## Recall–Confidence

The Recall–Confidence curve shows

- Overall recall is highest at very low confidence thresholds.
- Recall gradually decreases as the confidence threshold increases.
- The legend reports **all classes recall = 0.87 at confidence = 0.000**.

---

## F1–Confidence

The F1 curve indicates

- Peak overall performance at **F1 = 0.81**.
- Best operating confidence threshold of **0.377**.
- Lower confidence thresholds provide higher recall.
- Higher confidence thresholds improve precision while reducing recall.

---

# Confusion Matrix Analysis

The uploaded confusion matrices show the following observable characteristics.

- Several classes exhibit strong diagonal values, indicating successful predictions.
- Misclassifications are visible between multiple defect classes.
- The background column contains large values for several predicted classes.
- The normalized confusion matrix shows perfect normalized diagonal values (1.00) for:
  - horizontal_dislocation
  - vertical_dislocation
- The normalized confusion matrix shows comparatively lower diagonal values for:
  - fragment (0.33)
  - star_crack (0.39)
  - thick_line (0.36)
  - crack (0.64)
- The scratch row contains no successful diagonal detection in the normalized confusion matrix.

No further interpretation beyond the plotted matrices is made.

---

# Learning Behaviour

The uploaded learning curves indicate

- Continuous reduction of training losses.
- Reduction of validation box and DFL losses.
- Validation classification loss decreases initially and increases slightly near the end.
- Increasing Precision.
- Increasing Recall.
- Increasing mAP@0.50.
- Increasing mAP@0.50:0.95.

No numerical instability or loss divergence is visible in the provided plots.

---

# Overall Evaluation

## Strengths

- Stable optimization throughout training.
- Continuous reduction in training losses.
- Improvement in validation metrics throughout most of training.
- High AP for:
  - corner
  - horizontal_dislocation
  - printing_error
  - short_circuit
  - vertical_dislocation
  - black_core
  - finger
  - star_crack
- Overall mAP@0.50 of **0.837**.
- Best overall F1 of **0.81**.

---

## Areas Requiring Attention

The evaluation shows comparatively lower AP values for

- crack
- fragment
- thick_line

The evaluation reports

- scratch

with

**AP@0.50 = 0.000**

No explanation for this result is inferred from the uploaded evaluation artifacts.

---

# Final Results

| Metric | Final Value |
|--------------------------|----------------:|
| Precision | **0.84054** |
| Recall | **0.76272** |
| mAP@0.50 | **0.79830** |
| mAP@0.50:0.95 | **0.54311** |
| Overall PR mAP@0.50 | **0.837** |
| Best F1 | **0.81** |
| Best Confidence Threshold | **0.377** |
| Total Epochs | **113** |
| Training Time | **16 Hours 42 Minutes** |

---

# Included Evaluation Artifacts

- Training loss curves
- Validation loss curves
- Precision curve
- Recall curve
- mAP curves
- Precision–Recall curve
- Precision–Confidence curve
- Recall–Confidence curve
- F1–Confidence curve
- Confusion Matrix
- Normalized Confusion Matrix

These uploaded evaluation artifacts collectively provide a complete view of optimization behaviour, validation performance, confidence-threshold behaviour, class-wise detection performance, and confusion patterns without drawing conclusions beyond what is directly observable.