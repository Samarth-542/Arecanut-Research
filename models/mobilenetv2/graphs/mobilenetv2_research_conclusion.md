
# MobileNetV2 — Experimental Results and Conclusion

## 1. Experimental Overview

MobileNetV2 was evaluated using three input color-space
representations: RGB, HSV, and YCgCr.

The experiments used the same grouped training,
validation, and test dataset split.

## 2. Test Performance

| Color Space | Accuracy | Macro Precision | Macro Recall | Macro F1 | Test Loss |
|---|---:|---:|---:|---:|---:|
| YCgCr | 92.86% | 0.9490 | 0.9038 | 0.9199 | 0.2187 |\n| RGB | 91.43% | 0.9252 | 0.8925 | 0.9049 | 0.1967 |\n| HSV | 81.43% | 0.8062 | 0.7893 | 0.7959 | 0.4037 |\n

## 3. Key Findings

- **YCgCr** achieved the highest observed test
  accuracy of 92.86%.
- **YCgCr** achieved the highest observed macro F1
  score of 0.9199.
- **RGB** recorded the lowest test loss
  (0.1967).

These metrics describe different aspects of performance.
The highest accuracy, highest macro F1, and lowest loss
should not be treated as interchangeable.

## 4. Validation Checkpoint Results

The best validation checkpoints were selected using
validation loss. The saved validation comparison is:

Color Space  Best Epoch  Validation Loss  Validation Accuracy (%)  Validation Macro F1  Total Epochs
        RGB          14         0.245251                91.304348             0.905909            19
      YCgCr          18         0.301672                84.057971             0.822539            23
        HSV          13         0.408852                79.710145             0.787037            18

## 5. Research Interpretation

Under the current experimental configuration, YCgCr
provided the strongest observed classification performance
in terms of test accuracy and macro F1.

RGB also performed competitively and recorded the lowest
test loss.

HSV achieved lower test performance than the other two
representations in this experiment.

These findings apply to this dataset, split, preprocessing
pipeline, and training configuration. They do not establish
that one color space is universally superior.

## 6. Limitations

- The test set contains only 70 images.
- Results are based on one grouped train-validation-test split.
- A single run does not establish statistical significance.
- External field validation under different illumination,
  occlusion, and background conditions is still required.
- Confidence intervals and repeated-seed experiments would
  provide stronger evidence of performance stability.

## 7. Final Conclusion

Among the three evaluated input representations,
MobileNetV2 with YCgCr achieved the highest observed
test accuracy (92.86%) and macro F1
(0.9199).

RGB recorded the lowest test loss (0.1967).

Therefore, YCgCr is the strongest candidate based on
the observed test accuracy and macro F1, while further
independent validation and repeated experiments are needed
before drawing broader conclusions.
