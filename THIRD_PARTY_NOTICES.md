# Third-party notices and VGG16 release exclusion

The public Zenodo v1.0.0 package intentionally excludes these exact trained H5 benchmark files:

| Archival filename | Benchmark role | Public Zenodo status | Project licence status |
|---|---|---|---|
| `models/vgg16/frozen.h5` | Frozen VGG16 benchmark | Not included | Outside the project's MIT and CC BY 4.0 licences |
| `models/vgg16/finetuned.h5` | Final fine-tuned VGG16 benchmark | Not included | Outside the project's MIT and CC BY 4.0 licences |
| `models/vgg16/finetuned_stage1_frozen.h5` | Intermediate stage-1 model | Not included | Outside the project's MIT and CC BY 4.0 licences |

The published VGG16 notebooks reproduce the benchmark workflow using Keras VGG16 with `weights="imagenet"`. These three models were initialized from Keras VGG16 pretrained ImageNet weights. Permission to redistribute the pretrained ImageNet-derived components has not been established clearly enough for public redistribution, so the exact trained H5 files are omitted from the public Zenodo v1.0.0 package. This statement does not assert that redistribution is prohibited and does not grant rights to third-party pretrained components.

Rerunning the notebooks can recreate the workflow, but new training is not guaranteed to produce bit-identical weights or predictions. The exclusion does not affect the reported manuscript metrics: they remain preserved in the released notebooks, results, and figures.

Project-authored VGG16 notebook code remains within the MIT code scope; its project-authored narrative, outputs, reports, and figures fall within the CC BY 4.0 content scope. Neither project licence applies to the excluded H5 files. Other dependencies retain their own licences; environment pins do not relicense those dependencies.

See the [Keras Applications documentation](https://keras.io/api/applications/) and [Keras VGG16 documentation](https://keras.io/api/applications/vgg/vgg_models/) for the workflow references. Do not infer pretrained-weight licensing solely from the Keras software licence or download availability.
