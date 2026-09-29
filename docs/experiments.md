# Experiment inventory

The release retains 15 notebooks and 13 model files. Paths below are relative to the GitHub root; H5 files reside in the matching Zenodo package. Exact principal-result evidence is in [manuscript_results.csv](manuscript_results.csv).

| Experiment | Notebook | Results directory |
|---|---|---|
| Balanced baseline | `notebooks/balanced/baseline.ipynb` | `results/balanced/baseline/` |
| Balanced L1 | `notebooks/balanced/l1.ipynb` | `results/balanced/l1/` |
| Balanced L2 | `notebooks/balanced/l2.ipynb` | `results/balanced/l2/` |
| Balanced L1+L2 | `notebooks/balanced/l1_l2.ipynb` | `results/balanced/l1_l2/` |
| Balanced dropout | `notebooks/balanced/dropout.ipynb` | `results/balanced/dropout/` |
| Balanced augmentation | `notebooks/balanced/augmentation.ipynb` | `results/balanced/augmentation/` |
| Balanced L2+dropout+augmentation | `notebooks/balanced/l2_dropout_augmentation.ipynb` | `results/balanced/l2_dropout_augmentation/` |
| Imbalanced baseline | `notebooks/imbalanced/baseline.ipynb` | `results/imbalanced/baseline/` |
| Imbalanced L2 | `notebooks/imbalanced/l2.ipynb` | `results/imbalanced/l2/` |
| Binary L2 | `notebooks/binary/l2.ipynb` | `results/binary/l2/` |
| VGG16 frozen | `notebooks/vgg16/frozen.ipynb` | `results/vgg16/frozen/` |
| VGG16 fine-tuned | `notebooks/vgg16/finetuned.ipynb` | `results/vgg16/finetuned/` |
| Independent L2 | `notebooks/evaluation/balanced_l2_cross_cell.ipynb` | `results/balanced/l2/cross_cell/` |
| Independent VGG16 frozen | `notebooks/evaluation/vgg16_frozen_cross_cell.ipynb` | `results/vgg16/frozen/cross_cell/` |
| Independent VGG16 fine-tuned | `notebooks/evaluation/vgg16_finetuned_cross_cell.ipynb` | `results/vgg16/finetuned/cross_cell/` |

## Saved principal results

| Experiment | Saved result |
|---|---|
| Balanced L2 validation | 594/600; 99.00%; macro-F1 0.9900 |
| Imbalanced L2 validation | 457/460; 99.3478%; balanced accuracy 99.2917% |
| Independent balanced cross-cell L2 | 898/900; 99.7778%; macro-F1 0.997778 |
| Binary L2 validation | 400/400; 100% |
| VGG16 frozen independent | 875/900; 97.2222% |
| VGG16 fine-tuned independent | 889/900; 98.7778% |
| Full-map L2 inference | 16,384 curves in 6.8230 s; Intermediate 3,765, Nanodomain 8,180, Outside 4,439 |

Validation values refer to saved model evaluations on within-cell hold-outs. The balanced 600-image split contains 200 per class; the imbalanced 460-image split contains Intermediate 160, Nanodomain 200 and Outside 100. Binary validation contains 200 per retained class. No saved binary independent-test result is claimed.

CNN ablations retain the same architecture and use seed 42, 224 × 224 images, batch size 32, up to 50 epochs, Adam learning rate 0.0001, and minimum-validation-loss checkpoint selection. L1/L2 factors are 0.001 when enabled; dropout rates are 0.25 convolutional and 0.5 dense. Augmentation uses horizontal flipping, rotation factor 0.1 and zoom factor 0.2. See each notebook for implementation.

Frozen VGG16 trains its classifier head with the base frozen. Fine-tuning has 20 stage-1 epochs and 30 stage-2 epochs, unfreezing block 5 in stage 2; stage learning rates are 0.001 and 0.00001. The stage-1 H5 and both stage histories are retained. VGG16 uses its own ImageNet preprocessing.

The independent test contains the same 900 experimentally labelled curves across the L2 and VGG16 comparisons. Full-map timing is a saved warm-up-adjusted inference measurement excluding model loading, not a new benchmark. Full-map inference uses the same independent cell, not an additional biological replicate. The selected L2 designation is retained without asserting it was the highest-validation-accuracy ablation.
