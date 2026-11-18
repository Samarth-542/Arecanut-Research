# DenseNet121 — Experimental Results and Research Conclusion

## 1. Experimental Objective

The objective of this experiment was to evaluate DenseNet121 for
binary arecanut ripeness classification using three input color
representations:

- RGB
- HSV
- Custom YCgCr representation

The same dataset partitions and model-training configuration were
used across the three experiments to support a controlled comparison.

## 2. Dataset and Experimental Configuration

| Parameter | Configuration |
|---|---|
| Model | DenseNet121 |
| Pretrained weights | ImageNet |
| Image size | 224 × 224 |
| Batch size | 16 |
| Optimizer | AdamW |
| Weight decay | 0.0001 |
| Phase 1 learning rate | 0.001 |
| Phase 2 learning rate | 0.0001 |
| Maximum Phase 1 epochs | 10 |
| Maximum Phase 2 epochs | 40 |
| Early stopping patience | 5 |
| Random seed | 42 |
| Number of classes | 2 |

### Dataset partition

| Partition | Ripe | Unripe | Total |
|---|---:|---:|---:|
| Training | 204 | 354 | 558 |
| Validation | 25 | 44 | 69 |
| Testing | 26 | 44 | 70 |
| Total | 255 | 442 | 697 |

The final grouped dataset contains 697 retained images after the
duplicate and label-conflict audit.

## 3. Best Validation Checkpoints

The checkpoint for each color space was selected using minimum
validation loss.

```text
Color Space  Best Epoch Best Phase  Validation Loss  Validation Accuracy  Validation Macro F1
        RGB          14    Phase 2           0.2176               0.8986               0.8871
        HSV          16    Phase 2           0.2263               0.9420               0.9348
      YCgCr          18    Phase 2           0.1987               0.9275               0.9222
```

The selected checkpoints were:

- RGB: Phase 2, overall epoch 14.
- HSV: Phase 2, overall epoch 16.
- YCgCr: Phase 2, overall epoch 18.

## 4. Final Test Results

The selected checkpoints were evaluated on the held-out test set
containing 70 images.

```text
Color Space  Test Samples  Test Loss  Accuracy  Macro Precision  Macro Recall  Macro F1  Balanced Accuracy
        RGB            70     0.2410    0.9000           0.9314        0.8654    0.8854             0.8654
        HSV            70     0.4862    0.7857           0.7869        0.7430    0.7544             0.7430
      YCgCr            70     0.2782    0.9000           0.8956        0.8890    0.8920             0.8890
```

### Best observed test metrics

- Highest test accuracy: RGB
  (90.00%).
- Highest macro F1: YCgCr
  (0.8920).
- Highest balanced accuracy: YCgCr
  (0.8890).
- Lowest test loss: RGB
  (0.2410).

## 5. Comparative Interpretation

RGB and YCgCr both achieved 90.00% test accuracy, while HSV
achieved 78.57%.

Although RGB and YCgCr had identical accuracy, their other
metrics differed. YCgCr achieved the highest macro F1 and
balanced accuracy, indicating a stronger balance between the
two classes in this test evaluation.

RGB achieved the highest macro precision and the lowest test
loss. HSV showed comparatively lower performance across the
reported test metrics.

These findings suggest that the choice of color representation
can influence DenseNet121 classification performance on this
dataset. However, the results do not establish that one color
space will perform best across other datasets or field conditions.

## 6. Training Behavior

Training and validation curves were generated for all three
color spaces.

The training histories show that training performance generally
improved during fine-tuning. Validation performance fluctuated
across epochs, reinforcing the importance of selecting
checkpoints using validation loss rather than simply using the
last training epoch.

The saved training-history graphs should be consulted when
discussing convergence and possible overfitting.

## 7. Research Limitations

The following limitations should be acknowledged:

1. The held-out test set contains only 70 images.
2. The comparison uses one grouped train-validation-test split
   with seed 42.
3. Repeated-seed experiments and statistical significance tests
   have not been established by these results.
4. External validation under different farms, lighting conditions,
   camera devices, and backgrounds has not been demonstrated.
5. The results concern binary image-level classification of
   Ripe and Unripe samples; they do not quantify the maturity
   percentage of individual nuts in a bunch.
6. The experiments compare color representations using
   DenseNet121; they do not establish the performance of
   segmentation or image-fusion methods.

## 8. Conclusion

DenseNet121 was evaluated using RGB, HSV, and custom YCgCr
representations for binary arecanut ripeness classification.

RGB and YCgCr achieved the highest observed test accuracy
of 90.00%. Among these results, YCgCr achieved the highest
macro F1 score of 0.8920 and balanced
accuracy of 0.8890, whereas
RGB achieved the lowest test loss of 0.2410.

HSV achieved a test accuracy of 78.57%.

Overall, YCgCr provided the strongest observed balance between
the two classes for DenseNet121, while RGB also demonstrated
competitive classification performance.

These findings are specific to the current dataset and
experimental split. Further evaluation using repeated
stratified group splits and independent field data is required
before drawing broader conclusions about generalization.

## 9. Generated Graphs

The following visualizations are stored in the graphs directory:

- Individual training-history graphs for RGB, HSV, and YCgCr.
- Combined validation comparison.
- Final test-performance comparison.
- Individual confusion matrices.
- Combined confusion-matrix comparison.
- Validation checkpoint comparison.