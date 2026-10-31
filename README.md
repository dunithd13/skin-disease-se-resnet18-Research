# Nine-Class Skin Disease Classification with SE-ResNet18

Research code for comparing targeted dataset balancing, Mixup, and
RandAugment in nine-class dermoscopic skin disease classification.

## Overview

This project investigates three experimental configurations using
a shared SE-ResNet18 backbone trained from scratch. The experiments
compare different data-balancing and augmentation strategies.

This repository contains the training notebooks, experimental
documentation, reported metrics, and visualization outputs.

## Experimental Configurations

| Model | Dataset | Training Augmentation |
|---|---|---|
| A — Baseline | Original imbalanced dataset | Standard augmentation + Mixup |
| B — Balanced | Dataset balanced using targeted augmentation | Standard augmentation |
| C — Proposed | Dataset balanced using targeted augmentation | Standard augmentation + RandAugment |

Models B and C do not use Mixup.

In the original reported experiments, the balanced dataset contained
1,000 images per class.

## Disease Classes

- Actinic Keratosis
- Basal Cell Carcinoma
- Dermatofibroma
- Melanoma
- Nevus
- Pigmented Benign Keratosis
- Seborrheic Keratosis
- Squamous Cell Carcinoma
- Vascular Lesion

This list is descriptive. The actual output-index mapping must be
obtained from the saved class mapping used by the trained model.

## Reported Results

The following values summarize the original reported experiments.
All values are percentages and describe validation performance,
not independent clinical-test performance.

| Model | Validation Accuracy | Precision | Recall | F1-Score | ROC-AUC |
|---|---:|---:|---:|---:|---:|
| A | 69.34 | 69.42 | 70.07 | 69.53 | 93.98 |
| B | 93.61 | 93.66 | 93.61 | 93.58 | 99.49 |
| C | 93.88 | 93.88 | 93.88 | 93.86 | 99.43 |

Before interpreting these results, see docs/experiment_protocol.md
for the data split, metric averaging, checkpoint selection, and
evaluation details.

Model C has the highest reported validation accuracy and F1-score.
Model B has the highest reported ROC-AUC.

These single-run differences do not establish statistical significance.

## Dataset

Dataset: Multiple Skin Disease Detection and Classification.

Source: [INSERT EXACT KAGGLE DATASET URL]
Version/access date: [INSERT DETAILS]
Dataset license: [INSERT VERIFIED LICENSE]

The dataset is not included in this repository.
Download it from the original source and follow data/README.md.

The repository's code license does not grant rights to the dataset.

## Installation

Create and activate a Python virtual environment, then run:

```bash
pip install -r requirements.txt
```

Tested Python, framework, CUDA, and dependency versions:
[INSERT VERIFIED ENVIRONMENT DETAILS]

## Running the Experiments

1. Download the dataset from the documented source.
2. Follow data/README.md to configure the local data paths.
3. Install the required dependencies.
4. Open the appropriate notebook in notebooks/.
5. Verify its configuration and run the cells in order.

Notebook configurations:

- 01_model_a_original_mixup.ipynb
- 02_model_b_targeted_balancing.ipynb
- 03_model_c_balancing_randaugment.ipynb

Training is computationally intensive. Hardware and runtime details
are documented in docs/experiment_protocol.md.

## Reproducibility

Record and preserve:

- Original dataset version and class counts
- Training, validation, and test split identifiers
- Random seeds
- Class-to-index mapping
- Augmentation settings
- Optimizer and scheduler parameters
- Checkpoint-selection rule
- Metric definitions and averaging methods
- Software and hardware environment

## Limitations

The experiments evaluate nine-class dermoscopic image classification.
They do not establish clinical diagnostic safety or generalization
to arbitrary smartphone photographs or unseen patient populations.

The original experimental protocol and any subsequent corrected
or extended experiments are documented separately.

