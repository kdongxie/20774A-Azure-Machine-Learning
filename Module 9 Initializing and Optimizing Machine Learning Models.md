# Module 9 Initializing and Optimizing Machine Learning Models
## Module Overview

- Using [<u>hyperparameters</u>](<https://m.blog.naver.com/PostView.nhn?blogId=laonple&logNo=220571820368&proxyReferer=https%3A%2F%2Fwww.google.com%2F>)
- Using multiple algorithms and models
- Scoring and evaluating models

### Team Data Science Process [TDSP]

| **1.   Business Understanding** |     **2.   Data Acquisition and Understanding**     |   **3.  Modeling**   |         **4.   Deployment**          |
| :-----------------------------: | :-------------------------------------------------: | :------------------: | :----------------------------------: |
|         Technical needs         |      Loading data into storage   environments       | Engineering features | Publishing a model as a web service  |
|    Identifying your scenario    | Importing data into Azure Machine   Learning Studio |  Selecting features  | Consuming a model   programmatically |
|                                 |                   Preparing data                    | Learning with counts |      Consuming a model in Excel      |
|                                 |                   Exploring data                    |  Training the model  |                                      |
|                                 |                     Sample data                     | Evaluating the model |                                      |
|                                 |                                                     |   Tuning the model   |                                      |

## Lesson 1: Using hyperparameters [인자]

- Overview of parameters
- Optimizing parameters
- Defining the parameter space
- Defining cross-validation settings
- Demonstration: Using cross-validation folds
- The Tune Model Hyperparameters module
- Defining the evaluation metric
- Training, evaluating, and comparing
- Demonstration: Using hyperparameters

### Overview of parameters

Hyperparameters

- Define higher-level features of a model:
- Cannot be directly learned from data using the model training process
- Are provided as inputs when running and training the model

Optimal values are selected by trial and error during training

> Learning Rate (학습 진도율) 
>
> Cost Function
>
> Regularization parameter
>
> Mini-batch 크기
>
> Training 횟수
>
> Hidden Unit의 개수
>
> Weight initialization (가중치 초기화)

### Optimizing parameters

Before model selection:

- Define the parameter space
- Define cross-validation settings
- Define the evaluation metric

Model selection:

- Train the model with each unique combination of values in the parameter space
- Compare the results of cross-validation using the specified metric
- Select the best-performing model

### Defining the parameter space

- Can supply a single value for each parameter
- Can supply a comma-separated list for each parameter
- Can provide <u>minimum value, maximum value, and number of points</u>
  - Can use a linear scale or log distribution

### Defining cross-validation settings

- You can use the Partition and Sample module to work with a subset of your data
- You can create a sample of your data and specify:
  - The rate of sampling
  - Fixed or random seed values
  - Fixed or random splits of the dataset

- You can split your data into partitions and specify:
  - Whether to reuse sampled data
  - Whether rows are randomly chosen
  - Whether partitions are even

### Demonstration: Using cross-validation folds
In this demonstration, you will see how to configure the **Partition and Sample** module to:

- Create a subset of cases from the beginning of a dataset
- Create a sample of data
- [Split data into partitions](<https://gallery.azure.ai/Experiment/Sample-9-Split-partition-and-sample-system-2>)
- Use data from a predefined partition

> Partition and Sample module  - Properties options
>
> 1. Rate of Sampling : 0.1 = 전체 데이터의  10%를 랜덤하게 뽑아 샘플링 한다.
> 2. head : 100 = 정체 데이터이서 100개의 rows를 가져온다.
> 3. Select  a single column 을 지정한 후 진행되면 지정된  column에서 랜덤으로 뽑아낸다.
> 4. Assign to Folds : folds의 수를 지정하여 sub dataset을 몇개 만들지 정할 수 있다.
> 5. Specify the partitioner method 에서  List of proportions separated by comma 하여 (예시: 0.1,0.1,0.5) 전체 데이터를 %로 나누어 준다. 예시와 같이 분류하면 총 4개의 folds가 만들어 지게 된다. 이유는 0.1+0.1+0.5는 0.7로 전체 데이터가 되기 위해서는 0.3이 모자르게 되고 이 나머지 0.3는 자동으로 하나의 fold로 지정되게 된다.
> 6. Pick-Fold : (예시 3) = Assign to Folds에서 나눈 Fold의 번호(순번)를 입력하여 원하는 fold만을 가져올 수가 있다.  

![image](https://user-images.githubusercontent.com/46669551/56399929-03c9a180-628c-11e9-8d01-0cedace26d9d.png)

### The Tune Model Hyperparameters module

- **Automate the trial-and-error** approach for finding optimal parameters
- Two methods for finding the best model:
  - Integrated train and tune
  - Cross-validation with tuning

- Parameter sweep configurations:
  - Random sweep
  - Grid sweep

### Defining the evaluation metric

- Select the evaluation metric in the properties of the **Tune Model Hyperparameters** module
- Different metrics are used for classification models and regression models

### Training, evaluating, and comparing

- **Tune Model Hyperparameters** inputs:
  - Untrained learner
  - Primary dataset
  - Optional second dataset containing fold definitions or validation dataset

- Outputs
  - Evaluation metric dataset
  - Best model

### Demonstration: Using hyperparameters
In this demonstration, you will see how to

- Create a tuned model
- Create an untuned model (for comparison)
- Compare the results

![image](https://user-images.githubusercontent.com/46669551/56400787-a84de280-6290-11e9-8d53-07a1f8786275.png)

Tune Model Hyperparameters

![image](https://user-images.githubusercontent.com/46669551/56400811-c3205700-6290-11e9-8547-d6645315c7fc.png)

![image](https://user-images.githubusercontent.com/46669551/56400832-e0edbc00-6290-11e9-96c5-072daf3eeb7d.png)

Train Model

![image](https://user-images.githubusercontent.com/46669551/56400851-fb279a00-6290-11e9-9353-156ddd2b5c9b.png)

![image](https://user-images.githubusercontent.com/46669551/56400861-0b3f7980-6291-11e9-8559-87cc62c1402e.png)

두 모델을 비교 [파랑 Tune Model Hyperparameters]

![image](https://user-images.githubusercontent.com/46669551/56400902-45108000-6291-11e9-9a01-7dc59db63927.png)

![image](https://user-images.githubusercontent.com/46669551/56400914-55285f80-6291-11e9-93cb-b09d38d7fbe7.png)

두개의 Model을 비교했을 때 Support Vector Machine의 Parameter를 지정해 주고, Tune Model Hyperparameter를 사용 한 것이 성능이 더 좋음을 알 수 있다. 

> 각 알고리즘에는 자체 매개 변수가 있습니다. 올바른 데이터 선택 각 데이터 집합 및 알고리즘에 대한 매개 변수를 선택하면 정확도를 높일 수 있습니다. Azure ML에는 구성 요소 이름 " **Tune Hyper Parameters** "가 있습니다. 이 구성 요소는 정확성을 향상시키는 데 도움이됩니다.
>
> 튜닝 모델은 두개의 입력 을 받게 된다.  하나는 데이터 용이고 다른 하나는 알고리즘의 분할 데이터 구성 요소에서 오는 학습 모델의 목표입니다. 실제로이 구성 요소는 **Train Model을** 대체 할 수 있습니다 .
>
> 
>
> Grid : 논리 곱
>
> Parametets1 -> 1,2,3
>
> Parameters2-> A,B,C,D
>
> ​     	1	    2	    3
>
> A	A,1	A,2	 A,3
>
> B	B,1	B,2	 B,3
>
> C	C,1	C,2	 C,3
>
> D	D,1	D,2	D,3
>
> ![image](https://user-images.githubusercontent.com/46669551/56401680-0aa8e200-6295-11e9-8131-842da2d68ae3.png)
>
> entire grid는 전체의  매개변수의 값을 선택하여 매개변수를 서로 비교한다.
>
> random sweep 무작위로 매개 변수의 값을 선택하여 일련의 학습 반복을 수행합니다. 따라서이 구성 요소는 다른 매개 변수의 값을 임의로 시도하고이를 기반으로 모델을 학습합니다
>
> random grid   

## Lesson 2: Using multiple algorithms and models

- Algorithm selection

- **Trade-offs** between machine learning algorithms 

  [Trade-off: 한가지가 장점으로 부각되면 한부분은 낮아지는 현상]

- Decision trees [Entropy를 사용]

- Overview of ensembles [앙상블을 통해 집계된 결과 중 최고를 구하는 방법]

- Bagging, boosting, and stacking

- Demonstration: Evaluating an ensemble by using stacking

> Cheat Sheet를 활용하기

### Algorithm selection

- The Microsoft Learning Algorithm Cheat Sheet is:
  - A starting point for algorithm selection
  - Based on industry **recommendations**[추천시스템] and best practices

### Trade-offs between machine learning algorithms
- Accuracy
- Training time
- Number of parameters
- Linearity
- Number of features

### Decision trees

![image](https://user-images.githubusercontent.com/46669551/56346040-2ca25600-61fc-11e9-95ed-46dff12ea706.png)

### Example of a decision tree algorithm
![image](https://user-images.githubusercontent.com/46669551/56346072-43e14380-61fc-11e9-8ed8-e6ff8d3b0482.png)

### Overview of ensembles

- Combining the outputs of **several classifiers** may reduce the risk of selecting a poorly performing classifier and avoid overfitting
- The errors made while classifying instances by one classifier are generally averaged out by the correct classification of another classifier, so that the overall classification accuracy is improved
- Base classifiers should be diverse in nature so that a final **unbiased** decision can be taken

### Bagging, boosting, and stacking

- Bagging
  - Decreases variance

- Boosting
  - Reduces bias

- Stacking 
  - Improves accuracy

### Demonstration: Evaluating an ensemble by using stacking

In this demonstration, you will see how to:

- Explore a Gallery experiment that uses stacking to build an ensemble of classifiers
- Evaluate the ensemble experiment



## Lesson 3: Scoring and evaluating models
- Scoring models
- Evaluating models
- Test and training datasets

### Scoring models

- **Apply Transformation** module, for applying a data transformation to a dataset
- **Score Matchbox Recommender** module, for recommendation and relationship models
- **Assign Data to Clusters** module, for clustering models
- The **Score Model** module, for all other model types

### Evaluating models [중요함 알아두기]

#### Evaluate Model Metrics for Classification Models

- **Accuracy, Recall, Precision, and F1-Score**
- **AUC**
- **Average log loss**
- **Training log loss**

#### Metrics for Regression Models

- **Mean absolute error (MAE)**
- **Root-mean-square error (RMSE)**
- **Relative absolute error (RAE)**
- **Relative square error (RSE)**
- **Coefficient of determination**

### Test and training datasets

![image](https://user-images.githubusercontent.com/46669551/56346249-adf9e880-61fc-11e9-8122-ccfde907b0c8.png)

## Lab: Initializing and optimizing Machine Learning models
- Exercise 1: Using hyperparameters

>Lab Scenario
>
>You work as a data scientist for Adatum Consultants, a company that provides
>machine learning services and advice for a range of clients. One of your
>clients runs an e-commerce company and they want to show a different home page
>to users depending on their annual income. Your client has, therefore, asked
>you to test and evaluate a machine learning model that predicts adult incomes. 
>
>As part of this evaluation, you need to compare a tuned model with an untuned
>model, and investigate the effects of using hyperparameters for tuning.

>Lab Review
>
>- What are the input and output nodes of the Tune Model Hyperparameters
>  module?
>- Why did you use two Split Data modules in the lab experiment?

![image](https://user-images.githubusercontent.com/46669551/56411824-05f82400-62bd-11e9-962b-9fa25bb7c8e7.png)

![image](https://user-images.githubusercontent.com/46669551/56411847-19a38a80-62bd-11e9-88cf-fa335e2340cc.png)

![image](https://user-images.githubusercontent.com/46669551/56411864-2aec9700-62bd-11e9-88c0-fa9c041961e8.png)

일반 Train model

![image](https://user-images.githubusercontent.com/46669551/56411894-448dde80-62bd-11e9-88c3-17dbec920f70.png)

![image](https://user-images.githubusercontent.com/46669551/56411901-52436400-62bd-11e9-9543-5226fd18768d.png)

