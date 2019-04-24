# Module 13 Using R services with Machine
Learning

## Module Overview

현재는 Machine Learning Server로 바뀌었다.

- Overview of R and R Server
- Using R Server with Machine Learning
- Using R with SQL Server

## Lesson 1: Overview of R and R Server
- Overview of R Server
- Environments for running R Server
- R Client

### Overview of R Server

- R Server is the “enterprise” version of R:
  - RevoScaleR provides robustness

- **R Server can be installed on Linux or Windows**
- **For big data, R Server can be installed on Hadoop or Spark clusters**

### Environments for running R Server

- R Server can run on servers:
  - Windows
  - Linux

- R Server can run on clusters:
  - Hadoop
  - Spark

- Install through regular SQL Server setup or standalone installer

- Install R packages for Linux server

### R Client [Microsoft R Client]

Microsoft에서 자체 적으로 제공하는 R Client이다.

- Environments for running R Client

- How do you install R Client?

  - Download R Client for your operating system and follow the installation sequence for Windows or Linux

  - Configure the IDE to point at your R executable file

- How do you connect to a remote server by using R Client?

## Lesson 2: Using R Server with Machine Learning
- Getting started with R Server
- R Server example tasks
- Remote execution on R Server
- Demonstration: Executing remote commands

### Getting started with R Server

- Perform analytics with R by using R Server on HDInsight

- ScaleR provides functions to distribute and parallelize the data

- Compute contexts

  - **rxSetComputeContext(“local”)**

  - **rxSetComputeContext(“localpar”)**

  - **RxSpark**

  - **RxHadoopMR**

### R Server example tasks

- Microsoft case studies
- Partner case studies
- Cortana Intelligence Gallery

### Remote execution on R Server

- **mrsdeploy** login functions

  - **remoteLogin()**

  - **remoteLoginAAD()**



- Switching compute contexts

### Demonstration: Executing remote commands
In this demonstration, you will see how to: 

- Enable remote access to R Server
- Use R Client to execute R commands in a remote session

## Lesson 3: Using R with SQL Server

- Using R with SQL Server
- Deploy SQL Server 2016 on an Azure VM
- Configuring SQL Server to enable execution of R
- Executing R scripts inside T-SQL statements
- Data Visualization with R
- Demonstration: Creating R graphics from R Server

### Using R with SQL Server

- **R Services (in-database)** enables the execution of R scripts on SQL Server 

- **R Server** is enterprise-scale R for big data

### Deploy SQL Server 2016 on an Azure VM
- Configure options in the Azure Portal
- Select SQL Server VM image

### Configuring SQL Server to enable execution of R
To run R code directly from SQL Server:

- Use the **sp_execute_external_script** stored procedure
- Enable this procedure using the **sp_configure** command
- Restart SQL Server

### Executing R scripts inside T-SQL statements
- Specify the language extension to invoke
- View active R scripts
- Monitor usage of external script execution

### Data Visualization with R

- R Server can generate R graphics
- The default location for graphic output is the current folder from which you executed the command

### Demonstration: Creating R graphics from R Server
In this demonstration, you will see how to:

- Create a stored procedure to run R code and extract useful data
- Create a stored procedure to run R code and plot extracted data
- Use PowerShell to deploy a stored procedure and create a graphic from data

## Lab: Using R Services with Machine Learning
- Exercise 1: Deploy the Data Science virtual machine
- Exercise 2: Prepare a sample SQL Server database, and configure SQL Server and
  R Server
- Exercise 3: Use a remote R session
- Exercise 4: Execute R scripts inside T-SQL statements

>Lab Scenario
>
>You work as a data scientist for Adatum Consultants, a company that provides machine learning services and advice for a range of clients. One of your clients is Wide World Importers, who are planning the deployment of applications that use SQL Server data and R scripts. You have decided to do a small proof of concept before working with this client.
>
>You are going to ramp up quickly with the Data Science virtual machine. As a first step, you will need to deploy the virtual machine from the Azure Portal. After you have deployed the Data Science virtual machine from the Azure Portal, you can explore some of the tools available. You will also configure a test database, using data supplied by Wide World Importers, and enable SQL Server to accept external scripts. Finally, you will configure R Server, and enable remote access from machines running R Client.
>
>You will also test the use of R commands in a remote session, and the execution of R scripts inside T-SQL statements. 

>Lab Review
>
>- Why do you need to add an inbound security rule before you can use remote R
>  commands?
>- Why might you select to use SSD storage when deploying an instance of the Data
>  Science VM?

> Module Review and Takeaways
>
> **Review Question(s)**
>
> **Question**
>
> Based on your own organization’s data analysis requirements, what do you think R adds to SQL Server?
>
> **Answer**
>
> Answers will vary, depending on the students’ experience.

>Course Evaluation
>
>- Your evaluation of this course will help Microsoft understand the quality of your learning experience.
>
>- Please work with your training provider to access the course evaluation form.
>
>- Microsoft will keep your answers to this survey private and confidential and will use your responses to improve your future learning experience. Your open and honest feedback is valuable and appreciated.