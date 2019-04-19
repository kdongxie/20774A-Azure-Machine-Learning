# Module 5 Using Feature Engineering and Selection in Azure Machine Learning
## Module Overview

- Using feature engineering
- Using feature selection

> 데이터를 정의 하거나 데이터를 조작하는 방법에 대하여 학습한다. 
>
> : 전처리의 과정을 거친 후 진행하게 된다.
>
> : Column을 사용(항목에 함수를 정의하거나 추가하는 방법)
>
> : 해당 Column을 줄이거나 추가하는 방법을 사용

## Lesson 1: Using feature engineering

- Feature engineering overview
- **Merging datasets**
- **Merging and combining data**
- Demonstration: **Using Join** to merge data



### Feature engineering overview

**Feature Engineering**

- Generates additional features
- Combines existing features
- Provides Data Transformation

### Merging datasets

- Merging datasets:
  - Main dataset plus update dataset to enrich the source data
  - Datasets from two or more sources



- Machine Learning modules:
  - **Join Data**
  - **Add Rows**
  - **Add Columns** 

### Merging and combining data



- Merging data:
  - Combine columns into a single set of predictive data
  - Rolling aggregates for time-series data
  - Calculated features



- Tools for merging and combining data:
  - Custom R scripts
  - SQL, Python, or Hive queries
  - Machine Learning modules, such as Feature Hashing and Apply SQL Transformation

### Demonstration: Using Join to merge data
In this demonstration, you will see how to:

- Create a transaction dataset by importing from Azure SQL Database
- Upload a date dataset from a flat file
- Add the second dataset to an experiment
- Join the transaction and date datasets

## Lesson 2: Using feature selection

- Feature selection overview
- Reducing data dimensions
- Selecting features
- Demonstration: Using count-based featurization

### Feature selection overview [Model prediction을 향상]

**Feature Selection**

- Filters out irrelevant features [관계없는 항목을 제외 시켜주는 과정]
- Distinguishes classes of objects dependent on their relationships

> 피러슨 상관계수 등의 관계를 보아야 한다. 
>
> 0 에 가까워 질 수록 관계가 적어지고 , 1에 가까워 질수록 관계가 짙어 진다.

### Reducing data dimensions [차원축소]

- Reducing data dimensions:
  - Uses data transformation, and other methods, to modify the original features


- Examples:
  - **Principal Component Analysis (PCA)**
  - **Canonical correlation analysis**
  - **Singular Value Decomposition**

- **Learning with Counts modules**:
  - **Build Counting Transform**
  - **Export Count Table**
  - **Import Count Table**
  - **Merge Counting Transform**
  - **Modify Count Table Parameters**

### Selecting features

- Selecting features



- Tools:

  - **Filters**
    - For example, moving averages, moving medians, waveform decomposition 

  - Edit metadata

### Demonstration: Using count-based featurization
In this demonstration, you will see how to

- Use an example **counting transformation**

![image](https://user-images.githubusercontent.com/46669551/56254045-1e6c1100-60fa-11e9-91b1-fa8faca4b130.png)

![image](https://user-images.githubusercontent.com/46669551/56253583-fe3b5280-60f7-11e9-8c32-ae9236666394.png)

![image](https://user-images.githubusercontent.com/46669551/56253628-2a56d380-60f8-11e9-9ba6-c50b8ee29e4d.png)

> <출력 결과 해설 >
>
> - Receiver Operating Curve (ROC) 가 왼쪽 상단의 corner에 근접할 수 록 더욱 성공한 모델이다.
>
> 이번 결과를 보았을 때에 외쪽 상단에 매우 근접함을 볼 수 있다. 따라서 이 모델은 성공적인 모델로 보여질 수 있다. 그러나 그래프가 아닌 실제 측정 된 수치를 확인하여야 한다. 
>
> - Accuracy (정확도)는 0.969로 예측된 관측치가 얼마만큼 정확한지를 나타내며,  직관적으로 높은 수치이다.
>
> - Precision(정밀도)는 0.946으로  높은 수치로 일관된 값을 나타내는 Model임을 표현하고 있다.
>
> - Recall (재현율)은 0.996으로 전체의  예측값에서 매우 높은 수치로 원래 데이터와 일치하는 값을 나타냄을 보여주고 있다. 
>
> - F1 (F-Score)는 0.970 으로 Model의 성능을 나타내 준다. [양의 값과 음의 값을 가질 수 있는 특징]

- Accuracy : 정확도

- Precision : 정밀도 

> 정보 검색 분야에서 정밀도(precision)는 검색된 문서들 중 관련 있는 문서들의 비율이다.

- Recall : 재현율

> 정보 검색 분야에서 재현율(recall)은 관련 있는 문서들 중 실제로 검색된 문서들의 비율이다.

- F1 = (Precision+Recall)/2

![image](https://user-images.githubusercontent.com/46669551/56252844-cd0d5300-60f4-11e9-8d3a-fb1f998b723c.png)

![image](https://user-images.githubusercontent.com/46669551/56252880-05ad2c80-60f5-11e9-8ca3-217332adf5a0.png)



## Lab: Lab: using feature engineering and selection

- Exercise 1: Prepare datasets ready for merging
- Exercise 2: Use Join to create new merged dataset

>Lab Scenario
>
>You work as a data scientist for Adatum Consultants, a company that provides
>machine learning services and advice for a range of clients. One of your
>clients is Wide World Importers, who are transitioning from a Business
>Intelligence practice to a Business Analytics practice. As part of this
>transition, Wide World Importers are looking for insights from operational data
>sources throughout the organization.
>
>You are working with a team of Wide World Importers business analysts, who write reports
>using data that is stored in a variety of locations, including Azure SQL
>Database, and various local flat files. You are following the recommended steps
>of the Team Data Science Process (TDSP). As part of the TDSP, you will perform
>some feature engineering steps, as per the Modeling phase of the process. You
>will be using Machine Learning with this team so, to familiarize yourself with
>this environment, you need to explore the steps required to merge two datasets
>in Azure Machine Learning Studio. 

> Lab Review
>
> - Why is it important to fully understand your datasets before running any form of
>   merging or combining on these datasets?
> - What steps could you take if you did not have a common key field, or feature,
>   in two datasets that you wished to join together?

![image](https://user-images.githubusercontent.com/46669551/56196150-41061780-6071-11e9-9940-76e322777066.png)

![image](https://user-images.githubusercontent.com/46669551/56196207-5713d800-6071-11e9-89ca-3bed3d999ce1.png)

