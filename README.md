# Neighbourly Advertisements Platform, Azure Serverless Microservice Deployment

## Table of Contents

- [Summary](#Summary)

- [Technologies](#Technologies)

- [Sample Data](#Sample-Data)

- [Structure](#Structure)

- [Configuration](#Configuration)

- [Deployment](#Deployment)

## Summary

This Craiglist clone was configured and deployed to Azure as part of my **Cloud Developer using Microsoft Azure Nanodegree from Udacity**.

**It demonstrates my understanding and ability to configure the following :**

#### Azure services

Azure Functions
Azure Event Hub
Azure Logic Apps
Azure Kubernetes
Azure App Service
Azure Container Registry
Azure Cosmos DB - MongoDB

#### Containerization

Build Docker image.  
Kubernetes service scaling.  
Pushing Docker images to a registry.  
Create and deploy a Kubernetes cluster.

#### Microservice Configuration

Configure and deploy a microservices project into serverless functions (Azure Functions)

#### Deployment

Deploy a client side as a web app (Azure App Service)

## Technologies

Flask was used for the client side.  
Docker was used for containerization.  
Flask-Bootstrap was used for the frontend.  
Python was used as the language of choice.  
Azure Functions was used for the serverless deployment.
Azure Kubernetes was used for container orchestration.  
Azure Container Registry Hub was used as the image registry.  
Kubectl was used as the Kubernetes command-line tool of choice.

## Sample Data

Two MongoDB collections are available at /SampleData

## Structure

```
+---NeighborlyAPI
|   |   Dockerfile
|   |   host.json
|   |   proxies.json
|   |   requirements.txt
|   |
|   +---createAdvertisement
|   |       function.json
|   |       sample.dat
|   |       __init__.py
|   |
|   +---deleteAdvertisement
|   |       function.json
|   |       sample.dat
|   |       __init__.py
|   |
|   +---eventHubTrigger
|   |       function.json
|   |       __init__.py
|   |
|   +---getAdvertisement
|   |       function.json
|   |       host.json
|   |       __init__.py
|   |
|   +---getAdvertisements
|   |       function.json
|   |       sample.dat
|   |       __init__.py
|   |
|   +---getPost
|   |       function.json
|   |       __init__.py
|   |
|   +---getPosts
|   |       function.json
|   |       sample.dat
|   |       __init__.py
|   |
|   \---updateAdvertisement
|           function.json
|           sample.dat
|           __init__.py
|
+---NeighborlyFrontEnd
|   |   app.py
|   |   requirements.txt
|   |   settings.py
|   |   __init__.py
|   |
|   +---static
|   |   \---css
|   |           main.css
|   |
|   +---templates
|   |       base.html
|   |       delete_ad.html
|   |       edit_ad.html
|   |       index.html
|   |       new_ad.html
|   |       view_ad.html
|   |
|   \---tests
|           conftest.py
|           __init__.py
|
\---SampleData
        sampleAds.json
        samplePosts.json
```

## Configuration

You will have to configure/use the following services

1. Azure Functions
2. Azure Event Hub
3. Azure Logic Apps
4. Azure Kubernetes
5. Azure App Service
6. Azure Container Registry
7. Azure Cosmos DB - MongoDB

Making the following changes to the files located at /NeighborlyAPI :  
Replace

```python
url = "ENTER DB CONNECTION STRING HERE"
```

With your Azure MongoDB connection string

```
database = client['ENTER DB NAME HERE']
```

With your Azure MongoDB database name

## Deployment

Install the following

- [Azure CLI](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli?view=azure-cli-latest)
- [Azure Function tools V3](https://docs.microsoft.com/en-us/azure/azure-functions/functions-run-local?tabs=windows%2Ccsharp%2Cbash#install-the-azure-functions-core-tools)
- [Azure Tools for Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=ms-vscode.vscode-node-azure-pack)

### 1. Backend

Deploy the functions to Azure functions using the Azure VS extension.

Check the output for the live links which you can test using postman.

### 2. Frontend

Use the following command to deploy your frontend to Azure App Service

```shell
az webapp up --sku F1 -n <APP_NAME> --resource-group <RESOURCE_GROUP_NAME>
```

### 3. Kubernetes

[Install Kubectl](https://kubernetes.io/docs/tasks/tools/)

Use the following command to create an Azure Kubernetes Cluster

```shell
az aks create --name <CLUSTER-NAME> --resource group <RESOURCE-GROUP-NAME> --node-count <DESIRED-NODE-COUNT> --generate-ssh-keys
```

Use the following to check for running nodes

```shell
kubectl get nodes
```
