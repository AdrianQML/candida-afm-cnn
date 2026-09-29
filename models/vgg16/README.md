# VGG16 benchmark models

The published VGG16 notebooks reproduce the benchmark workflow using Keras VGG16 with `weights="imagenet"`. The corresponding benchmark outputs remain available in the notebooks, result tables, and figures.

The three exact trained H5 benchmark files are intentionally not included in the public Zenodo v1.0.0 package because redistribution permission for the pretrained ImageNet-derived components has not been established clearly enough for public redistribution. This exclusion does not affect the reported manuscript metrics, which remain preserved in the released notebooks, results, and figures.

| Archival filename | Scientific role |
|---|---|
| `frozen.h5` | Frozen VGG16 benchmark model. |
| `finetuned.h5` | Final fine-tuned VGG16 benchmark model. |
| `finetuned_stage1_frozen.h5` | Intermediate stage-1 model from the two-stage fine-tuning workflow, before block-5 fine-tuning. |

These models were initialized from Keras VGG16 pretrained ImageNet weights. Rerunning the published notebooks can recreate the workflow with `weights="imagenet"`, but new training is not guaranteed to produce bit-identical weights or predictions.

See the top-level [`THIRD_PARTY_NOTICES.md`](../../THIRD_PARTY_NOTICES.md). No rights to third-party pretrained components are granted here; upstream redistribution and use terms must be verified before public redistribution.
