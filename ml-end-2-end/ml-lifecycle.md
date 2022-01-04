# ML Project Lifecycle

A Machine Learning project is typically split into two phases, experimentation & production.

**Experimentation:** An iterative process that attempts to demonstrate that ML is an effective solution to a problem.

This phase is my current focus - making the tooling and processes as templatable and adhering to development best practices. 

**Production:** The process of converting an ML experiment into a robust form, wrapped around supporting software towards delivering business value. 

At the time of writing, I will adapt the production phase to the needs of the consumer (product team etc) rather than forcing integration with platforms or adapting a fixed point of integration.

## Experimentation

### 1. Discovery

- Understand ROI Potential
- Understand existing business processes.
- Identify key client contacts.
- Confirm Avaliability of and access to data.
- Define clear problem statement.
- Research ML approaches to determine feasibility.

### 2. Project Setup

- Create repoistory & scaffold the folder structure.
    - Leverage Kedro or other tools to support this process.
- Environment setup
    - Docker
    - Dependency management (requirements.txt, Poetry etc.)
    - Helper commands - MAKE.

### 3. Data Acquistion

- Identify constraints on data compliance.
    - PII, GDPR etc.
- Identify data sources & access options.
- Initial review of a subset of the data.
- Create a data dictionary.
- Build data pipelines to acquire the initial dataset(s).
    - Queries, joins, scripts etc.
- Implement data versioning strategy.
    - DVC, Kedro, Sagemaker Lineage.
- Is human labelling needed?
    - SME knowledge required?
- Consider the use of a feature store
    - Sagemaker feature store (Offline in S3, or online in a low latency DB, or both.)


### 4. EDA

- Data ingestion to a notebook environment.
- Data cleaning/preprocessing
    - Missing values, outliers, data selection, normalisation etc.
- Data Analysis
    - Visualisation, correlation, distirbutions etc.
- Seasonality
- Does the training data reflect the expected real world data?
- Data Bias

### 5. Modelling

- Target variable definition
    - binning etc.
- Handling imbalanced data/target variables.
- Feature engineering and selection
- Dimensionality reduction
- Hyperparameter optimisation
- Threshold moving
- Probability calibration
- Auto ML
    - H20, Auto SkLearn.
- Data augmentation
    - Smote, dropping majority classes etc.
- Experiment Tracking
- Model Registry
- Model types
    - Ensemble, single model, cascading models, rules based alternative?
- Repoducability of Results.

### 6. Evaluation

- XAI
- Define a no skill model.
- Metric Selection (loss)
- Testing strategy
    - Cross validation
    - Train test split - season, account for groups.
- Confusion Matrix
- Compare to human/business process.
- Select V1 model.
- Data drift risk over time.

### 7. Solution Selection

- Consider NFR's
- Model persistence method.
    - ONNX vs joblib.
- Recall/Precision Trade off.
- Map solution to ROI impact estimation.
- Business acceptance.
- Early of implementation effort from ML perspective.
    - Automated training required?
- Independent Review.

## Production

### 8. Hardening

- Unit tests
- Solidify documentation
- Functional, clean code.
- Logging.

### 9. Deployment Plan

- Establish multi skilled team
- Design solution architecture
    - Batch vs realtime inference.  
    - Model management strategy
    - A/B testing required?
    - Human in the loop?
    - Who/what is impacted by introducing this solution?
- Formal estimation
- Cost of solution

### 10. Production Phase

- Observability
    - Datadog
- Data drift monitoring.
- ML solution optimisation.
- CI Processes - Model generation + code artifacts
- Code Packaging
    - Docker, Poetry, Lambda Zip.
- Infrastructure as code needs.
- Define SLA's
- Auto scaling
- Alerts

## Resources

Information supported by ML-Ops principles:
- https://ml-ops.org/content/state-of-mlops
- https://towardsdatascience.com/mlops-at-home-part1-4c60db29d4a2
- https://cloud.google.com/architecture/mlops-continuous-delivery-and-automation-pipelines-in-machine-learning