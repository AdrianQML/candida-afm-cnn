# Convolutional Neural Networks for Nanobiomechanical Classification of Atomic Force Microscopy Force-Distance Curves

This project evaluates convolutional neural networks for classifying images of atomic force microscopy force-distance curves from *Candida albicans*. The three experimental classes are **Nanodomain**, **Intermediate**, and **Outside**.

The release includes balanced CNN ablations (baseline, L1, L2, L1+L2, dropout, augmentation and L2+dropout+augmentation), imbalanced baseline/L2 experiments, a Nanodomain-versus-Outside binary L2 experiment, frozen and fine-tuned VGG16 benchmarks, independent cross-cell evaluations, and complete 128 × 128 force-map inference.

## Headline results

| Experiment | Saved result |
|---|---|
| Balanced L2 validation | 594/600; 99.00%; macro-F1 0.9900 |
| Imbalanced L2 validation | 457/460; 99.3478%; balanced accuracy 99.2917% |
| Independent balanced cross-cell L2 | 898/900; 99.7778%; macro-F1 0.997778 |
| Binary L2 validation | 400/400; 100% |
| VGG16 frozen independent | 875/900; 97.2222% |
| VGG16 fine-tuned independent | 889/900; 98.7778% |
| Full-map L2 inference | 16,384 curves in 6.8230 s; Intermediate 3,765, Nanodomain 8,180, Outside 4,439 |

These values come from saved authoritative artifacts, not new runs of the publication notebooks. [Manuscript result mapping](docs/manuscript_results.csv) identifies the exact source tables and metrics. [Experiments](docs/experiments.md) distinguishes validation, independent testing and unlabelled map inference. Full-map class counts are predictions, not accuracy measurements. L2 is the selected reported CNN; it did not have the highest balanced validation accuracy, and no unsupported selection rationale is asserted here.

## Repository and data release

```text
notebooks/     Final training and evaluation notebooks, with historical outputs
results/       Compact reports, predictions, histories and timing tables
figures/       Saved final figures
data/         Dataset manifest, provenance and authoritative filename mapping
models/        Model manifest and model-use documentation
environment/   Environment YAML, exact-version reference and observed environment
docs/          Experiment, reproduction, hardware and manuscript documentation
```

GitHub contains notebooks, documentation, compact results, figures and manifests. Dataset ZIPs and trained H5 files are supplied in the Zenodo package alongside a complete GitHub snapshot, release manifest and SHA256 checksums.

**Copyright © 2026 The Authors.**

Release version: v1.0.0. Repository: [https://github.com/AdrianQML/candida-afm-cnn](https://github.com/AdrianQML/candida-afm-cnn). Zenodo version DOI, publication DOI and release date remain pending.

## Quick start

Obtain the matching Zenodo package and retain its `github_snapshot/`, `data/` and `models/` layout. From `github_snapshot/` (or the GitHub root with the matching assets arranged as documented):

```bash
conda env create -f environment/environment.yml
conda activate candida-afm-cnn
python -m pip check
# Optional notebook interface; versions observed in the source environment:
python -m pip install ipykernel==6.29.4 jupyterlab==4.2.2
python -m jupyterlab
```

For independent L2 testing, open `notebooks/evaluation/balanced_l2_cross_cell.ipynb`, restart the kernel and run **only the final code cell tagged `evaluation-only`**. Use the analogous VGG16 evaluation notebooks for those benchmarks. Earlier retained training cells are disabled by default. Do not use Run All for evaluation-only reproduction. See [reproduction instructions](docs/reproduction.md) before training or inference.

## Reproducibility and provenance

The independent balanced cross-cell test contains 900 force-distance curves acquired from a second Candida albicans cell, distinct from the cell used for training and validation. AtomicJ ROI selection experimentally defined Nanodomain, Intermediate and Outside, with 300 curves per class. The files were later anonymized/randomly renamed and their original class-folder organization was lost. Later computational processing restored the class-file organization. Restoration metadata did not define the experimental class labels.

The original and labelled balanced test ZIPs contain the same 900 curves, not independent cohorts. Original filenames belong to blind workflows; restored filenames belong to labelled evaluations. [cross_cell_label_mapping.csv](data/labels/cross_cell_label_mapping.csv) preserves both identities. The imbalanced test is a subset of the same independent cohort. See [data provenance](docs/data_provenance.md).

Notebook outputs are preserved historical outputs. Portable notebook sources have not been executed during publication preparation; a clean environment installation and end-to-end reproduction remain unverified. New runs write to unique `runs/` directories, separate from published artifacts. Environment pins describe the observed scientific dependency set, not a cryptographically locked environment. Current hardware observations do not independently establish historical benchmark hardware.

## Citation and licensing

[CITATION.cff](CITATION.cff) records the confirmed author order, affiliations, available ORCIDs and corresponding-author emails. Zenodo version DOI, publication DOI and release date remain pending. Copyright © 2026 The Authors. Project-authored executable code is released under MIT. Project-authored datasets, metadata, documentation, figures, tables and custom CNN model artifacts are released under CC BY 4.0 where distributed. The three VGG16-derived H5 files are not included in public Zenodo v1.0.0; the VGG16 notebooks, benchmark results, figures and documentation remain included. Those notebooks use Keras VGG16 with `weights="imagenet"`. Exact H5 redistribution was intentionally omitted because upstream redistribution permission for ImageNet-derived pretrained components was not established clearly enough. Third-party and pretrained components remain subject to the exclusions and notices in [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md).
