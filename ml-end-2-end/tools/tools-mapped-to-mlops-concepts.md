# Mapping MLOps Concepts to Tooling

This document translates the [Machine Learning Lifecycle](../ml-lifecycle.md) into core ML-Ops concepts. This also reflects a best efforts attempt at connecting the concepts to tooling to represent what I use today in ML projects.

1. Environment Management
2. Project Scaffolding
3. Flexible Compute
4. Artifact Versioning
5. Experiment Tracking
6. Data/Model/Concept Drift Detection
7. Model Monitoring (Observability)
8. ML Pipelines
9. XAI and Bias

## #1 Environment Management

### Preferred Options 
- Docker for local development using a Python image, supported by a requirements.txt file.
    - This allows the use of local IDE for ease of debugging and offers greater development agility.

### Alternative Options
- Virtual environments.
- Anaconda.

## #2 Project Scaffolding

### Preferred Options
- Kedro, in its recommended usage pattern.
    - Example: ML Mumford Member auto matching project.

### Alternative Options
- Custom project structures.

## #3 Flexible Compute

### referred Options
- Sagemaker Notebooks - Studio or managed Notebook instance during the iterative experimentation phase.
    - If required, running Kedro inside Sagemaker Notebook using the terminal is also an accepted usage pattern as long as credentials are avaliable.
    - Sagemaker Studio based commits required a personal access token from GitHub.
- Sagemaker processing and training jobs for "off notebook" workloads.

### Alternate Options
- N/A

### Unknowns
- Is it possible to get training metrics from Sagemaker training jobs? Beyond simply logging in the training script?

## #4 Artifact Versioning

### Preferred Options
- Kedro versioning to cloud storage (S3)

### Alternate Options
- N/A
    - Sagemaker Feature Store?

## #5 Experiment Tracking

The ability to capture the results of an ML experiment **and** reproduce on demand.

### Preferred Options
- Sagemaker Experiment Tracking
    - Offers the ability to capture metrics from training jobs using Regex and capturing any desired metadata using the Sagemaker SDK. 

### Alternate Options
- N/A
    - DVC Pipelines

## #6 Model Monitoring (Observability)

### Preferred Options
- N/A

### Alternate Options
- N/A
    - Tracking changes in the features the model uses in Datadog or other monitoring tool.
    - Great Expectations?
        - Flexible for any solution with apprioriate alerting.
    - Sagemaker Endpoints
        - Only suitable for model deployed to an endpoint on Sagemaker.

## #7 ML Pipelines

A central pipeline for preparing data and training ML model in a single click/command/schedule. The output being a /datamodel or multiple data/model artifacts.

### Preferred Options
- Kedro

### Alternate Options
- DVC?
- Sagemaker Pipelines?

## #8 XAI and Bias

### Preferred Options
- SHAP + feature attribution from models.
    - As it stands, applied only during the experimention phase effectively. 

### Alternate Options
- Sagemaker Clarify?
- Lime

## Resources

- https://ml-ops.org/content/state-of-mlops

---
WIP Other possible topics:
- Automated retraining.
- Alerting - Pager Duty via Datadog Monitors?


