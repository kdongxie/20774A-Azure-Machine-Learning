# Module 10 Using Azure Machine Learning Models

## Module Overview

- Deploying and publishing models
- Consuming experiments

> Machine Learning Models의 Logic을 적용한 후 Deploy 를 통해 사용하는 방법에 대하여 학습한다. 

## Lesson 1: Deploying and publishing models
- Deployment overview
- Using <u>[xml]web service</u> parameters (Web Mathod)
- The Cortana Intelligence Gallery (음성인식)
- Demonstration: Deploying and publishing experiments

### Deployment overview

- Training experiment
- Predictive experiment
- Web service
  - New
  - Classic

### Using [web service parameters](<https://docs.microsoft.com/ko-kr/azure/machine-learning/studio/web-service-parameters>)

- Web service parameters can:
  - Increase the number of features
  - Change the export destination

### The Cortana Intelligence Gallery

- Experiments 
- Jupyter Notebooks 
- Solutions 
- Tutorials 
- Collections
- Industries

### Demonstration: Deploying and publishing experiments
In this demonstration, you will see how to:

- Create a new standard Machine Learning Workspace
- Open a sample experiment
- Publish the experiment as a web service
- Add export path as a web service parameter
- Deploy the web service

## Lesson 2: Consuming experiments

- Consuming a published experiment
- Using Excel with a published model
- Using the Export Data module
- Demonstration: Consuming Machine Learning experiments

### Consuming a published experiment

- Request-Response Service
- Batch Execution Service
- Batch Pool

### Using Excel with a published model

- Excel add-in
- Macro version
- New and classic web services 

### Using the Export Data module

- Export Data module
  - Hive query
  - Azure SQL Database
  - Azure Table
  - Azure Blob storage account

### Demonstration: Consuming Machine Learning experiments
In this demonstration, you will see how to:

- Use the API testing console to send test requests to an experiment
- View the test results

## Lab: Using Machine Learning experiments
- Exercise 1: Publish a Machine Learning model
- Exercise 2: Consume a Machine Learning model

#### [Office Store](<https://store.office.com/addinsinstallpage.aspx?rs=en-US&assetid=WA104379638>)

![image](https://user-images.githubusercontent.com/46669551/56485234-2bc83780-650e-11e9-9700-385c33e1f4a3.png)

#### Azure Machine Learning in Excel

![image](https://user-images.githubusercontent.com/46669551/56485276-5a461280-650e-11e9-9c13-9770b7a1b04d.png)







>Lab Scenario
>
>You work as a data scientist at Adatum Consultants, a company that provides machine
>learning services and advice for a range of clients. Your client has asked you
>to publish a machine learning model that predicts whether adults have an income
>of more or less than USD50,000 a year. Your client runs an e-commerce company
>and they want to show a different home page to users depending on their annual
>income.
>
>You will publish this model and consume predictions using HTTP
>calls via Fiddler and the BES endpoint with a C# application. You will also
>investigate scored predictions using Microsoft Excel. 

>Lab Review
>
>- Where can having the Excel add-in help you?

>Module Review and Takeaways
>
>**Review Question(s)**
>
>**Question**
>
>What kinds of modeling could students add to the Gallery?
>
>**Answer**
>
>Answers will vary, depending on the students’ experience.