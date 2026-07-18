# CNN Baseline — WSI Patch Classification

Standard CNN baseline (ResNet34 / ConvNeXt via `timm`) for patch-level whole-slide-image classification, used as the reference point against the KAT and VIB baselines in the MSI/MSS colorectal cancer classification pipeline.

## Structure

- `source.py` — ResNet34 training loop over labeled WSI patches
- `convnext.py` — ConvNeXt (via `timm`) variant of the same training loop
- `preprocess.py` — patch/label preparation from raw slide metadata
- `splits_creation.py` — train/val/test split generation
- `baseline.ipynb` — end-to-end run and evaluation walkthrough

## Data

Expects a patch-level dataset with a `train.csv` / label CSV mapping each patch to its slide and target class. `dataset.csv`, `patches_with_label.csv`, and `selected_data.csv` hold the cohort used for this run; `zenodo_patches_names.csv` maps in patches sourced from Zenodo.

## Running

```bash
python source.py      # ResNet34 baseline
python convnext.py    # ConvNeXt baseline
```

Both scripts read patch data from a configured `train_dir`/`train_lib` path and write metrics and checkpoints to an `Output/<project>` directory, where `project` selects the classification target (mutation/biomarker label) being trained.
