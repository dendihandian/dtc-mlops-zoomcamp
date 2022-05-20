mlops maturity model

https://docs.microsoft.com/en-us/azure/architecture/example-scenario/mlops/mlops-maturity-model

### mlops maturity level 1 - DevOps , no mlops
- releases are automated
- unit & integration tests
- CI/CD
- ops metrics

- no experiment tracking
- no reproducibility
- os separated from engineers

### mlops maturity level 2 - automated training

- training pipeline 
- experiment tracking
- model registry

- low friction deployment
- os work with engineers

### mlops maturity level 3 - automated deployment

- easy to deploy model
    - data prep
    - train model
    - deploy model
- a/b test to find better model (abtest not covered in the course)
- model monitoring

### mlops maturity level 4 - full mlops automation
- fully automated

The course may only focus on level 2-3