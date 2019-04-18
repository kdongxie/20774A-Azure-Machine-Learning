# Module 2 Introduction to Azure Machine Learning
## Module Overview

- Machine Learning overview
- Introduction to Machine Learning Studio
- Developing and hosting Machine Learning applications

## Lesson 1: Machine Learning overview

- What is Machine Learning?
- Machine Learning and the Cortana Intelligence Suite
- Using Machine Learning with other Azure services

### What is Machine Learning?

#### Components of Machine Learning:

- Machine Learning Studio, a graphical development environment 
- Data preprocessing modules
- Machine learning algorithms
- APIs to expose a model to applications



#### Pricing options for Machine Learning:

- Free
- Standard (월 130만원)

### Machine Learning and the Cortana Intelligence Suite 

> Suite : 기존의 Azure Machine Learning의 기능을 Package형식으로 사용하도록 하는 것

#### **Information management**

- Azure Data Factory
- Azure Data Catalog
- Azure Event Hub



#### **Big data stores**

- Azure Data Lake
- Azure SQL Data Warehouse



#### **Machine learning and analytics**

- Machine Learning
- Azure Data Lake Analytics
- Azure HDInsight (Hadoop, Spark)
- Azure Stream Analytics



#### **Intelligence** [API 사용]

- Cognitive services [얼굴 인식]
- Bot framework [챗 봇]
- Cortana [음성 인식]



#### **Dashboards and visualizations**

- Power BI [화면에 출력 해주는 Service]



### Using Machine Learning with other Azure services
#### Cortana Intelligence Suite

- Experiments
- Jupyter Notebooks
- Solutions
- Tutorials



## Lesson 2: Introduction to Machine Learning Studio
- Introduction to Machine Learning Studio
- Workspaces
- Experiments and projects
- Modules
- Demonstration: Using Machine Learning Studio

### Introduction to Machine Learning Studio
#### Machine Learning Studio graphical tool used throughout the machine learning development life cycle:



- Data import
- Data preprocessing
- Feature selection
- Algorithm selection
- Model testing
- Model deployment
- Model retraining and redeployment

> 이후 프로젝트 시  활용 가능 !각각의 <Processing>을 알아두기

### Workspaces

#### Machine Learning workspace [Azure Machine Learning Studio]

- Container for projects, experiments, and models
- Linked to Microsoft account—can be shared



#### Storage

- Free: uses default storage account (10 GB maximum)  
- Standard: requires storage account



#### Roles

- User
- Owner



### Experiments and projects

#### Machine Learning experiments:

- Comprise at least one **dataset and one module**
- **Datasets** can **only be connected to modules**
- **Modules connect to datasets or to other modules**
- Input ports on all modules must be connected to the data flow
- Mandatory parameters on modules must be configured



#### Machine Learning projects:

- Experiments, datasets, notebooks



### Modules

#### Modules:

- Execute a specific machine learning **algorithm**, **function**, or **other code**
- Perform actions on data, or as part of working with other modules 
- Can operate independently
- Can be connected with other modules as part of a machine learning workflow
- Can be configured using parameters



#### Custom modules can be built using R

> Module을 개인적인 로직으로 구성할때에 R을 쓴다는 특징을 갖는다.

## Demonstration: Using Machine Learning Studio
### In this demonstration, you will see how to:

- Sign in to a Machine Learning Studio account
- Clone a sample experiment
- View the modules in an experiment



## Lesson 3: Developing and hosting Machine Learning applications
- Building Machine Learning applications
- Introduction to the Data Science Virtual Machine
- Using the Data Science VM
- Using N-series VMs for Machine Learning applications



### Building Machine Learning applications
#### To make a model available as an application:

1. Create a training experiment 
2. Convert the training experiment to a predictive experiment

![image](https://user-images.githubusercontent.com/46669551/56016352-e69a4d80-5d36-11e9-8f6a-c12d130cdb59.png)

![1555050400976](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1555050400976.png)

> Training 을 위한  Experiments의 Module중 불필요한 Module을 지워주고 실전사용 가능한 Processing 구성으로 Converting해준다.

#### To convert a training experiment to a predictive experiment:

1. Replace Machine Learning algorithm modules with code from the trained model

2. Remove unnecessary modules

3. Specify how the model will accept/return data



### Introduction to the Data Science Virtual Machine
- Data Science Virtual Machine:
- Microsoft R 
- Python
- Jupyter Notebook Server
- SQL Server 
- Visual Studio 
- Azure HDInsight (Hadoop)
- Data Lake
- Power BI desktop
- Azure Storage Explorer and AzCopy
- Azure CLI and Azure PowerShell

> 기본적인  Settings 들이므로 사용법만 알면되며, 가격 책정을 신경써라

### Using the Data Science VM

#### DSVM requires:

- Azure subscription
- Azure storage account



#### Usage costs:

- Azure compute charges
- No software charges



### Using N-series VMs for Machine Learning applications
#### N-series Azure NC VMs:

- Designed for compute-intensive applications 
- Powered by NVIDIA Tesla® K80 GPUs

![image](https://user-images.githubusercontent.com/46669551/56016547-8c4dbc80-5d37-11e9-8e10-10a4ec73ff98.png)

#### DSVM Deep Learning Toolkit:

- Available on Windows version of DSVM (preconfigured with GPU enabled)
- Includes sample solutions that use GPU processing



## Lab: Introduction to Machine Learning
- Exercise 1: Using Machine Learning Studio
- Exercise 2: Clone and run a simple experiment

> **Lab Scenario**
>
> You work as a data scientist for Adatum Consultants, a company that provides
> machine learning services and advice for a range of clients. Adatum Consultants
> helps these clients understand and visualize their data, discover patterns and
> correlations, and determine the optimum ways to present data to be consumed by
> users and applications. You will be using Machine Learning with your clients
> so, to familiarize yourself with this environment, you need to explore Machine
> Learning Studio workspaces—and then look at the cloning and managing of machine
> learning experiments.

> **Lab Review**
>
> - How would you compare the sharing and tracking features in Machine Learning Studio
>   with those in any source control software you have used?
> - What are some of the key reasons why you might need to use standard workspaces,
>   rather than free workspaces, in your organization?