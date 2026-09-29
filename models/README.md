# Trained models

Custom CNN H5 binaries are distributed in the Zenodo `models/` directory, not ordinary GitHub source history. [manifest.csv](manifest.csv) records original source paths, publication destinations, byte sizes, and SHA256 hashes for included models, as well as the VGG16 benchmark files omitted from public Zenodo v1.0.0.

| Family | Public Zenodo model paths |
|---|---|
| Balanced | `models/balanced/{baseline,l1,l2,l1_l2,dropout,augmentation,l2_dropout_augmentation}.h5` |
| Imbalanced | `models/imbalanced/{baseline,l2}.h5` |
| Binary | `models/binary/l2.h5` |
| VGG16 | No H5 files included in public Zenodo v1.0.0; benchmark workflow, results, and figures remain published. |

The public Zenodo package contains ten custom CNN H5 files. Multiclass output order is Intermediate, Nanodomain, Outside; binary order is Nanodomain, Outside. Custom CNN images are resized to 224 × 224 and rescaled by 1/255. VGG16 uses its `preprocess_input` transformation; do not substitute the CNN rescaling procedure.

The selected balanced L2 model is `models/balanced/l2.h5`. Independent evaluation reloads the published checkpoint; it does not train or save a model. Training notebooks write new checkpoints into unique run directories. Saved model metadata records Keras 2.15.0 with TensorFlow backend. Model loading was not re-tested during publication preparation.

Use the final evaluation-only cells as described in [reproduction.md](../docs/reproduction.md). The ten custom CNN H5s fall within the project CC BY 4.0 scope. Three exact VGG16-derived H5 benchmark files are intentionally omitted from public Zenodo v1.0.0 because redistribution permission for pretrained ImageNet-derived components has not been established clearly enough for public redistribution. The VGG16 notebooks, results, and figures remain included, and the notebooks reproduce the workflow using Keras VGG16 with `weights="imagenet"`; reruns are not guaranteed to be bit-identical. See [VGG16 model notes](vgg16/README.md) and [third-party notices](../THIRD_PARTY_NOTICES.md).
