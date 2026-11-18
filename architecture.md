# Basic System Architecture
## Arecanut Ripeness Classification Research Pipeline

**Status:** Starter proposal. Update after inspecting the actual dataset and paper.

## 1. High-level flow

```text
                 Zenodo Dataset Archive
                           |
                           v
                    Raw Dataset Store
                    (immutable source)
                           |
                           v
                      Dataset Audit
          - file inventory and readability
          - labels and class counts
          - dimensions and duplicates
          - annotation inspection
                           |
                           v
                Dataset Manifest + Splits
                 train / validation / test
                           |
                           v
                   Image Preprocessing
          - load and resize
          - RGB representation
          - HSV conversion
          - YCgCr conversion
          - normalization
                           |
                           v
                Classification Experiments
             +-------------+-------------+
             |             |             |
             v             v             v
          MobileNet       VGG16        DenseNet
             |             |             |
             +-------------+-------------+
                           |
                           v
                     Model Evaluation
          - accuracy / precision / recall
          - F1 / confusion matrix
          - per-class support
          - runtime / resource use
                           |
                           v
                Results + Experiment Log
```

## 2. Optional research extensions

```text
Verified annotations (if available)
                |
                v
        Segmentation dataset
                |
                v
     Segmentation model experiments
                |
                v
        Predicted object masks
                |
                v
  Masked/cropped image classification
                |
                v
      Optional fusion experiments
```

Segmentation and fusion are not first-milestone requirements. Their design depends on the paper and available ground-truth annotations.

## 3. Main modules
| Module | Responsibility |
|---|---|
| `data/` | Discovery, manifests, labels, splits, loaders |
| `preprocessing/` | Loading, resizing, colour conversion, normalization |
| `models/` | Model construction and classifier heads |
| `training/` | Training, validation, checkpoints |
| `evaluation/` | Metrics, plots, confusion matrices, reports |
| `segmentation/` | Future segmentation models and metrics |
| `fusion/` | Future, explicitly defined fusion methods |
| `utils/` | Seeds, configuration, logging, device selection |

## 4. Data-flow principles
- Raw images are read-only.
- Manifests describe source files and labels.
- Save split definitions.
- Record every transformation.
- Training data trains; validation selects; test evaluates final performance.
- Each run writes to a unique results directory.

## 5. Proposed experiment matrix
| Colour representation | MobileNet | VGG16 | DenseNet |
|---|---:|---:|---:|
| RGB | Planned | Planned | Planned |
| HSV | Planned | Planned | Planned |
| YCgCr | Planned | Planned | Planned |

This is a proposed controlled experiment matrix, not a claim about what the source paper implemented.

## 6. Decisions to verify
- Archive directory and label structure.
- Whole bunch versus individual nuts.
- Segmentation annotation availability.
- Image dimensions and preprocessing.
- Framework and pretrained weights.
- Grouping metadata for leakage-safe splits.
- Exact segmentation and fusion procedure in the source paper.
