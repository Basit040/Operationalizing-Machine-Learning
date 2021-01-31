

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

First we have to select and upload the Bank marketing dataset. Then configure a new compute cluster, we used 1 as minimum number of nodes. After that we will create new automated ML run. We run the experiment using Classification and ensured that “Explain best model” is checked. Moreover on exit criterion we reduce the default (3 hours) to 01 and reduce the concurrency from default to 5. AutoML run process takes 15 to 30 minutes. After the experiment run completes, a summary of all the models and their metrics are shown, including explanations. The Best Model will be shown in the Details tab. We selected the best model for deployment and enable authentication. We deploy the model using Azure Container Instance (ACI). Deploying the Best Model will allow to interact with the HTTP API service and interact with the model by sending data over POST requests. Now that the Best Model is deployed, enable Application Insights and retrieve logs. We write ad run the code to enable application insights. Use the code logs.py to view the logs. Now we consume the deployed model using swagger. Download the swagger.json file. Run the swagger.sh and serve.py . Interact ith the swagger instance running with the documentation for the HTTP API of the model. Then display the contents of the API for the model. Model is then consumed using endpoint.py after modifying both the scoring_uri and the key.

## Key Steps
*TODO*: Write a short discription of the key steps. Remeber to include all the screencasts required to demonstrate key steps. 

*TODO* Remeber to provide screenshots of the `RunDetails` widget as well as a screenshot of the best model trained with it's parameters.

## Screen Recording
*TODO* Provide a link to a screen recording of the project in action. Remember that the screencast should demonstrate:

## Standout Suggestions
*TODO (Optional):* This is where you can provide information about any standout suggestions that you have attempted.
