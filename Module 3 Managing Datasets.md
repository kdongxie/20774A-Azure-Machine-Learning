# Module 3 Managing Datasets

## Module Overview

- Categorizing your data
- Importing data to Machine Learning
- Exploring and transforming data in Machine Learning

## Lesson 1: Categorizing your data

- Data structure [데이터 구조]
- Dataset size and big data [데이터 크기]
- Demonstration: Load data from Hadoop using Hive [하둡]
- Data purpose [데이터 목적]

### Data structure

- Growth of information storage capacity exceeds **Moore’s Law**

  - Businesses rarely throw data away

  - Growth of unstructured data much higher than growth of structured data

> ## 무어의 법칙의 3가지 조건
>
> 무어의 법칙의 세 가지 조건은 다음과 같다.
>
> 1. 반도체 메모리칩의 성능 즉, 메모리의 용량이나 CPU의 속도가 18개월에서 24개월마다 2배씩 향상된다는 '기술 개발 속도에 관한 법칙'이다.
> 2. 컴퓨팅 성능은 18개월마다 2배씩 향상된다.
> 3. 컴퓨팅 가격은 18개월마다 반으로 떨어진다.

- Essential to understand data structure types

  - Structured data[정형]:
    - RDMS, SQL Server, Excel

  - Unstructured data[비 정형]: 
    - Text, blogs, images[**binary** file], audio, video

### Dataset size and big data

- Big data is challenging because:
  - It can have complex structures 
  - It might have no structure at all
  - The data source might not be static



- The three Vs:
  - Volume
  - Variety
  - Velocity



- Big data technologies: Hadoop/HDInsight



## Demonstration: Load data from Hadoop using Hive
In this demonstration, you will see how to:

- Upload data to Azure Blob storage
- Import data to Hive table
- Access the Hadoop data using Hive query
- Explore the data



## Data purpose

- Sample data

  - How was the sample made?

  - What criteria were used to create the sample?

  - Is the sample special?

  - Was there unconscious or subjective bias in the sample taking process? 

- Training data

  - 70% training, 30% testing

  - 70% training, 20% validation, 10% testing

- Predictive data
  - Not the same as training data



## Lesson 2: Importing data to Machine Learning
- Importing data—Overview
- Using online data sources
- Using offline data sources
- Demonstration: Load data from a website by using HTTP



### Importing data—Overview

- Data Sources:
  - Offline 
  - Online: live vs. cached
  - Generated

- Data formats:
  - Txt, CSV, TSV, Excel
  - Azure table, Hive table
  - SQL database table
  - OData
  - SVMLight
  - ARFF, zip
  - RData

- Data types:
  - String
  - Integer
  - Double
  - Boolean
  - DateTime
  - TimeSpan



### Using offline data sources

- Offline Data Sources:
  - CSV
  - TSV
  - RData files
  - ARFF files
  - SVMLight



## Demonstration: Load data from a website by using HTTP
In this demonstration, you will see how to: 

- Import CSV data from a web URL
- Visualize the imported data
- Add column names to imported data



## Lesson 3: Exploring and transforming data in Machine Learning
- Exploring data
- Transforming data
- Splitting data



### Exploring data

- Exploring data is the key step:
  - Descriptive statistics (기술통계) [Visualize 사용]
  - Data export
  - Power BI



- Summarizing data:
  - How many records are there?
  - Are there missing values? 
  - How many unique values are there?
  - Mean, standard deviation, and so on



### Transforming data

- Adding data
  - Small sample size
  - Missing data

- Removing data
  - Duplicate records

- Numerical encoding
  - Text to numbers

- Data conversion
  - Convert values to another value type

- Applying data transformations
  - SQL queries
  - R or Python code
  - Machine Learning modules



### Splitting data

- Split data:
  - Training dataset
  - Testing dataset
  - Validation dataset



- **Partition and Sample** and **Split Data** modules:
  - Data sampling
  - Dividing datasets
  - Returning a subset
  - Returning top rows



## Lab: Managing datasets

- Exercise 1: Preparing the lab
- Exercise 2: Importing data into Machine Learning
- Exercise 3: Converting imported data into separate datasets

>Lab Scenario
>
>You work as a data scientist for Adatum Consultants, a company that provides
>machine learning services and advice for a range of clients. One of your
>clients is Wide World Importers, who are transitioning from a Business
>Intelligence practice to a Business Analytics practice. As part of this
>transition, Wide World Importers are looking for insights from operational data
>sources throughout the organization.
>
>You are working with a team of business analysts from Wide World Importers, who
>write reports using data that is stored in a variety of locations, including
>flat files, Azure Blob storage, and Azure SQL Database. You will be using
>Machine Learning with this team so, to familiarize yourself with this
>environment, you should explore the steps required in Azure Machine Learning
>Studio to import data and to manage datasets.

>Lab Review
>
>- How much data should you use for training?
>- When might the use of cached data not be a good idea?

![image](https://user-images.githubusercontent.com/46669551/56175185-ef3d9d00-6030-11e9-9905-a3c0f1eba404.png)



![image](https://user-images.githubusercontent.com/46669551/56175213-16946a00-6031-11e9-81d0-fd248ea91b48.png)

![1555377768724](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1555377768724.png)