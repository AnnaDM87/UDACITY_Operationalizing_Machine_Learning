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
“Registered Datasets” in ML Studio shows "Bankmarketing" dataset available
![benchamrk](https://github.com/AnnaDM87/UDACITY_Operationalizing_Machine_Learning/blob/main/starter_files/screenshot/bankmarketing_dataset_renamed_as_bank_train.png?raw=true)

Best model screenshot
![bestmodel](https://github.com/AnnaDM87/UDACITY_Operationalizing_Machine_Learning/assets/22540529/107f9569-faa0-47c9-94c0-3f9569e557c1)
The experiment is shown as completed
![experiment_complete](https://github.com/AnnaDM87/UDACITY_Operationalizing_Machine_Learning/blob/main/starter_files/screenshot/automated_experiment_complted.png?raw=true)

### Deploy the model
* We deployed our trained Voting Ensemble model using Azure Container Instance (ACI), with authentication enabled.

Deploy model with authentication enabled
![deploymodel](https://github.com/AnnaDM87/UDACITY_Operationalizing_Machine_Learning/blob/main/starter_files/screenshot/deploy_model.png?raw=true)

 Endpoints ready
 ![endopoints](https://github.com/AnnaDM87/UDACITY_Operationalizing_Machine_Learning/blob/main/starter_files/screenshot/endpoints.png?raw=true)
### Enable logging
Enabling Application Insights and Logs could have been done at the time of deployment, but for this project we achieved it using Azure Python SDK.
  
  Logging is enabled by running the provided logs.py script
  ![logspy1](https://github.com/AnnaDM87/UDACITY_Operationalizing_Machine_Learning/blob/main/starter_files/screenshot/logspy_screenshot.png?raw=true)


  ![logspy2](https://github.com/AnnaDM87/UDACITY_Operationalizing_Machine_Learning/blob/main/starter_files/screenshot/logspy_screenshot2.png?raw=true)
  
  Endpoints section in Azure ML Studio, showing that “Application Insights enabled” says “true”.
 ![ensemble_true](https://github.com/AnnaDM87/UDACITY_Operationalizing_Machine_Learning/blob/main/starter_files/screenshot/auto_ml_ensemble_true.png?raw=true)
### Swagger Documentation
To consume our best AutoML model using Swagger, we first need to download the swagger.json file provided to us in the Endpoints section of Azure Machine Learning Studio.

Then we run the swagger.sh and serve.py files to be able to interact with the swagger instance running with the documentation for the HTTP API of the model.
Swagger runs on localhost showing the HTTP API methods and responses for the model
![swagger](https://github.com/AnnaDM87/UDACITY_Operationalizing_Machine_Learning/blob/main/starter_files/screensho2/automl_swagger.png?raw=true)
### Consume model endpoints
We provided the scoring_uri and key to endpoint.py script and running it. 

endpoint.py script runs against the API producing JSON output from the model.
![endpoint.py](https://github.com/AnnaDM87/UDACITY_Operationalizing_Machine_Learning/blob/main/starter_files/screensho2/swagger_json.png?raw=true)
### Benchmark
We run the file bencmark.sh to load tes our model
Apache Benchmark (ab) runs against the HTTP API using authentication keys to retrieve performance results. (optional)
![bench1](https://github.com/AnnaDM87/UDACITY_Operationalizing_Machine_Learning/blob/main/starter_files/screensho2/bench_mark1.png?raw=true)
![bench2](https://github.com/AnnaDM87/UDACITY_Operationalizing_Machine_Learning/blob/main/starter_files/screensho2/benchmark2.png?raw=true)
### Create and publish a pipeline
We used a jupyter notebook to create, consume and publish the best model for the same dataset we already used. 
The pipeline section of Azure ML studio, showing that the pipeline has been created
![pipeline](https://github.com/AnnaDM87/UDACITY_Operationalizing_Machine_Learning/blob/main/starter_files/screensho2/pipeline_creation.png?raw=true)
*ipeline status in notebook
![notebook](https://github.com/AnnaDM87/UDACITY_Operationalizing_Machine_Learning/blob/main/starter_files/screensho2/Immagine2.png?raw=true)
The Bankmarketing dataset with the AutoML module
![pipeline2](https://github.com/AnnaDM87/UDACITY_Operationalizing_Machine_Learning/blob/main/starter_files/screensho2/pipeline_endpoint_2.png?raw=true)
The “Published Pipeline overview”, showing a REST endpoint and a status of ACTIVE
![pipeline_active](https://github.com/AnnaDM87/UDACITY_Operationalizing_Machine_Learning/blob/main/starter_files/screensho2/pipeline_active.png?raw=true)

Rest endpoint with status active
![restednpoint](https://github.com/AnnaDM87/UDACITY_Operationalizing_Machine_Learning/blob/main/starter_files/screensho2/published_pipeline.png?raw=true)


## Screen Recording
I cannot record the voice screen cast. Following you can find the text description:
[00:00-00:04] From the home page in azure ml studio, I select the Automated ML. 
[00:05-00:07] Selecting it, the Automated ML page open. There are two experiments. One was aborted. I select the completed one.
[00:08-00:18] The job page opens and I cane all the details about it, also the best model and the accuracy metric value
[00:19-00:32] Now, I select the endpoints. When I can see the deployed model.The application isneghts were enabled.
[00:33:00:55] Now I select the Pipeline. Again I select a successful pipeline. Selecting the pipelin, I can see all the details about the pipeline itself.
[00:56-01:14] I go aback to Pipeline section and select the pipeline endopoints tab. In this section I can see the rest endpoin details about the pipeline.


