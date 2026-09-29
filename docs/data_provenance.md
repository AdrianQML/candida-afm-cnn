# Experimental and file provenance

The independent balanced cross-cell test contains 900 force-distance curves acquired from a second Candida albicans cell, distinct from the cell used for training and validation. AtomicJ ROI selection experimentally defined Nanodomain, Intermediate and Outside, with 300 curves per class. The files were later anonymized/randomly renamed and their original class-folder organization was lost. Later computational processing restored the class-file organization. Restoration metadata did not define the experimental class labels.

## One independent balanced cohort, two archive representations

`candida_cross_cell_test_balanced_original.zip` preserves the anonymized names used by original blind workflows. `candida_cross_cell_test_balanced_labelled.zip` preserves restored class-file organization for sample-level evaluation. Both contain the same 900 curves. Flat and class-folder copies within the labelled archive are duplicate representations, not additional observations.

The publication mapping in `data/labels/cross_cell_label_mapping.csv` associates original `filename`, experimental `true_label`, and `reorganized_filename`. All 900 image associations were verified against the original archive during staging. The separate restoration metadata records the file-organization procedure, not the origin of experimental class labels.

The 855-curve imbalanced test is a subset of this independent cohort, with 290 Intermediate, 280 Nanodomain and 285 Outside images confirmed by image-content matching. It is not another independent cell. A dedicated imbalanced label CSV is not supplied to the current optional notebook branch; the published imbalanced test artifacts are blind predictions and aggregate comparisons, not sample-level test accuracy.

## Training, validation and full-map inference

Training and validation use subsets from the training cell; they are not independent-cell evaluations. Balanced splits contain 2,400 training and 600 validation images. Imbalanced splits contain 1,840 training and 460 validation images. Binary analysis uses only Nanodomain and Outside from the balanced source, split into 1,600 training and 400 validation images.

The full 128 × 128 map contains 16,384 curves from the same second cell. Full-map predictions are unlabelled operational inference; their class counts do not establish accuracy. Spatial scan orientation and curve-index-to-coordinate mapping still require confirmation. Raw instrument data and the complete raw-data-to-image workflow are not included in this image-classification package.

## Publication changes and traceability

Authoritative working artifacts were copied into staging. Notebook paths were made portable while preserving historical outputs. No notebook/model was executed. The approved change inside the labelled dataset ZIP replaced only TestingAdrian_Labelled/README.txt; all other members remained byte-identical. Dataset/model manifests and the Zenodo release manifest identify exact publication artifacts and checksums.

Restoration and analysis documentation now uses experimental AtomicJ ROI provenance consistently. Current environment observations are distinguished from historical run evidence; no broader biological generalization beyond the documented cells is asserted.
