# Kedro General Thoughts

## Overview

## Pros

- Enforces a project structure, which is one way to ensure consistency of development for a capability.
- Maintained by QuantumBlack (McKinsey) with active support.
- Proven as a delivery tool in a production grade model generation project (product matching)
- Can be modified to work well within a Docker container during local development. 
- Can be extended in a relatively easy manner (e.g. ONNX data type extension).
- Data catalog and its ease of integration with cloud storage is extremely effecient. 
- Possible to intregate Kedro with other tools like MLFlow and Sagemaker in the case where Kedros use is limited to acting as a data catalog and pipeline orchestrator. 

## Cons

- Moving Kedro jobs/nodes to scalable compute is not built in, but there exists options to shift into several services (e.g. AWS Batch).
- The learning curve for Kedro would be higher than other tooling in the MLOps space.
- Comes with signficant boilerplate in its template structure.
- As Kedro changes, the nature of the code generally changes quite a bit, to the extent its difficult to port Kedro code between versions of the tool. 
- Dependency management is a two step process, which led to writing my own custom abstraction for managing pip installs as part of project setup. 
- Kedro is not a platform solution, it cannot track experiments, metrics or offers a UI to explore artifacts and results like you would do in MLFlow. 