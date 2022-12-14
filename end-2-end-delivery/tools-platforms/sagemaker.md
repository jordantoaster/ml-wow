# Sagemaker General Thoughts

## Potential Use of Sagemaker

### Experimentation

- Leverage [local mode](https://aws.amazon.com/blogs/machine-learning/use-the-amazon-sagemaker-local-mode-to-train-on-your-notebook-instance/) for the development cycle if required.

- Use the Studio notebooks if flexible compute is needed, following the same setup/development standards as I would locally in the terminal.

- Take advantage of preprocessing and training jobs for cases where they are required.

- Use Sagemaker for experiment tracking. Covering parameters, metrics and beyond as required,
    - See [here](https://github.com/jordantoaster/kedro-sagemaker) which contains an example of using the SDK for managing experiment metadata.

### Production

It is possible to deploy a model to Sagemaker, taking advantage of its capability for bias and drift detection. At the time of writing all deployments are handled on a case by case basis rather than fixed to a given platform.

## Pros	

- Flexible selection & orchestration of compute.
- An Ever evolving platform.
- "Local mode" offers flexibility outside of the Sagemaker platform, to leverage tools like VS Code for faster develomeny cycles.
- Certain functionality like training jobs are quite simple to use.
- Jump start material could be valuable in some circumstances.
- Can be used alongside open source tools where there are gaps or SM functionality is overly cumbersome.
- Most things in Sagemaker can be powered by custom Docker images if needed.
- LOTS of functionality offered.
- Experiment tracking tooling is quite elegant and easy to use via the SDK.

## Cons

- Several ways of doing the same thing, which causes confusion across examples and documentation.
- Sagemaker + Sagemaker Studio duplicate what they show to the user, e.g. endpoints can be managed in two places.
- Studio's value increases the more you adopt the platform for the complete ML lifecycle but introduces difficulty when leveraging a patchwork of functionality.
- The intutitiveness of the API for the Sagemaker SDK is lacking.
- .gitignore file is hidden in the Sagemaker Studio UI.
- How SM fits into infrastructure as code is unclear and will add severe complexity for teams trying to adopt who do not have large ML capabilities.
- Documentation can be inconsistent, hard to follow and overly complex.
- "Mastering" SM is a long term process and the process is akin to vendor lock in type knowledge as it does a lot of things in its own specific way, which could be dangerous to general skills development.
- Uncertainty on how SM can fit into a CI/CD workflow.
- SM Studio git integration seems to require the use of personal access tokens (in place of a password) for version control push commands, which is a sub par experience.
- When working different product teams, introducing an entirely new platform to manage is unfeasible over using typical AWS components - e.g. API on EC2 > SM endpoint.

## Reference Resources

- https://github.com/jordantoaster/sagemaker-exemplar
- https://github.com/jordantoaster/kedro-sagemaker
