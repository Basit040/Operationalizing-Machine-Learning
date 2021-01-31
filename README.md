

# Operationalizing Machine Learning

In this project we will use Bank Marketing Dataset of Portuguese banking institution. Primary task is classification and we have to predict if the client will subscribe a term deposit. Dataset consists of 20 features and 32,950 rows. Link for the dataset is https://automlsamplenotebookdata.blob.core.windows.net/automl-sample-notebook-data/bankmarketing_train.csv
We are using Azure to configure a cloud based machine learning production model, deploy it and consume it. Then we are creating, publishing and consume a pipeline. In this project we follow the following steps:
1.	Automated ML Experiment
2.	Deploy the best model
3.	Enable logging
4.	Swagger Documentation
5.	Consume model endpoints
6.	Create and publish a pipeline


## Architectural Diagram
<img src = "https://github.com/Basit040/Operationalizing-Machine-Learning/blob/main/snaps/Architectureflow.png"  />

First we have to select and upload the Bank marketing dataset. Then configure a new compute cluster, we used 1 as minimum number of nodes. After that we will create new automated ML run. We run the experiment using Classification and ensured that “Explain best model” is checked. Moreover on exit criterion we reduce the default (3 hours) to 01 and reduce the concurrency from default to 5. AutoML run process takes 15 to 30 minutes. After the experiment run completes, a summary of all the models and their metrics are shown, including explanations. The Best Model will be shown in the Details tab. We selected the best model for deployment and enable authentication. We deploy the model using Azure Container Instance (ACI). Deploying the Best Model will allow to interact with the HTTP API service and interact with the model by sending data over POST requests. Now that the Best Model is deployed, enable Application Insights and retrieve logs. We write ad run the code to enable application insights. Use the code logs.py to view the logs. Now we consume the deployed model using swagger. Download the swagger.json file. Run the swagger.sh and serve.py . Interact ith the swagger instance running with the documentation for the HTTP API of the model. Then display the contents of the API for the model. Model is then consumed using endpoint.py after modifying both the scoring_uri and the key.

## Key Steps
First we register the dataset
<img src = "https://github.com/Basit040/Operationalizing-Machine-Learning/blob/main/snaps/1-dataset-register.jpg"  />


Configure a compute cluster
<img src = "https://github.com/Basit040/Operationalizing-Machine-Learning/blob/main/snaps/2-cluster.jpg"  />


AutoML run takes 15 to 30 minutes to complete, status will be shown as “completed”
<img src = "https://github.com/Basit040/Operationalizing-Machine-Learning/blob/main/snaps/3-automl-completed.jpg"  />


Voting ensemble is the best model with accuracy of 0.92049
<img src = "https://github.com/Basit040/Operationalizing-Machine-Learning/blob/main/snaps/4-voting-ensemble.jpg"  />


Showing run of different models and their performance
<img src = "https://github.com/Basit040/Operationalizing-Machine-Learning/blob/main/snaps/5-diff-models.jpg"  />


Best model other metrics
<img src = "https://github.com/Basit040/Operationalizing-Machine-Learning/blob/main/snaps/6-best-metric1.jpg"  />
<img src = "https://github.com/Basit040/Operationalizing-Machine-Learning/blob/main/snaps/7-best-metric2.jpg"  />


Deploying the best model with authentication enabled
<img src = "https://github.com/Basit040/Operationalizing-Machine-Learning/blob/main/snaps/8-deploy-model.jpg"  />


logs.py with application insights true code
<img src = "https://github.com/Basit040/Operationalizing-Machine-Learning/blob/main/snaps/9-logspy.jpg"  />


Screenshots below shows output of logs.py
<img src = "https://github.com/Basit040/Operationalizing-Machine-Learning/blob/main/snaps/10-logpyrun1.jpg"  />
<img src = "https://github.com/Basit040/Operationalizing-Machine-Learning/blob/main/snaps/11-logpyrun2.jpg"  />


After we enable application insights using logs.py, status is set to True and a URL is also displayed to access insights for the deployed model (Voting Ensemble)
<img src = "https://github.com/Basit040/Operationalizing-Machine-Learning/blob/main/snaps/12-enabletrueandurl1.jpg"  />
<img src = "https://github.com/Basit040/Operationalizing-Machine-Learning/blob/main/snaps/13-enabletrueandurl2.jpg"  />


swagger.json' was downloaded from the Azure ML Studio. Swagger is used to interact with the HTTP REST API endpoint documentation. 'swagger.sh' will download the latest Swagger container, and it will run it on our specified port. 'serve.py' will start a Python server on port specified
<img src = "https://github.com/Basit040/Operationalizing-Machine-Learning/blob/main/snaps/14-swagger1.jpg"  />
<img src = "https://github.com/Basit040/Operationalizing-Machine-Learning/blob/main/snaps/15-swagger2.jpg"  />
<img src = "https://github.com/Basit040/Operationalizing-Machine-Learning/blob/main/snaps/16-swagger3.jpg"  />
<img src = "https://github.com/Basit040/Operationalizing-Machine-Learning/blob/main/snaps/17-swagger4.jpg"  />
<img src = "https://github.com/Basit040/Operationalizing-Machine-Learning/blob/main/snaps/18-swagger5.jpg"  />
<img src = "https://github.com/Basit040/Operationalizing-Machine-Learning/blob/main/snaps/19-swagger6.jpg"  />
<img src = "https://github.com/Basit040/Operationalizing-Machine-Learning/blob/main/snaps/20-swagger7.jpg"  />
<img src = "https://github.com/Basit040/Operationalizing-Machine-Learning/blob/main/snaps/21-swagger8.jpg"  />
<img src = "https://github.com/Basit040/Operationalizing-Machine-Learning/blob/main/snaps/22-swagger9.jpg"  />
<img src = "https://github.com/Basit040/Operationalizing-Machine-Learning/blob/main/snaps/23-swagger10.jpg"  />
<img src = "https://github.com/Basit040/Operationalizing-Machine-Learning/blob/main/snaps/24-swagger11.jpg"  />


After model is deployed, used the updated 'endpoint.py' script to interact with the trained model
<img src = "https://github.com/Basit040/Operationalizing-Machine-Learning/blob/main/snaps/25-endpoint1.jpg"  />
<img src = "https://github.com/Basit040/Operationalizing-Machine-Learning/blob/main/snaps/26-endpoint2.jpg"  />
<img src = "https://github.com/Basit040/Operationalizing-Machine-Learning/blob/main/snaps/27-endpoint3.jpg"  />
<img src = "https://github.com/Basit040/Operationalizing-Machine-Learning/blob/main/snaps/28-endpoint4.jpg"  />


Now we create a pipeline for the entire process. Use Jupyter Notebook aml-pipelines-with-automated-machine-learning-step.ipynb to create this pipeline
<img src = "https://github.com/Basit040/Operationalizing-Machine-Learning/blob/main/snaps/29-pipeline1.jpg"  />
<img src = "https://github.com/Basit040/Operationalizing-Machine-Learning/blob/main/snaps/30-pipeline2.jpg"  />
<img src = "https://github.com/Basit040/Operationalizing-Machine-Learning/blob/main/snaps/31-pipeline3.jpg"  />
<img src = "https://github.com/Basit040/Operationalizing-Machine-Learning/blob/main/snaps/32-pipeline4.jpg"  />


After the pipeline is published, we can use Published Pipeline Overview to see the status and REST endpoint of the pipeline.  
<img src = "https://github.com/Basit040/Operationalizing-Machine-Learning/blob/main/snaps/33-pipelinerest1.jpg"  />
<img src = "https://github.com/Basit040/Operationalizing-Machine-Learning/blob/main/snaps/34-pipelinerest2.jpg"  />
<img src = "https://github.com/Basit040/Operationalizing-Machine-Learning/blob/main/snaps/35-pipelinerest3.jpg"  />




## Screen Recording
*TODO* Provide a link to a screen recording of the project in action. Remember that the screencast should demonstrate:

## Standout Suggestions
*TODO (Optional):* This is where you can provide information about any standout suggestions that you have attempted.
