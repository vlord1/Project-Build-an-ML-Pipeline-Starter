# NYC Airbnb Price Predictor Pipeline

This project implements an end-to-end automated machine learning pipeline to predict Airbnb rental prices in New York City. The pipeline is designed for reproducibility, utilizing MLflow for component orchestration, Hydra for hyperparameter management, and WandB for experiment tracking and artifact versioning.

## Project Overview

The pipeline follows a modular architecture, consisting of the following steps:

* **Download**: Fetches the raw dataset.
* **Basic Cleaning**: Filters price outliers ($10–$350) and enforces geolocation boundaries.
* **Data Check**: Validates the incoming data against reference distributions.
* **Data Split**: Stratifies and splits data into train, validation, and test sets.
* **Train Random Forest**: Trains a Regressor using NLP features from listing names.
* **Test Regression Model**: Evaluates the production-tagged model against a holdout test set.

## GitHub Repository

The link to the GitHub repository is as follows:
[https://github.com/vlord1/Project-Build-an-ML-Pipeline-Starter](https://github.com/vlord1/Project-Build-an-ML-Pipeline-Starter)  

## Weights & Biases Dashboard
You can track all experiment runs and artifact lineage here:
[https://wandb.ai/vlord1-western-governors-university/nyc_airbnb/overview/details](https://wandb.ai/vlord1-western-governors-university/nyc_airbnb/overview/details)

**Note on Visibility:** This project is hosted within an institutional W&B team workspace. Due to organization-level security policies, the "Public" visibility option is restricted. If you encounter any access issues, please let me know, and I will provide the necessary screenshots or report exports.

## Getting Started

To run this pipeline, ensure you have `mlflow`, `conda`, and `hydra` installed.

### Run the Pipeline

To execute the full pipeline using the latest release:

```bash
mlflow run https://github.com/vlord1/Project-Build-an-ML-Pipeline-Starter.git -v 1.0.1

```

### Run with New Data

To test the pipeline against a new dataset (e.g., `sample2.csv`):

```bash
mlflow run https://github.com/vlord1/Project-Build-an-ML-Pipeline-Starter.git \
  -v 1.0.1 \
  -P hydra_options="etl.sample='sample2.csv'"

```

## Best Model Configuration

The default hyperparameters in `config.yaml` are set to the winning configuration identified during hyperparameter optimization:

* **n_estimators**: 200
* **max_depth**: 50
* **Final Test MAE**: ~33.85

