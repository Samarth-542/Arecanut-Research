# Project Memory
## Persistent Context

Update this file when facts are verified or decisions change. Do not turn assumptions into facts.

## Project identity
- Project: Arecanut ripeness classification research.
- Initial task: binary whole-bunch image classification (`ripe` / `unripe`).
- Dataset source: https://zenodo.org/records/19426901
- Codebase is being created from scratch.
- Raw dataset must remain unchanged.

## Planned research dimensions
- Colour representations: RGB, HSV, YCgCr.
- Classifiers: MobileNet, VGG16, DenseNet.
- Possible later extension: segmentation and fusion, conditional on annotations and source-method verification.
These are plans, not confirmed dataset contents or achieved results.

## Reported machine
- Windows 11.
- AMD Ryzen 5 CPU.
- 16 GB RAM.
- NVIDIA GeForce RTX 4060 Laptop GPU, 8 GB VRAM.
- AMD integrated Radeon graphics.
Use NVIDIA for CUDA training after verifying the PyTorch CUDA setup. Do not assume CUDA is ready.

## Collaboration preferences
- Explain concepts in beginner-friendly language.
- Work incrementally: explain, implement, verify, then proceed.
- Avoid overwhelming the learner with a complete complex pipeline at once.
- Maintain parallel research notes suitable for Notion.
- Be strict about reproducibility.

## Scientific cautions
- Do not assume the dataset has 1,017 images; verify locally.
- Do not assume class balance, label quality, or masks.
- Whole-bunch binary classification is not continuous maturity-percentage prediction.
- Mixed-maturity bunches need a documented ground-truth rule.
- Verify paper claims against manuscript, code, and split protocol.
- Separate verified facts, proposals, and unknowns.

## Current status
- [x] Starter scope and architecture defined.
- [ ] Download dataset.
- [ ] Extract dataset.
- [ ] Audit structure, images, labels, duplicates, annotations.
- [ ] Verify Python/PyTorch CUDA environment.
- [ ] Create reproducible splits.
- [ ] Train first baseline.

## Decision log
| Date | Decision | Status |
|---|---|---|
| 2026-11-16 | Start a clean, modular research codebase | Confirmed |
| 2026-11-16 | Audit dataset before training | Confirmed |
| 2026-11-16 | Treat segmentation/fusion as later, evidence-dependent extensions | Confirmed |

## Update protocol
For every new fact, record observation, source, status (verified/proposed/unknown), and date. Preserve old decisions in the log when they change.
