# ZIP README correction — approved and applied

The exact approved README is inside the staged labelled ZIP. Only that README changed; image members and internal mapping remained byte-identical. This file retains the earlier proposal below as a historical drafting record, not the authoritative replacement text.

# Earlier proposal

Archive: data/candida_cross_cell_test_balanced_labelled.zip
Member to replace: TestingAdrian_Labelled/README.txt

Replace only that README with:

Independent cross-cell test set — restored experimental class-file organization
=============================================================================

The 900 balanced cross-cell curves come from a second Candida albicans cell. AtomicJ ROI selection experimentally defined Nanodomain, Intermediate and Outside, with 300 curves per class. Later computational processing restored filename/class organization after anonymization/random renaming; restoration metadata did not define experimental class labels. Both balanced test archives represent the same cohort.

The original archive preserves anonymized filenames used by blind workflows.
This labelled archive preserves restored organization for sample-level evaluation.
Flat Test/ images and by_class/ images are duplicate representations of 900 curves.

Restored filename convention:
testing1-testing300       Nanodomain
testing301-testing600     Intermediate
testing601-testing900     Outside

The internal TestingAdrian_labels.csv preserves restored filenames, experimental
classes, original source filenames, and restoration measurements. Its filename
column uses restored numbering; source_filename uses original numbering.
The external publication cross_cell_label_mapping.csv uses filename for original
numbering and reorganized_filename for restored numbering.

The recovery_amplitude_px field and recovery-distribution figure document the
file-organization restoration procedure; they did not define experimental class labels.

No image, label association, mapping CSV, or figure change is proposed.
