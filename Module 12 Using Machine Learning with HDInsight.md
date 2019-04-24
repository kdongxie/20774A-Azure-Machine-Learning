# Module 12 Using Machine Learning with HDInsight
## Module Overview

- Introduction to HDInsight
- HDInsight clusters
- HDInsight and machine learning models

## Lesson 1: Introduction to HDInsight

- HDInsight and big data
- Introducing Azure HDInsight
- HBase on HDInsight
- Storm on HDInsight
- Demonstration: Provisioning a Hadoop cluster on HDInsight

### HDInsight and big data

- Big data:
  - Volume
  - Variety
  - Velocity 



- Processing big data:
  - Batch processing
  - Batch processing and machine learning
  - Real-time streaming
  - Real-time streaming and machine learning
  - Simple statistical analysis and visualizations

### Introducing Azure HDInsight

- Azure HDInsight:
  - Apache Hadoop running on Microsoft Azure
  - HDP Hadoop instances running on Azure virtual machines



- HDFS in Azure:
  - Azure storage account [가격이 저렴함]
  - Azure Data Lake

### HBase on HDInsight

- Apache HBase: [관계가 없는 데이터, 테이블의 틀만을 만들어 쓴다(Join불가능), 기본 구조만을 사용하기 때문에 작업이 빠르다. 그러나 불편하고 규격화 하기 힘듬.data node를 통해 각각 Table별 관리가 가능]

  Hadoop에서 Big Table을 사용할 경우가 있음. 

  - **Nonrelational table** store built on Hadoop technologies
  - Distributes workload across Hadoop cluster nodes
  - Typically used to store large databases of unstructured and semi-structured data that needs random read/write



- Uses NoSQL:[Document base, SQL Query 쓰지 않음, MongoDB가 대표적임]
  - Cannot use regular queries
  - Stores data in tables as key-value pairs
  - Each key can have multiple columns
  - Each column can contain multiple updates
  - Values of a key are arranged into column families 

### Storm on HDInsight

- **Apache Storm** is designed for working with a live feed of **streaming data** 
- Azure 의 ASA를 사용하면 쉽게 처리가 가능하다.



- Typical scenarios include: 
  - The Internet of Things 
  - Fraud detection
  - Social analytics
  - Extract, transform, and load (ETL)
  - Network monitoring
  - Search
  - Mobile engagement

### Demonstration: Provisioning a Hadoop cluster on HDInsight
In this demonstration, you will see how to:

- Start a cluster configuration
- Configure basic cluster details
- Configure cluster storage
- Configure cluster size and create the cluster

## Lesson 2: HDInsight clusters

- Hadoop clusters in HDInsight
- HBase clusters in HDInsight
- Storm clusters in HDInsight
- Deploying HDInsight clusters
- Demonstration: Managing a Hadoop cluster on HDInsight

### Hadoop clusters in HDInsight

- Hadoop cluster
  - Name nodes—usually two for redundancy
  - Data nodes—as many data nodes as required for the volume of data



- Hadoop Distributed File System (HDFS)
  - Common shared file system striped across the data nodes



- YARN
  - Coordinates all the work performed on the cluster

### HBase clusters in HDInsight

- HBase Storage
  - Data is stored on HDFS in Azure storage
  - Do not use an HBase storage account for other services



- HBase compute
  - HBase uses a lot of CPU and memory 
  - Do not use an HBase cluster for other Hadoop applications such as Hive and Spark



- Use a VPN on an HBase cluster for on-premises applications to connect directly to a cloud instance of HBase

### Storm clusters in HDInsight

- Storm on HDInsight
  - SLA of 99.9%



- Reliability
  - Nimbus node is responsible for assigning tasks to worker nodes through Zookeeper
  - Storm on HDInsight deploys two Nimbus nodes for high availability
  - Zookeeper nodes manage communication between the active Nimbus node and worker threads



- Scalability
  - Change the number of nodes in a cluster at any time

### Deploying HDInsight clusters

- Cluster configuration:
  - Cluster type
  - Operating system
  - HDInsight version
  - Cluster tier
  - Resource group
  - Login user
  - Storage
  - Cluster location

### Demonstration: Managing a Hadoop cluster on HDInsight
In this demonstration, you will see how to:

- View the cluster dashboard
- Connect to the cluster using SSH
- Use SSH to browse HDFS

1. HDInsight 를 Putty를 통해 접속.

2. HDFS file system 의 root folder를 확인 

   ```
   hdfs dfs -ls /
   ```

3. HDFS file system의 example folder안의 내용을 확인

   ```
   hdfs dfs -ls /example
   ```

4. HDFS file system의 example folder의 하위의 sample text files를 확인

   ```
   hdfs dfs -ls /example/data/gutenberg # 3개의 text files확인
   ```

5. ulysses.txt files을 확인

   ```
   hdfs dfs -text /example/data/gutenberg/ulysses.txt
   ```



## Lesson 3: HDInsight and machine learning models
- Introduction to Spark
- Working with data in Spark
- Exploring data with Spark SQL
- Using **Spark with machine learning**
- Using **MapReduce with machine learning**
- Demonstration: Working with HDInsight

### Introduction to Spark

- Apache Spark
  - Fast, general-purpose computation engine that supports in-memory operations
  - Lazy evaluation model
  - Adapts to large volumes of data and multiple cores, including on hyperthreaded CPUs
  - Manages cluster and jobs with its own cluster manager and **does not depend on YARN**

### Working with data in Spark

- Resilient distributed dataset (RDD)
  - Collection of items with own data properties



- Working with Spark
  - **Java**, **Python**, and **Scala APIs**
  - **Jupyter notebooks for Spark**



- Working with RDDs
  - Spark context
  - Transformations
  - Actions

### Exploring data with Spark SQL

- Dataframes
  - Load data directly
  - Convert existing RDDs



- Querying dataframes
  - Use standard SQL
  - Specify or infer the schema

### Using Spark with machine learning

Spark includes the MLlib machine learning library, which is:

- Built on Spark and will use existing Spark infrastructure and projects
- Straightforward, but powerful
- Compatible with many tools and languages

### Using MapReduce with machine learning
- Map phase
  - Split the data into key and value pairs



- Reduce phase
  - Take each unique key and operate only on its values



- MapReduce engine
  - Original Hadoop engine
  - **Hive and Pig include the Tez engine**

### Demonstration: Working with HDInsight
In this demonstration, you will see how to:

- Use the Python Spark shell
- Run a MapReduce job

1. SSH console window를 통해 pyspark를 실행한다.

   ```python
   pyspark
   ```

   ```python
   Welcome to
         ____              __
        / __/__  ___ _____/ /__
       _\ \/ _ \/ _ `/ __/  '_/
      /__ / .__/\_,_/_/ /_/\_\   version 2.3.2.2.6.5.3008-11
         /_/
   
   Using Python version 2.7.12 (default, Nov 12 2018 14:36:49)
   SparkSession available as 'spark'.
   ```

   

2.  입력란이 '>>>' 형태로 변했느지 확인

3. RDD 를 만들시 수행

   ```python
   txtRdd = sc.textFile('/example/data/gutenberg/ulysses.txt')
   ```

4. 'txtRdd'RDD파일의 count mathod를 수행시킨다. 

   ```python
   txtRdd.count() #33055
   ```

5. filtering을 통해 'good'을 가지고 있는 line의 개수를 구한다.

   ```python
   txtRdd = txtRdd.filter(lambda x: 'good' in x)
   txtRdd.count() #289
   ```

6. Spark Shell 을 종료한다.

   ```python
   quit()
   ```



1. Hadoop을 통한 MapReduce 수행하기

   ```python
   ls /usr/hdp/current/hadoop-mapreduce-client
   ```

2. Head node의 sample jar 의 목록을 볼 수 있다.

3. MapReduce 기능 list 중 hadoop-mapreduce-examples.jar file을 확인

   ```python
   hadoop jar /usr/hdp/current/hadoop-mapreduce-client/hadoop-mapreduce-examples.jar
   ```

4. wordcount function 을 사용하여 result file생성

   ```python
   hadoop jar /usr/hdp/current/hadoop-mapreduce-client/hadoop-mapreduce-examples.jar wordcount /example/data/gutenberg/ulysses.txt /example/result
   ```

5. result file확인하기

   ```python
   hdfs dfs -ls /example/result # part-r-00000 파일을 확인할 수 있다.
   ```

6. part-r-00000 file을 확인한다.

   ```python
   hdfs dfs -text /example/result/part-r-00000 
   #각 word별 count의 값이 호출 됨을 알 수 있다.
   ```

   

## Lab: Using machine learning with HDInsight
- Exercise 1: Provision an HDInsight cluster
- Exercise 2: Use HDInsight for MapReduce and Spark jobs

위 Demonstration 3개와 이어서 진행 한다.

1. pyspark 를 실행한다.

   ```python
   pyspark
   ```

2. example 경로 밑에 있는 davinci.txt 파일을 호출한다.

   ```python
   alltxt = sc.textFile("/example/data/gutenberg/davinci.txt")
   ```

3. 전체 line의 수 를 count한다

   ```python
   alltxt.count()
   ```

4. 첫번째 line을 출력해본다

   ```python
   alltxt.first()
   ```

5. 전체 문장에서 'Italy'를 포함한 문장만을 뽑아낸다.

   ```python
   filtertxt = alltxt.filter(lambda alltxt: "Italy" in alltxt)
   ```

6. 필터링 된 문장의 수를 출력한다.

   ```python
   filtertxt.count()
   ```

7. 필터링 된 문장을 호출한다.

   ```python
   filtertxt.collect()
   ```

8. pyspark 를 종료한다

   ```python
   quit()
   ```



1. Python Script를 Spark에서 사용하여 MapReduce작업을 수행한다. 

2. SparkCount.py 를 편집한다.

   ```python
   nano SparkCount.py
   ```

   -  다음을 입력해 준다.

   ```python
   # import and initialize Spark context
   from pyspark import SparkConf, SparkContext
   cnf = SparkConf().setMaster("local").setAppName("SparkCount")
   sc = SparkContext(conf = cnf)
   # use Spark to count words
   alltxt = sc.textFile("/example/data/gutenberg/outlineofscience.txt")
   words = alltxt.flatMap(lambda alltxt: alltxt.split(" "))
   counts = words.map(lambda word: (word, 1)).reduceByKey(lambda a, b: a +b)
   # store results
   counts.saveAsTextFile("/example/spark_output")
   ```

3. CTRL+X 그리고 Y 이후 Enter를 입력하여 console 창을 빠져 나온다.

4. SparkCount.py를 입력시켜준다.

   ```py
   spark-submit SparkCount.py
   ```

5. scripts를 수행하여 나온 결과를 확인한다.

   ```python
   hdfs dfs -ls /example/spark_output
   ```

6. 결과 text파일을 확인한다.

   ```python
   hdfs dfs -text /example/spark_output/part-00000
   ```

7. Azure portal의 Hadoop Cluster 의 blob storage의 container 안의 folder중 example/spark_output/part-00000 를 내려받아 확인해 본다.

![image](https://user-images.githubusercontent.com/46669551/56546982-f3306880-65b6-11e9-8fdc-7066f3d90789.png)

>Lab Scenario
>
>You work as a data scientist for Adatum Consultants, a company that provides machine learning services and advice for a range of clients. One of your clients is planning the deployment of HDInsight to support large-scale big data analysis and machine learning applications.
>
>You are working with a team of business analysts and, as part of your planning, you will deploy an HDInsight cluster and then use this cluster to evaluate MapReduce and Spark operations.

> Lab Review
>
> - In your own organization, why might you choose Windows over Linux as the operating
>   system for an HDInsight cluster?
> - True or false: To create a basic HDInsight cluster, you select Hadoop as the
>   cluster type.