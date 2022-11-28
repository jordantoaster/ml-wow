# MLFlow General Thoughts

## Planned Use of MLFlow

At the time of writing MLFlow will **not** be adopted for any part of default Machine Learning Project workflow, due to some of its constraints and benefits of using a managed service like Sagemaker.

## Pros

- Best in class user interface for experimet tracking.
- Flexible usage patterns are possible, ranging from the end to end ML lifecycle to simply experiment tracking.
- Easy to setup and use.
- Package API is clean and clear.
- Integration of MLFLow into Python code is organic and not obstrusive.

## Cons

- Running MLFlow server locally means you cannot persist the 'mlruns' metadata to S3. It it possible to manage this using AWS sync commands to S3, but it is not elegant and brings along risk of deleting data accidentally.
- Adoptog MLflow effectively involves having to manage the deployment of the MLFlow server application and a MYSql backend store. Even if you leverage boiler plate CloudFormation (or other) for this, it drastically increases the amount of moving pieces you need to manage.

## Resources

- https://github.com/jordantoaster/kedro-sagemaker-mlflow
