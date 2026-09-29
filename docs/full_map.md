# Full-map inference

The full AFM force map contains a 128 × 128 grid of force-distance (FD) curves, or 16,384 curves. Its publication archive is `data/candida_full_force_map_128x128.zip` (the same filename is recorded in `data/manifest.csv`). This archive is used for full-map inference; it is not a training or validation dataset. The staged data documentation identifies it as the complete map from the same independent second cell used for the labelled cross-cell test.

## Selected balanced L2 result

The selected balanced L2 CNN classified all 16,384 curves. The saved inference time is **6.8230 seconds**, with an average of **0.4164 ms per curve** and throughput of **2,401.3 curves per second**. The predicted counts were **3,765 Intermediate**, **8,180 Nanodomain**, and **4,439 Outside**. These counts sum to 16,384. The input map is unlabelled in this workflow, so the class counts are prediction totals, not accuracy or a validation/test score.

The authoritative compact records are [`results/balanced/l2/computational_performance.csv`](../results/balanced/l2/computational_performance.csv), [`results/balanced/l2/full_map_predictions.csv`](../results/balanced/l2/full_map_predictions.csv), and [`docs/manuscript_results.csv`](manuscript_results.csv). The saved timing is warm-up-adjusted and excludes model loading; timing depends on the execution environment. The prediction CSV records each image filename, predicted class, and class probabilities.

## Reproducing the workflow

Use [`notebooks/balanced/l2.ipynb`](../notebooks/balanced/l2.ipynb). Provide the Zenodo full-map archive at `data/candida_full_force_map_128x128.zip` and the selected balanced L2 checkpoint at `models/balanced/l2.h5`, following the [reproduction instructions](reproduction.md). In the notebook, establish/load the balanced L2 model as `best_model`, then run the full-map inference section. That section extracts the archive into the run workspace, checks for 16,384 supported image files, resizes images to 224 × 224, rescales pixel values to [0, 1], performs batched inference, and writes per-image predictions to a new run's results directory. It does not use the 900-curve labels to score the map.

The staged release does not explicitly preserve a verified scan orientation, physical coordinate mapping, pixel-to-position transformation, or acquisition-direction metadata for this inference output. The released predictions therefore support per-curve classification and class counts; they should not be interpreted as a spatially oriented map or used to infer physical coordinates.
