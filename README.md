# README

## Project: Hyperparameter Tuning for CNN and VGG16 using WandB

This project provides training pipelines for image classification using CNN and VGG16 architectures with hyperparameter tuning support via Weights & Biases (WandB).

### Files Included

- `TrainA.py`: Trains a custom CNN model with configurable architecture using WandB sweeps.
- `TrainB.py`: Fine-tunes a VGG16 model with configurable classifier layers, integrated with WandB.

### Requirements

Make sure to install the necessary packages:

```bash
pip install wandb torch torchvision
```

### Dataset Structure

The scripts expect the iNaturalist 12K dataset in the following structure:

```
/kaggle/input/inaturalist12k/inaturalist_12K/
├── train/
│   ├── class1/
│   ├── class2/
│   └── ...
└── val/
    ├── class1/
    ├── class2/
    └── ...
```

This can be overridden using `--data-path` and `--test-path` arguments.

---

## TrainA.py - Custom CNN

### Command Line Arguments

| Argument         | Description                                      | Default     |
|------------------|--------------------------------------------------|-------------|
| `--wandb_key`    | WandB API key (required)                         | None        |
| `--project`      | WandB project name                               | Assignment2 |
| `--entity`       | WandB team/entity name                           | cs23m004-indian-institute-of-technology-madras |
| `--data_dir`     | Path to dataset root (contains train/ and val/)  | /kaggle/input/inaturalist12k/inaturalist_12K |
| `--sweep_count`  | Number of sweep runs to execute                  | 1           |

### Example Usage

```bash
python TrainA.py \
  --wandb_key YOUR_API_KEY \
  --project Assignment2 \
  --entity your-entity-name \
  --data_dir /path/to/data \
  --sweep_count 5
```

---

## TrainB.py - VGG16 Fine-Tuning

### Command Line Arguments

| Argument          | Description                                      | Default     |
|-------------------|--------------------------------------------------|-------------|
| `--dev`           | Enable development mode for quick runs          | False       |
| `--sweep-count`   | Number of sweep runs to execute                  | 10          |
| `--data-path`     | Path to training data                            | /kaggle/input/inaturalist12k/inaturalist_12K/train |
| `--test-path`     | Path to validation data                          | /kaggle/input/inaturalist12k/inaturalist_12K/val   |
| `--wandb-key`     | WandB API key                                    | (Default key in script) |
| `--wandb-project` | WandB project name                               | Assignment2 |
| `--wandb-entity`  | WandB entity/team name                           | cs23m004-indian-institute-of-technology-madras |

### Example Usage

```bash
python TrainB.py \
  --dev \
  --sweep-count 5 \
  --wandb-key YOUR_API_KEY \
  --wandb-project Assignment2 \
  --wandb-entity your-entity-name
```

---

## Notes

- Training and validation metrics are logged automatically to your WandB dashboard.
- Each sweep run is uniquely named based on configuration.
- You can customize the model architecture or hyperparameter space by editing the respective config dictionary or model functions.

---

## Author

This project was developed by `cs23m004` from Indian Institute of Technology Madras.