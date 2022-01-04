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

### Alternative Options
- Virtual environments.
- Anaconda

## #2 Project Scaffolding

### Preferred Options
- Kedro, in its recommended usage pattern.
    - Example: Product auto matching project.

### Alternative Options
- Custom project structures.

## #3 Flexible Compute

### referred Options
- Sagemaker Notebooks - Studio or managed Notebook instance during the iterate experimentation phase.
- Sagemaker processing and training jobs for "off notebook" workloads.
    - GPU
    - Cases of long wait times that slow development agility.

### Alternate Options
- N/A

### Unknowns
- Is it possible to get training metrics from Sagemaker training jobs? Beyond simply logging in the training script?

## #4 Artifact Versioning

### Preferred Options
- Kedro versioning to cloud storage.
    - AWS credentials give flexible regardless of development environment.

### Alternate Options
- N/A
    - Possibly MLFlow? (Pending)
    - Sagemaker Feature Store?

## #5 Experiment Tracking

The ability to capture the results of an ML experiment **and** reproduce on demand.

### Preferred Options
- N/A

### Alternate Options
- N/A
    - MLFlow
    - DVC Pipelines
    - Sagemaker Experiments?
        - Limited to use when used as part of Sagemaker training jobs.

## #6 Data/Model/Concept Drift Detection

### Preferred Options
- N/A

### Alternate Options
- N/A
    - Great Expectations?
        - Flexible for any solution with apprioriate alerting.
    - Sagemaker Endpoints
        - Only suitable for model deployed to an endpoint on Sagemaker.

## #7 Model Monitoring (Observability)

### Preferred Options
- N/A

### Alternate Options
- N/A
    - Custom Datadog dashboards

## #8 ML Pipelines

A central pipeline for preparing data and training ML model in a single click/command/schedule. The output being a model or multiple model artifacts.

### Preferred Options
- N/A

### Alternate Options
- DVC?
- Sagemaker Pipelines?

## #9 XAI and Bias

### Preferred Options
- SHAP + feature attribution from models.

### Alternate Options
- Sagemaker Clarify?
- Lime

## Resources

- https://ml-ops.org/content/state-of-mlops

---
WIP Other possible topics:
- Automated retraining.
- Alerting


