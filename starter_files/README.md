*NOTE:* This file is a template that you can use to create the README for your project. The *TODO* comments below will highlight the information you should be sure to include.


# Operationalizing Machine Learning
This project is part of the Udacity Azure ML Nanodegree. In this project, we use Azure to configure a cloud-based machine learning production model, deploy it, and consume it. We also create, publish, and consume a pipeline.

## Architectural Diagram

Authentication : In this step, we need to create a Security Principal (SP) to interact with the Azure Workspace.
Automated ML Experiment : In this step, we create an experiment using Automated ML, configure a compute cluster, and use that cluster to run the experiment.
Deploy the best model : Deploying the Best Model will allow us to interact with the HTTP API service and interact with the model by sending data over POST requests.
Enable logging : Logging helps monitor our deployed model. It helps us know the number of requests it gets, the time each request takes, etc.
Swagger Documentation : In this step, we consume the deployed model using Swagger.
Consume model endpoints : We interact with the endpoint using some test data to get inference.
Create and publish a pipeline : In this step, we automate this workflow by creating a pipeline with the Python SDK.

## Key Steps
### Authentication
I used the udacity virtual machine. I skipped this part because I am not allowed to use it.

### Automated ML Experiment
* I created an AutoML experiment by usinf the Bank Marketing dataset. I uploaded the dataset in the workspace and chose y as a column.
* As requested, I chose the Standard_DS12_V2 for the virtual machine, 1 minimum number of nodes.
* The experiment type was classification.
* The best model for this classification was Voting Ensemble.
![benchamrk](https://github.com/AnnaDM87/UDACITY_Operationalizing_Machine_Learning/blob/main/starter_files/screensho2/bankmarketing_dataset.png?raw=true)

## Screen Recording
*TODO* Provide a link to a screen recording of the project in action. Remember that the screencast should demonstrate:

## Standout Suggestions
*TODO (Optional):* This is where you can provide information about any standout suggestions that you have attempted.
