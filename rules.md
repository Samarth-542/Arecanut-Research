# Project Rules

## 1. Research integrity
1. Never invent dataset statistics or experimental results.
2. Mark statements as **Verified**, **Proposed**, or **Unknown**.
3. Do not claim reproduction until data split, preprocessing, implementation, and evaluation are checked.
4. Never manipulate results to improve appearance.
5. Record failed and inconclusive experiments.

## 2. Dataset rules
1. `dataset/raw/` is immutable.
2. Keep processed and augmented data outside raw storage.
3. Preserve source filenames and maintain a manifest.
4. Check corruption, duplicates, imbalance, and related-image groups.
5. Split by source group when needed to prevent leakage.
6. Keep augmented copies in the same partition as their source.
7. Never use test data for tuning, threshold selection, early stopping, or model selection.

## 3. Coding rules
1. Use notebooks for exploration; put reusable logic in `src/`.
2. Avoid duplicated preprocessing and metric code.
3. Keep parameters configurable.
4. Use descriptive names and small functions.
5. Set and record random seeds where possible.
6. Record Python, PyTorch, Torchvision, CUDA, and library versions.
7. Avoid machine-specific absolute paths in reusable code.
8. Never commit secrets or API keys.

## 4. Experiment rules
Every run records: unique ID, date, dataset manifest/version, split ID, model, colour space, input size, normalization, augmentation, optimizer, learning rate, batch size, epochs, stopping rule, seed, software/hardware, metrics, and output paths.

Comparisons must use equivalent splits and protocols. Explain unavoidable differences.

## 5. Model and colour-space rules
1. RGB, HSV, and YCgCr are image representations, not classifier architectures.
2. MobileNet, VGG16, and DenseNet are classifier architectures.
3. Do not assume a best model or colour space before testing.
4. Document channel ordering, numeric ranges, conversion library, and normalization.
5. Match preprocessing to model input expectations.
6. Treat segmentation and classification as separate tasks.

## 6. Segmentation and fusion rules
1. Do not implement Mask R-CNN until annotation availability is confirmed.
2. Distinguish ground-truth masks, predicted masks, and pseudo-labels.
3. Define segmentation metrics before evaluation.
4. State precisely what fusion combines and provide its equation.
5. Never tune fusion weights or thresholds on the test set.
6. Include single-branch and no-fusion baselines.

## 7. Documentation and Git
- Update research notes after major concepts, decisions, and results.
- Label preliminary results clearly.
- Record unresolved questions instead of guessing.
- Commit code, docs, configs, and small manifests.
- Do not commit datasets, checkpoints, virtual environments, or large generated artifacts.
