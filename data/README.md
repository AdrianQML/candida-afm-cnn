# Datasets and filename mapping

The independent balanced cross-cell test contains 900 force-distance curves acquired from a second Candida albicans cell, distinct from the cell used for training and validation. AtomicJ ROI selection experimentally defined Nanodomain, Intermediate and Outside, with 300 curves per class. The files were later anonymized/randomly renamed and their original class-folder organization was lost. Later computational processing restored the class-file organization. Restoration metadata did not define the experimental class labels.

| Zenodo dataset filename | Contents and role |
|---|---|
| `candida_balanced_dataset.zip` | 3,000 images, 1,000 per class; source of balanced training/validation and binary subset |
| `candida_imbalanced_dataset.zip` | 2,300 images: Intermediate 800, Nanodomain 1,000, Outside 500 |
| `candida_cross_cell_test_balanced_original.zip` | 900 curves with original anonymized filenames; blind workflows |
| `candida_cross_cell_test_balanced_labelled.zip` | Same 900 curves with restored filenames/class organization; labelled evaluation |
| `candida_cross_cell_test_imbalanced.zip` | 855 curves: Intermediate 290, Nanodomain 280, Outside 285; subset of the balanced cross-cell cohort |
| `candida_full_force_map_128x128.zip` | 16,384 curve images from the complete map of the same independent cell |

Both training datasets include images subsequently split into training and validation subsets. These are image-based classification datasets, not raw instrument force-distance files.

[manifest.csv](manifest.csv) records sizes and SHA256 values. Its `zenodo/data/` destinations mean `data/` inside the downloaded Zenodo package. The two balanced test archives are representations of one cohort. Flat Test/ and by_class/ copies inside the labelled archive must not be counted as additional curves.

[labels/cross_cell_label_mapping.csv](labels/cross_cell_label_mapping.csv) is the authoritative publication mapping:

- `filename`: original anonymized archive identity.
- `true_label`: experimental AtomicJ ROI class.
- `reorganized_filename`: restored labelled-archive identity.

[labels/cross_cell_restoration_metadata.csv](labels/cross_cell_restoration_metadata.csv) preserves restoration-only measurements. These measurements did not define experimental class labels. Published cross-cell prediction tables use reorganized filenames; blind tables use original filenames.

Only the labelled archive README was corrected during staging, with approval. Its images and internal mapping remained unchanged. Its internal CSV uses filename for restored identity and source_filename for original identity; do not confuse those conventions with the publication mapping. The corrected archive hash is recorded in the manifest.

See [data_provenance.md](../docs/data_provenance.md). Project-owned datasets and mappings fall within the CC BY 4.0 scope in [LICENSE](../LICENSE); attribution details remain to be completed. The VGG16 H5 exclusion is documented separately and does not relicense upstream material.
