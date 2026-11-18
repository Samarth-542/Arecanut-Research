
# VGG16 — Experimental Conclusion

## 1. Overall Performance

The VGG16 transfer-learning model was evaluated using three
color-space representations: RGB, HSV, and YCgCr.

| Color Space | Test Accuracy | Macro F1 | Test Loss |
|:------------|--------------:|---------:|----------:|
| RGB | 88.57% | 0.8732 | 0.2408 |
| HSV | 80.00% | 0.7890 | 0.4411 |
| YCgCr | 80.00% | 0.7680 | 0.5000 |

## 2. Key Findings

- **RGB:** Achieved the highest observed test accuracy
  (88.57%) and macro F1 (0.8732).

- **HSV:** Achieved 80.00% test accuracy, with a macro F1
  score of 0.7890.

- **YCgCr:** Achieved 80.00% test accuracy, with a macro F1
  score of 0.7680.

- RGB also recorded the lowest test loss (0.2408).

## 3. Validation Checkpoint Selection

The best checkpoints were selected using validation loss:

| Color Space | Best Epoch | Best Validation Loss |
|:------------|-----------:|---------------------:|
| RGB | 12 | 0.2286 |
| HSV | 11 | 0.4634 |
| YCgCr | 12 | 0.3189 |

## 4. Research Interpretation

Under the current experimental setup, RGB provided the
strongest overall VGG16 classification performance.

HSV and YCgCr did not outperform RGB on the observed test
accuracy or macro F1 metrics.

These findings suggest that the RGB representation was
more effective for this particular dataset and experimental
configuration. They do not establish that RGB is universally
superior to alternative color spaces.

## 5. Limitations

- The test set contains only 70 images.
- Performance differences require further statistical validation.
- Results are based on one grouped train-validation-test split.
- External field validation under varying illumination,
  occlusion, and background conditions remains necessary.

## 6. Final Conclusion

Among the three evaluated color-space representations,
**VGG16 with RGB input achieved the strongest observed
classification performance**, recording 88.57% test accuracy
and 0.8732 macro F1.

Further evaluation using repeated grouped splits, confidence
intervals, and independent field data is required before
making broader generalization claims.
