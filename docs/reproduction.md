# Portable publication execution

The 900 balanced cross-cell curves come from a second Candida albicans cell. AtomicJ ROI selection experimentally defined Nanodomain, Intermediate and Outside, with 300 curves per class. Later computational processing restored filename/class organization after anonymization/random renaming; restoration metadata did not define experimental class labels. Both balanced test archives represent the same cohort.

Launch Jupyter with its working directory at the GitHub publication root or a notebook subdirectory. The same notebooks support (1) github/ alongside zenodo/, (2) Zenodo github_snapshot/ with assets in its parent, or (3) downloaded data/ and models/ inside the GitHub root. A clear error is raised if the dataset assets are absent.

Dataset files use the approved candida_* names. Labels are read from the publication root's data/labels/cross_cell_label_mapping.csv. Blind and binary workflows join original archive images on filename. Labelled evaluations use reorganized_filename for the flat Test/ images and never combine them with by_class/ duplicates. Published cross-cell prediction CSV filenames retain reorganized identities; published blind prediction filenames retain original identities.

The three evaluation notebooks retain historical training code and outputs. To reproduce only the independent test, restart the kernel and run ONLY the last code cell, tagged evaluation-only. Earlier code cells are tagged retained-training and blocked unless RUN_RETAINED_TRAINING = True is explicitly set. The independent evaluation cell imports and configures everything it needs, loads the published H5, and contains no training or model-saving operation.

Training notebooks create fresh unique runs/<family>/<experiment>/run-*/ directories. New checkpoints are written there; published models are read-only inputs to standalone evaluation. Fresh results preserve historical experiment-prefixed filenames and are separated from the curated results/ and figures/ artifacts. No published result is overwritten. Existing notebook outputs describe the original runs, not an execution of these edited sources.

The binary optional evaluation selects 300 Nanodomain and 300 Outside rows from the full 900-row mapping, checks uniqueness and completeness, and pairs original filenames with the original archive. No binary independent test has been executed or added to the published results. The optional imbalanced label CSV is not supplied; existing aggregate-only behavior is retained.

Only the labelled ZIP README was corrected with approval; all image members and its internal mapping remain unchanged. The dataset manifest records its updated checksum. Copyright © 2026 The Authors. Project-authored executable code is released under MIT; project-authored datasets, metadata, documentation, figures, tables and custom CNN model artifacts are released under CC BY 4.0 where distributed. Third-party and pretrained components remain subject to the exclusions and notices in THIRD_PARTY_NOTICES.md. Zenodo version DOI, publication DOI and release date remain pending. The VGG16-derived H5 files are not included in public Zenodo v1.0.0; their upstream redistribution permission has not been established clearly enough for public redistribution. No notebook/model execution was performed during preparation.

## Create a separate publication environment

The specification targets Linux x86_64, including WSL2. It does not alter TFQ.
From the publication root (github/ or github_snapshot/):

```bash
conda env create -f environment/environment.yml
conda activate candida-afm-cnn
python -m pip check
```

Keep requirements-pinned.txt beside environment.yml: Conda's pip integration
resolves the requirements file relative to the environment-file directory.
requirements-pinned.txt is an exact-version reference for the observed scientific dependency set (69 packages), not a cryptographically locked environment. A fresh installation has not been attempted.
Only Python and pip are provisioned by Conda; the scientific stack uses pip pins.
TensorFlow Quantum is installed in TFQ but is not needed for this publication.

Optional notebook interface, using versions observed in TFQ:

```bash
python -m pip install ipykernel==6.29.4 jupyterlab==4.2.2
python -m jupyterlab
```

These are instructions for a future user; no installation was performed during
inspection. Keep the kernel in the publication root or a notebook subdirectory.
Select the final evaluation-only cell to avoid training, as described above.
Do not treat all-cell execution of a training notebook as an environment check.

A suitable host NVIDIA driver and WSL GPU support must already be available for
GPU use. NVIDIA runtime packages are pinned to the observed TFQ versions. Do not
substitute tensorflow[and-cuda], whose 2.15.0 extra pins differ from this observed
stack. System nvcc 12.5 is recorded for provenance, not required for loading the
prebuilt TensorFlow wheel. Model execution on a fresh environment has not been
verified. See hardware.md and environment/environment-reference.txt for the
separate build, installed runtime, compiler and driver-supported CUDA versions.

## Verify the downloaded release

From the Zenodo package root, verify file integrity before use:

```bash
sha256sum -c SHA256SUMS
```

SHA256 verifies release-file integrity; it does not make the package-version reference a cryptographic environment lock. There is no supplied exact wheel/Conda-artifact lock. The source environment is preserved, and all setup commands in this document are instructions for a future user.

## Relate reproduced outputs to the publication

Use docs/manuscript_results.csv to locate the saved reference result for each principal claim. Paths in that CSV are relative to the GitHub root or Zenodo github_snapshot/. New runs retain experiment-prefixed output filenames under runs/; compare them with the curated results/ tables using experiment identity and the correct original/reorganized filename convention. Timing depends on the runtime and hardware. Do not replace reference results merely because a fresh run differs.

Before release, add the Zenodo version DOI, publication DOI and release date when available. Upstream redistribution terms for the excluded VGG16-derived H5 files remain to be verified. Review figures and full-map spatial conventions, and decide whether to authorize a clean-environment reproduction check; that check has not been performed during staging.
