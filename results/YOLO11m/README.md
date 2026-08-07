# YOLO11m Training Results

## Model Overview

| Item | Value |
|------|-------|
| Model | YOLO11m |
| Task | Object Detection |
| Total Epochs | 116 |
| Training Time | 12 Hours 37 Minutes |

---

# Final Validation Metrics

| Metric | Value |
|---------|------:|
| Precision | **0.7009** |
| Recall | **0.6489** |
| mAP@0.50 | **0.6505** |
| mAP@0.50:0.95 | **0.4515** |

These values correspond to the final validation epoch.

---

# Training Summary

The model shows consistent optimization throughout training.

## Training Losses

| Loss | Initial Trend | Final Value |
|------|--------------|------------:|
| Box Loss | Steady decrease | **0.8339** |
| Classification Loss | Continuous decrease | **0.4321** |
| DFL Loss | Continuous decrease | **0.9208** |

Observations

- All three training losses decrease throughout training.
- No sudden divergence or instability is visible.
- Optimization remains stable until the final epoch.

---

## Validation Losses

| Loss | Final Value |
|------|------------:|
| Box Loss | **1.2216** |
| Classification Loss | **0.6474** |
| DFL Loss | **1.0414** |

Observations

- Validation losses decrease rapidly during early epochs.
- Improvements become smaller in later epochs.
- Validation curves remain relatively stable during the final training phase.

---

# Metric Progression

## Precision

Final Precision

**0.7009**

Observations

- Precision improves steadily throughout training.
- Intermediate fluctuations are present but the overall trend is upward.
- The metric stabilizes during later epochs.

---

## Recall

Final Recall

**0.6489**

Observations

- Recall increases consistently.
- Growth slows during the later epochs.
- No abrupt degradation is visible.

---

## mAP@0.50

Final

**0.6505**

Observations

- Rapid improvement during early training.
- Gradual convergence after approximately the midpoint of training.
- Stable during final epochs.

---

## mAP@0.50:0.95

Final

**0.4515**

Observations

- Continuous improvement throughout training.
- Later epochs provide incremental gains.
- Metric stabilizes toward the end.

---

# Precision–Recall Analysis

Overall mAP@0.50

**0.681**

Per-class AP@0.50

| Class | AP@0.50 |
|--------|---------:|
| black_core | **0.990** |
| corner | **0.995** |
| crack | **0.765** |
| finger | **0.935** |
| fragment | **0.665** |
| horizontal_dislocation | **0.000** |
| printing_error | **0.995** |
| scratch | **0.000** |
| short_circuit | **0.995** |
| star_crack | **0.950** |
| thick_line | **0.878** |
| vertical_dislocation | **0.000** |

---

# Per-Class Performance

## High Performing Classes

The following classes achieve AP values close to 1.0.

| Class | AP@0.50 |
|--------|---------:|
| corner | 0.995 |
| printing_error | 0.995 |
| short_circuit | 0.995 |
| black_core | 0.990 |
| star_crack | 0.950 |
| finger | 0.935 |

These classes exhibit strong precision-recall characteristics.

---

## Moderate Performance

| Class | AP@0.50 |
|--------|---------:|
| thick_line | 0.878 |
| crack | 0.765 |
| fragment | 0.665 |

These classes show measurable detection capability while leaving room for improvement.

---

## Classes with AP = 0

The evaluation reports:

- horizontal_dislocation
- scratch
- vertical_dislocation

Each has

**AP@0.50 = 0.000**

This README intentionally does **not** infer the reason, since AP alone does not identify whether the cause is insufficient detections, dataset characteristics, annotation issues, or other factors.

---

# Confidence Curve Analysis

## Best F1 Operating Point

Overall F1 reaches its maximum at

- **F1 = 0.61**
- **Confidence Threshold = 0.167**

This threshold represents the highest combined balance between precision and recall according to the evaluation.

---

## Precision–Confidence

The Precision–Confidence curve shows

- increasing precision with higher confidence thresholds
- near-perfect precision at very high confidence thresholds
- expected reduction in prediction count as confidence increases

---

## Recall–Confidence

The Recall–Confidence curve shows

- highest recall at low confidence thresholds
- gradual reduction as confidence threshold increases
- expected trade-off between false positives and missed detections

---

## F1–Confidence

The F1 curve indicates

- peak overall performance near **0.167 confidence**
- lower thresholds increase recall at the expense of precision
- higher thresholds increase precision while reducing recall

---

# Confusion Matrix Analysis

The confusion matrices provide class-wise prediction behavior.

Observed characteristics include

- Strong diagonal values for several classes, indicating successful classification.
- Misclassifications are present for some defect categories.
- Background predictions constitute a substantial portion of the matrix, reflecting false negatives during evaluation.
- Several classes with AP = 0 correspond to minimal or absent successful detections within the confusion matrix.

No further conclusions are drawn beyond what is directly observable.

---

# Learning Behaviour

The training curves indicate

- stable optimization
- decreasing training losses
- decreasing validation losses
- increasing precision
- increasing recall
- increasing mAP

No evidence of numerical instability or loss divergence is visible in the provided plots.

---

# Overall Evaluation

## Strengths

- Stable optimization throughout training.
- Continuous reduction in training and validation losses.
- Strong performance for several defect categories.
- High AP for:
  - black_core
  - corner
  - printing_error
  - short_circuit
  - star_crack
  - finger
- Stable convergence of mAP metrics.

---

## Areas Requiring Attention

The evaluation identifies comparatively lower performance for

- crack
- fragment

The following classes obtain zero AP in this evaluation

- horizontal_dislocation
- scratch
- vertical_dislocation

This README intentionally avoids attributing causes without additional evidence.

---

# Final Results

| Metric | Final Value |
|---------|------------:|
| Precision | **0.7009** |
| Recall | **0.6489** |
| mAP@0.50 | **0.6505** |
| mAP@0.50:0.95 | **0.4515** |
| Best F1 | **0.61** |
| Best Confidence Threshold | **0.167** |
| Total Epochs | **116** |
| Training Time | **12 Hours 37 Minutes** |

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

These artifacts collectively provide a comprehensive view of model optimization, convergence, and class-wise detection performance.