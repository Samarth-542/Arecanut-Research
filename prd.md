# Product Requirements Document (PRD)
## Arecanut Ripeness Classification Research Project

**Status:** Initial draft | **Version:** 0.1

## 1. Purpose
Build a reproducible computer-vision research pipeline to investigate arecanut ripeness classification. Begin with dataset auditing and reliable baselines. Add segmentation and fusion only after confirming the annotations and exact research method.

## 2. Problem statement
Investigate whether image-processing and deep-learning methods can classify arecanut bunch images consistently.

Initial target: **whole-image / whole-bunch binary classification**:
- `ripe`
- `unripe`

This is not continuous maturity-percentage prediction unless suitable continuous ground-truth labels are available.

## 3. Goals
1. Audit the Zenodo dataset before training.
2. Reproduce baseline experiments where implementation and settings can be verified.
3. Compare RGB, HSV, and YCgCr under controlled conditions.
4. Compare MobileNet, VGG16, and DenseNet fairly.
5. Evaluate with class-wise metrics, not accuracy alone.
6. Investigate segmentation/fusion only if annotations and methodology support them.
7. Keep experiments reproducible and traceable.

## 4. First-milestone non-goals
- Public web/mobile deployment.
- Claims of field-ready performance.
- Exact maturity percentage prediction.
- Mask R-CNN implementation before annotation inspection.
- Claiming fusion improves results before testing it.
- Forcing results to match a paper.

## 5. Dataset
Source: https://zenodo.org/records/19426901

Keep the original archive unchanged in `dataset/raw/`. Verify and record:
- Archive name, size, download date, source URL/DOI.
- Extracted directory tree.
- Readable image count and class distribution.
- Image formats and dimensions.
- Corrupt and duplicate images.
- Label and annotation formats.
- Related-image groups (same bunch, plant, location, or capture session).

Do not assume dataset size, class balance, or annotation type before local inspection.

## 6. Functional requirements
- **FR-01 Dataset audit:** generate an inventory and audit report.
- **FR-02 Reproducible splits:** save train/validation/test split definitions; group related images before splitting when appropriate.
- **FR-03 Preprocessing:** support loading, resizing, normalization, and RGB/HSV/YCgCr conversion.
- **FR-04 Baselines:** configurable MobileNet, VGG16, and DenseNet training.
- **FR-05 Evaluation:** accuracy, precision, recall, F1, confusion matrix, and per-class support.
- **FR-06 Experiment tracking:** save configuration, seed, split, software versions, metrics, and output paths.
- **FR-07 Segmentation extension:** if masks exist, evaluate with suitable IoU/Dice and task-appropriate metrics.
- **FR-08 Fusion extension:** document exactly what is fused, the equation, thresholds/weights, and parameter-selection method.

## 7. Non-functional requirements
- Reproducibility through recorded seeds and configurations.
- No raw-data modification.
- Modular code separating data, preprocessing, models, training, and evaluation.
- Resource awareness for an NVIDIA RTX 4060 Laptop GPU with 8 GB VRAM, with CPU fallback.
- No test-set leakage.

## 8. Experimental principles
- Use equivalent splits and protocols for model comparisons.
- Fit data-dependent preprocessing on training data only.
- Augment training data only.
- Never place augmented copies of one source image across different splits.
- Use validation for model selection and test only for final evaluation.
- Preserve failed and incomplete runs in the experiment log.

## 9. First-milestone acceptance criteria
1. Original archive preserved in `dataset/raw/`.
2. Extracted structure documented.
3. Dataset audit script runs.
4. Counts, class distribution, dimensions, and corrupt-file checks reported.
5. Label/annotation format understood or marked unresolved.
6. No model training before audit review.

## 10. Open questions
- What is the archive's exact folder and label structure?
- Are labels folder-based, CSV-based, or another format?
- Are masks or bounding-box annotations included?
- Are images grouped by plant, bunch, location, or capture session?
- What is the ground-truth rule for mixed-maturity bunches?
- Which exact manuscript method and repository implementation are to be reproduced?
