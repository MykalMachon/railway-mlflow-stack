# MLflow Development Environment Example

This folder contains example code that shows how you can authenticate with your new MLflow instance deployed on Railway. The guide is basically just a suped up version of the [official MLflow tracking quickstart](https://mlflow.org/docs/latest/ml/tracking/quickstart/notebooks/tracking_quickstart/) that I made compatible with a remote/secure MLflow tracking server.

## Features

- Simple setup with `uv`
- Environment variable-based authentication
- Example ML experiment with scikit-learn
- Model registration and versioning

## Prerequisites

- Python 3.11+
- [uv](https://docs.astral.sh/uv/) (pip should work as well with some tweaking)
- A running MLflow deployment on Railway

## Setup

1. **Install dependencies**
	```bash
	uv sync
	```

2. **Configure environment variables**
	```bash
	cp .env.example .env
	```
	
	Edit `.env` with your MLflow server from the Caddy service in railway
	```env
	MLFLOW_TRACKING_URL=https://your-mlflow-caddy-server.up.railway.app
	MLFLOW_TRACKING_USERNAME=your-username
	MLFLOW_TRACKING_PASSWORD=your-password
	```

## Usage

### Quick Start

Run the example script to train a simple iris classification model and log it to MLflow:

```bash
uv run --env-file .env main.py
```

This will:

- Train a logistic regression model on the iris dataset
- Log parameters, metrics, and the trained model to MLflow
- Register the model in the MLflow model registry
- Load the model back and run predictions

## Extending this example

The `example_run.py` file contains the core MLflow integration logic but you can extend this general pattern out to track any of your ML work. As long as your authentication is working MLflow should work as documented.

## References

a few links to the docs I referenced while building this example out:

- [uv Python Package Manager](https://docs.astral.sh/uv/)
- [MLflow Documentation](https://mlflow.org/docs/latest/)
- [MLflow Tracking Quickstart](https://mlflow.org/docs/latest/ml/tracking/quickstart/notebooks/tracking_quickstart/)