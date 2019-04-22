# Module 7 Using Classification and Clustering with Azure Machine Learning Models
## Module Overview

- Using classification algorithms
- Clustering techniques
- Selecting algorithms



## Lesson 1: Using classification algorithms
- Understanding classification
- Two-class classification
- Multiclass classification
- Evaluating classification-based models
- Demonstration: Using Azure ML Studio modules for classification

### Understanding classification

- Classification places individual items into categories
- Classification can be two-class classification or multiclass classification

### [Two-class classification](<https://docs.microsoft.com/ko-kr/azure/machine-learning/studio/algorithm-choice>)

- Linear Regression: Yes or No
- Nonlinear Regression: A or B or C ... 

![image](https://user-images.githubusercontent.com/46669551/56266794-0c08cc00-6128-11e9-9c65-3ef3ff589932.png)

![image](https://user-images.githubusercontent.com/46669551/56266814-188d2480-6128-11e9-8180-4c91c4ff2372.png)

![image](https://user-images.githubusercontent.com/46669551/56266837-217df600-6128-11e9-86dd-0d2572bde594.png)

![image](https://user-images.githubusercontent.com/46669551/56266852-2b075e00-6128-11e9-86a7-636dcb8caf22.png)

Two-class classification

- Two-class logistic regression
- Two-class decision forest
- Two-class decision jungle
- Boosted decision tree
- Two-class neural network
- Averaged perception
- Support vector machine
- Locally deep support vector machine
- Bayes' point machine

### [Multiclass classification](<https://docs.microsoft.com/ko-kr/azure/machine-learning/studio/algorithm-choice>)

- Multiclass logistic regression
- Multiclass decision forest
- Multiclass decision jungle
- Multiclass neural network
- One-vs-all

### Evaluating classification-based models
- Two-class or multiclass?
- Use Azure Machine Learning: [Algorithm Cheat Sheet](<https://docs.microsoft.com/ko-kr/azure/machine-learning/studio/algorithm-cheat-sheet>)
- Test models against data

### Demonstration: Using Azure ML Studio modules for classification
In this demonstration, you will see how to:

- Use Azure Machine Learning Studio to create a classification model

## Lesson 2: Clustering techniques

- Understanding clustering
- The K-Means clustering algorithm
- Anomaly detection
- Demonstration: Using clustering in Azure ML Studio

### Understanding clustering

![image](https://user-images.githubusercontent.com/46669551/56266936-66a22800-6128-11e9-9367-18f18ddd3380.png)

### The K-Means clustering algorithm

- Items are added to the cluster with the closest mean value
- Mean value affects membership and membership affects mean value—therefore several iterations are required
- After the K-Means algorithm, data should go through the Train Clustering Model module or the Sweep Clustering module

### Anomaly detection

- Anomaly detection searches for unusual values
- Useful for fraud detection
- Can be difficult to train due to limited anomalies in training data
- Machine Learning has two algorithms:
  - One-class support vector machine
  - PCA-based anomaly detection

### Demonstration: Using clustering in Azure ML Studio

In this demonstration, you will see how to:

- Use clustering in Azure Machine Learning Studio

## Lesson 3: Selecting algorithms

- An overview of choosing Machine Learning algorithms
- The Algorithm Cheat Sheet
- Evaluating a model

### An overview of choosing Machine Learning algorithms
1. Narrow down choice of algorithms with Algorithm Cheat Sheet

2. Test algorithms with historic data

### The Algorithm Cheat Sheet

Brain storming 을 통하여 전체적 구성을 생각한 후 Cheat Sheet를 활용하여 적절한 분석 모델을 찾기 

![image](https://user-images.githubusercontent.com/46669551/56267051-b08b0e00-6128-11e9-9817-6b9570e203e1.png)

![image](https://user-images.githubusercontent.com/46669551/56267073-c0a2ed80-6128-11e9-80f6-e85b2d0bead8.png)

### Evaluating a model

- **Partition** your **data** for **training** and **testing**
- Use a module to **evaluate your model**

## Lab: Using classification and clustering with Machine Learning models
- Exercise 1: Apply Azure ML Studio modules for classification
- Exercise 2: Working with K-Means clustering

> Lab Scenario
>
> You work as a data scientist for Adatum Consultants, a company that provides
> machine learning services and advice for a range of clients. Some of your
> clients are looking to use machine learning for insights from operational data
> sources throughout their organizations.

![image](https://user-images.githubusercontent.com/46669551/56329930-cd732000-61c0-11e9-8509-c6e98fc1d02c.png)

![image](https://user-images.githubusercontent.com/46669551/56329908-b7655f80-61c0-11e9-8253-5a2294e1650a.png)

![image](https://user-images.githubusercontent.com/46669551/56329946-e976c180-61c0-11e9-8190-4bb3a26cf44c.png)

![image](https://user-images.githubusercontent.com/46669551/56329829-6ce3e300-61c0-11e9-8f9e-0a95444fea9b.png)

> Lab Review
>
> •In this lab, you used classification and clustering to group individual data
> items.

### Module Review and Takeaways

In this module, you learned how to:

- Apply classification algorithms
- Use clustering techniques
- Choose machine learning algorithms