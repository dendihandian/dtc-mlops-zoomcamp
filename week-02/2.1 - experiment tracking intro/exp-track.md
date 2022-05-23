experiment tracking: process of keeping track of all *relevant information* from an *ML experiment*

- source code
- environment
- data
- model
- hyperparameters
- metrics

__________

why it's important?

- reproducibility
- organization
- optimization

__________

tracking experiments in spreadsheets?
why is not enough?
- error prone
- no standard format
- visibility & collaboration

___________

MLFlow
an opensource platform for the machine learning lifecycle
- Tracking
- Models
- Model Registry
- Projects

____________

Tracking experiments with MLFlow
The Mlflow tracking module allows you to organize your experiment into runs, and to keep track of:

- parameters
- metrics
- metadata
- artifacts
- models

____________

along with this information, mlflow automatically logs extra information about the run:
- source code
- version of the code (git commit)
- start and end time
- author