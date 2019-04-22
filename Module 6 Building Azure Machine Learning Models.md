# Module 6 Building Azure Machine Learning Models
## Module Overview

- Workflows in Azure Machine Learning
- Scoring and evaluating models
- Using regression algorithms
- Using neural networks



## Lesson 1: Workflows in Azure Machine Learning
- Introduction to workflows and life cycles
- Team Data Science Process life cycle
- Other data science life cycles



### Introduction to workflows and life cycles

- What is the life-cycle process in data science?
- Why are the life-cycle processes important?
- Finding knowledge in data



### Team Data Science Process life cycle (**TDSP**)
There are four phases to the **T**eam **D**ata **S**cience **P**rocess

1. Business Understanding [비즈니스 해당 Logic구성]
2. Data Acquisition and Understanding
3. Modeling
4. Deployment

![image](https://user-images.githubusercontent.com/46669551/56256430-a1de3000-6103-11e9-8617-7757763fa608.png)

### Other data science life cycles

- [CRISP-DM](<https://www.nextobe.com/single-post/2018/04/12/CRISP-DM-%EB%B0%A9%EB%B2%95%EB%A1%A0>) : CRISP-DM은 데이터 마이닝을 위한 업계 사이의 프로세스 약자입니다. CRISP-DM 방법론은 데이터 마이닝 프로젝트를 계획하기 위한 체계적인 접근 방식을 제공합니다. 강력하고 검증된 방법론입니다. 강력한 실용성, 유연성과 첨단 비즈니스 문제를 해결하기 위해 분석을 사용할 때의 유용성이 뛰어납니다. 

![image](https://user-images.githubusercontent.com/46669551/56256621-7a3b9780-6104-11e9-9ce8-eee4fe7a160e.png)

- KDD : **데이터 마이닝**(data mining)은 대규모로 저장된 데이터 안에서 체계적이고 자동적으로 통계적 규칙이나 패턴을 찾아 내는 것이다. 다른 말로는 **KDD**(데이터베이스 속의 지식 발견, knowledge-discovery in databases)라고도 일컫는다.

- 각 프로세스 단계는 다음과 같습니다.
  1. 비즈니스 이해 (Business Understanding)
  2. 데이터 이해 (Data Understanding)
  3. 데이터 준비 (Data Preparation)
  4. 모델링 (Modelling)
  5. 평가 (Evaluation)
  6. 배포 (Deployment)



## Lesson 2: Scoring and evaluating models
- Introduction to scoring and evaluation
- Methodologies for scoring and evaluation
- Demonstration: Reviewing the four **TDSP** phases in Azure Machine Learning



### Introduction to scoring and evaluation
- Accuracy
- Precision
- Recall
- F1 score(Harmony means: 조화평균)



### Methodologies for scoring and evaluation (TDSP의 3단계)
- Modeling phase of TDSP
- Repeated testing throughout the model’s lifetime



### Demonstration: Reviewing the four TDSP phases in Azure Machine Learning
In this demonstration, you will review the four TDSP phases:

- Business Understanding
- Data Acquisition and Understanding
- Modeling
- Deployment

## Lesson 3: Using regression algorithms
- Introducing regression
- Ordinal regression
- Linear regression
- Bayesian linear regression
- SVM ordinal regression
- Neural network regression
- Decision forest regression
- Boosted decision tree regression
- Poisson regression
- Fast forest quantile regression
- Evaluating regression-based models



### Introducing regression

- Regression [예측방법 중 한가지]
- Overfitting [targeting이 너무 세밀하게 되어 현재 데이터의 accuracy는 높을 수 있으나, 다른값이 들어올 경우 model에 맞지 않을 가능성이 매우 높아진 경우]
- L1 and L2 regularization [기존 모델에 인자 값을 주어서 Overfitting된 model을 일반화하여 flexible하게 최적화 하는 방법]



### Ordinal regression

- Machine Learning has an ordinal regression task to predict ranked values
- This task is pre-configured with the required parameters for solving a ranking problem



### Linear regression

- Provides a simple form of regression, which involves scoring a single output
- Creates a good starting point
- Can be used to work out missing data values
- Can solve problems such as how likely is it that height predicts weight



### Bayesian linear regression 

> [범위를 벗어나는 데이터를 estimate의 기능을 사용하여 기존의 Linear regression보다 flexible하게 처리 가능하게 하는 기능]

- Provides a likelihood estimator
- Offers a more flexible approach to regression

### SVM ordinal regression

> [많은 데이터를 처리 할 수 있으며, 선형 또는 비선형의 형태에서 기준 축을 만들어 주는 기능을 한다]

- SVM is for large datasets
- It targets regression problems for scoring
- It can be used in **conjunction** with other algorithms to analyze large datasets [결합 문제]

### Neural network regression

- Uses a neural network to address regression problems
- Good for scoring
- Requires a labeled dataset

### Decision forest regression

- Non-parametric tests
- Result aggregated from a set of decision trees

### Boosted decision tree regression

> [회귀, 분류에서 사용이 되며 어떠한 기분에 있어서 clustering할때에 사용된다]

- Boosting is based on a series of decision trees
- Best tree is selected, depending on a loss function
- Smallest loss is selected

### Poisson regression

- Poisson regression looks at counts, not data values
- Bear the data in mind when interpreting the results

### Fast forest quantile regression

- The Fast Forest Quantile Regression module predicts values on a distribution
  - Example: range of prices

- Requires a labeled dataset

### Evaluating regression-based models

- **Descriptive statistics** are important:

  [Descriptive statistics] : 기술 통계 - 수집한 데이터를 요약 묘사 설명하는 통계기법

  - R2
  - F statistic
  - P for probability 

## Lesson 4: Using neural networks

> 신경망 모델을 사용한다 [가중치를 적용, Hidden Layer가 생성, Sigmoid 함수를 활용하였음(0~1)]
>
> Supervised Learning[지도학습] , Unsupervised Learning[비지도학습]이 존재

- Introduction to neural networks
- Use cases for neural networks
- Demonstration: Using a sample application based on a neural network

### Introduction to neural networks

- Interesting machine learning model
- Inspired by the human brain
- Used to make predictions from a dataset
- Can be time-consuming to run
- Easy to implement in Machine Learning, but can be difficult to analyze
- Training is an iterative process

### Use cases for neural networks

- Useful for making business decisions
- Excellent for regression and classification 
- Good at assessing likelihood and credit-scoring

### Demonstration: Using a sample application based on a neural network
![image](https://user-images.githubusercontent.com/46669551/56263187-ef1acb80-611c-11e9-91c6-72dee0646c5e.png)

In this demonstration, you will see how to:

- Open an income dataset and select metadata
- Remove duplicate rows
- Clip values for an upper age threshold of 75
- Verify the data clipping
- Split data into training and test datasets
- Add the Two-Class Neural Network module
- Evaluate the model

![image](https://user-images.githubusercontent.com/46669551/56263448-e37bd480-611d-11e9-98c8-9ce0a99f4892.png)

![image](https://user-images.githubusercontent.com/46669551/56263468-fd1d1c00-611d-11e9-847a-2826092a4688.png)

![image](https://user-images.githubusercontent.com/46669551/56263494-1756fa00-611e-11e9-8acc-ee00d7d3d46b.png)

> 교재의 내용은 Clean Missing Value가 없으나 실행함. 
>
> 실행전 F1 Score 는 0.657, 실행후 F1 Score는  0.668 로 소폭 증가하였다. 
>
> 그러나 모델의 성능은 그닥...

Two-class Boosted Decision tree 를 사용하면

![image](https://user-images.githubusercontent.com/46669551/56263701-f2af5200-611e-11e9-81e7-82d5f7e0807f.png)

![image](https://user-images.githubusercontent.com/46669551/56263752-2c805880-611f-11e9-9fd3-cf90af87af7c.png)

> 위의 신경망 Model보다 더 높은 정확도와 정밀도를 나타내며, Model의 성능 또한 뛰어남. 
>
> 그래프 또한 Left Top 방향에 더욱 가깝다.
>
> 그러나 Recall (재현율)은 두 모델 모두 0.688로 같다.

> 추가>
>
> ![image](https://user-images.githubusercontent.com/46669551/56264054-3bb3d600-6120-11e9-9a0d-4dd881e65209.png)

## Lab: Building Machine Learning models

- Exercise 1: Use regression analysis in Machine Learning Studio
- Exercise 2: Use neural networks in Machine Learning Studio

>Lab Scenario
>
>You work as a data scientist for Adatum Consultants, a company that provides
>machine learning services and advice for a range of clients. One of your
>clients is looking to use machine learning for insights from operational data
>sources throughout their organization. Your first thought is that models based
>on some form of regression or neural networks may be useful.
>
>You are working with a team of business analysts who will be building the final
>models. You are following the recommended steps of the Team Data Science Process.
>As part of the TDSP, you will perform some model development steps, as per the
>Modeling phase of the process. You will be using Machine Learning with this
>team, so, to familiarize yourself with this environment, you need to explore
>the steps required to use regression and neural network algorithms in Machine
>Learning Studio. 

> Lab Review
>
> - How important is it to understand the various regression algorithms before starting
>   to build a model? Why?
> - In your organization, can you think of any application that would benefit from
>   an approach based on neural networks?

![image](https://user-images.githubusercontent.com/46669551/56264990-3b690a00-6123-11e9-84e6-953d7e769248.png)

![image](https://user-images.githubusercontent.com/46669551/56265035-66535e00-6123-11e9-8fa3-1f67a2f17cbc.png)

> The Red Line appears result of Two-class Neural Network model
>
> The Blue Line appears result of Two-class Boosted Decision Tree model 
>
> Through the graph we would be recognized the Two-class Boosted Decision Tree model better than the other model.  

![image](https://user-images.githubusercontent.com/46669551/56265072-79662e00-6123-11e9-8b54-86441acac4ea.png)

> Evaluated Result of Linear Regression 
>
> ![1555481875361](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1555481875361.png)



![image](https://user-images.githubusercontent.com/46669551/56266407-16769600-6127-11e9-9696-f6d3d335a26e.png)

![image](https://user-images.githubusercontent.com/46669551/56266458-36a65500-6127-11e9-88b4-cb6b1fe611fa.png)

![image](https://user-images.githubusercontent.com/46669551/56266504-5473ba00-6127-11e9-89b1-b1ca5662436e.png)

![image](https://user-images.githubusercontent.com/46669551/56266551-740ae280-6127-11e9-8190-bed765ecc9e4.png)

> Accuracy Value (F1 Score) 가 0.9775 로 측정되며 이 수치는 매우 높은 것이다. 
>
> 따라서 이 모델은 매우 성공한 Model로 볼 수 있다. 