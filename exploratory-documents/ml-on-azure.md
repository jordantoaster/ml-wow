# Machine Learning Development on Azure

## Scope

The scope is limited to the **experimentation** phase of a Machine Learning project. The **production** phase is highly adaptive to the scenario of the project itself, where a fixed approach is often an unrealistic expectation, preferred direction can be assumed as a REST micro-service which can take several permutations (AKS, Function, App Service etc.)

Tooling scope is restricted to Databricks, MLFlow and Azure ML platform offerings. 

## ML on Azure Discussion

### Needs for (Experimentation) ML Development

- Access to flexible compute (from local to cluster)
- Notebook anaysis avaliable
- Code first approach - Clean code principles, IDE integration, PRs et al
- Replicable development environments (virtual envirment, docker et al)
- Experiment tracking
- Data storage, access and cataloging
- Pipeline orchestation
- Artifact versioning

### Rough Research Notes

- It seems you use MLFlow on Azure by pointing to the Azure ML workspace, which lives in the Azure ML platform rather than Databricks. 
- Can Databricks act as the notebook solution for scalable compute during analysis? 
- Azure ML seems to have shades of what MLFlow offers, though MLFlow is more conclusive and has exclusive experiment tracking as a preferred approach.
- If all databricks can do is retricted to notebooks, it should only be used for notebook development or if cluster is needed in exceptional cases to get the model, though a better CI process would be preferred. No manual steps. Scripting = better. 
- Hints seen that databricks run an mlflow instance? YES. 
- Databricks has a feature store. 
- You can deploy from MLFlow to Azure ML Platform deployment.

### Formal Outcomes & Recommendations

General observations...

|  Tool  | Flexible Compute | Notebook Analysis | Code First | Environment Replication  | Experiment Tracking |  Pipeline  |  Versioning  |  Data Storage  |
|---|---|---|---|---|---|---|---|---| 
| Databricks  | X (clusters)  | X  |   | X (pip + cluster config fixing)  | X (via MLFlow)  |   |   | X  |
| Local Dev  |  X (MLFlow Remote Jobs) | X  |  X |  X | X (send to MLFlow)  |   |   | X (can access blob)  |
| MLFlow  | X  |   | X (sdk)  | X | X  |   | X  |   |

Clearly lacking some pipelining and versioning strategy, MLflow offers for models, which in theory could be tethered to commit hash but not to data for reproduction - hand cranking needed in any case.

Can data factory or Azure ML help fill in the gaps? Maybe even Kedro?

Relying only on bricks has limits. Lack of unit testing, CI, PR for reviews etc. Lacks all modern development standards for good software if using a notebook only approach. 