# Module 4 Preparing Data for use with Azure Machine Learning
## Module Overview

- Data preprocessing
- Strategies for incomplete datasets

## Lesson 1: Data preprocessing

- Introduction to data preprocessing
- Cleaning data
- Normalizing data
- Reducing data complexity

### Introduction to data preprocessing

- Data preprocessing:
  - Identifying issues requires thorough data exploration
  - Power BI can help during exploration phase
  - Issues can include:
    - Missing information or incomplete records
    - Noisy data with outliers [이상한 데이터의 유무]
    - Other inconsistencies and discrepancies [데이터의 연관성]



- Tools for preprocessing:
  - SQL or Hive queries
  - R or Python scripts
  - Machine Learning modules

### Cleaning data

- Cleaning data involves:
  - Resolving missing values [Null 값 처리]
  - Updating or removing incorrect values [추가 또는 제거]



- Methods for cleaning data:
  - **Machine Learning modules** [select을 검색]
  - **R scripts**

### Normalizing data [Scaling]

Normalization:

- Transform data to a common scale
- Create consistent scales across data sources
- Change absolute values to a scale or percentage



Normalize Data module methods:

- **Zscore**
- **MinMax**
- **Logistic**
- **LogNormal**
- **TanH** : 쌍곡 탄젠트 계산

> TanH
>
> ![image](https://user-images.githubusercontent.com/46669551/56175554-9ec73f00-6032-11e9-9b23-96f3a2db2bc4.png)
>
> ![image](https://user-images.githubusercontent.com/46669551/56175599-d1713780-6032-11e9-8739-554252ad9bd7.png)
>
> 





### Reducing data complexity

- Grouping to reduce complexity

- Quantization:

  - Continuous data to bins/buckets
  - For example:
    - Ages: 0-10, 11-20, 21-30, and so on

  - Group Data into Bins module 

- Lookup tables:

  - Category data to smaller set

  - For example:
    - Car models to type: SUV, sedan, station wagon, and so on

  - Group Categorical Values module

  - R script

## Lesson 2: Strategies for incomplete datasets
- Handling missing data
- Dealing with outliers
- Working with imbalanced data
- Demonstration: Preprocessing data using Machine Learning



### Handling missing data

Methods for handling missing data include: [Missing Value: 값이 없는 것이 아님]

- **Removing records** that include missing values
- **Replacing** missing data with an **average value**
- **Replacing** missing values with the most **likely value**
- **Replacing** missing values with a **marker**

### Dealing with outliers

- **Outliers** can negatively affect results : 발생될수 있는 데이터에서 완전 동떨어지는 값 Filtering
- In some situations outliers contain useful data
- The **Clip Values module** can remove outliers



> - **ClipPeaks** : 피크로 값을 **자르면** <u>상위 경계 만 지정</u>합니다. 경계 값보다 큰 값은 대체되거나 제거
> - **ClipSubpeaks** : 하위 봉우리로 값을 **자를** 때 더 <u>낮은 경계 만 지정</u>합니다. 해당 경계 값보다 작은 값은 대체되거나 제거
> - **ClipPeaksAndSubpeaks** : 봉우리와 하위 봉우리로 값을 **자를** 때 <u>상한과 하한 경계를 모두 지정</u>할 수 있습니다. 해당 범위를 벗어나는 값은 대체되거나 제거됩니다. 경계 값과 일치하는 값은 변경되지 않음
>
> [Clip Values module](<https://docs.microsoft.com/en-us/azure/machine-learning/studio-module-reference/clip-values>)
>
> ![image](https://user-images.githubusercontent.com/46669551/56175693-40e72700-6033-11e9-962d-669fe44a0026.png)

### Working with imbalanced data

- Imbalanced data can lead to some classes being underrepresented
- SMOTE can be used to rebalance data
- Care should be taken to ensure model accuracy

### Demonstration: Preprocessing data using Machine Learning
In this demonstration, you will see how to:

- Use the Summarize module to identify issues with imported raw data
- Clean the import to remove rows with missing data
- Remove outliers from the imported data

## Lab: Preparing data for use with Machine Learning
- Exercise 1: Explore data using Power BI
- Exercise 2: Preprocess data using Machine Learning Studio

>Lab Scenario
>
>You work as a data scientist for Adatum Consultants, a company that provides
>machine learning services and advice for a range of clients. One of your
>clients is Wide World Importers, who are transitioning from a Business
>Intelligence practice to a Business Analytics practice. As part of this
>transition, Wide World Importers are looking for insights from operational data
>sources throughout the organization.
>
>You are working with a team of business analysts from Wide World Importers who write
>reports using data that is stored in a variety of locations, including Azure
>SQL Database. You are following the recommended steps of the Team Data Science
>Process (TDSP). As part of the TDSP, you will explore and prepare the data, as
>per the Data Acquisition and Understanding phase of the process. You will be
>using Power BI and Machine Learning with this team so, to familiarize yourself
>with the environment, you need to explore the steps required in Power BI to
>identify data issues—and then to perform some data preprocessing steps in
>Machine Learning Studio. 

> Lab Review
>
> - What are some of the potential benefits of using Power BI to visualize a source
>   dataset before importing it into Machine Learning?
> - Why is it important to fully understand your dataset before running any form of
>   cleaning or transformation on that data?

![image](https://user-images.githubusercontent.com/46669551/56182116-916a7e80-604b-11e9-9703-e5fc4497eee7.png)

![image](https://user-images.githubusercontent.com/46669551/56182158-cb3b8500-604b-11e9-8531-2adff73161c0.png)

