# Module 8 Using R and Python with Azure Machine Learning
## Module Overview

- Using R
- Using Python
- Incorporating R and Python into Machine Learning experiments

## Lesson 1: Using R

개발 언어가 아닌 데이터 처리에 주 목적을 갖고 있는 Script언어

- Why use R for machine learning?
- Common R types and data structures
- R operators
- R programming constructs
- Creating functions in R
- Incorporating R packages and libraries
- Visualizing data in R
- Working with dates and times in R
- Demonstration: Processing and visualizing data in R

### Why use R for machine learning?

- Statistical analysis comprises three common tasks:
  - Data transformation
  - Data visualization
  - Data modeling

- R provides an array of packages to help you perform these tasks
- R also provides programming constructs to build a workflow of operations
- R is interactive; you can quickly prototype your operations\
- R packages can be written using compiled languages, for speed

### Common R types and data structures

- Atomic types:
  - numeric
  - logical
  - character
  - complex

- Factor types:

  - Values constrained to a set of values

  - Can be ordered or unordered

- All types can be NA

- Numerics can be NaN

- Vectors:
  - 1-dimensional
  - Values must have same type

- List

  - 1-dimensional

  - Values can have different types

- Matrix
  - 2-dimensional, same type

- Array
  - N-dimensional, same type

- Dataframe
  - List of vectors

### R operators

- Operators act on the individual elements in a structure
  - Operands must have the same size and dimensions
  - Results are a structure with the same size and dimensions

```R
c(1, 2) + c(3, 4) ->  y
 y

 # Results
 4 6
```

- Numeric:
  - +, -, *, /, %/%, %%, ^

- Relational:
  - <, >, <=, >=, == !=

- Logical:
  - &, | , !

- Assignment:

  - ->, <-

  - Avoid =

- Text functions:
  - substr, grep, strsplit, paste, toupper, tolower

### R programming constructs

- Decision making
  - *if-else*

```R
if (a < 10) {
  a <- a * 2
 } else {
  a <- a ^ 2
 }
```

- Looping

  - *for*

  - *while*

```R
a <- 0
 while (a < 10) {
  print(a)
  a <- a + 1
 }
```

- Vectorized functions

 For example:

​	- *sum*

​	- *ifelse*

```R
 x <- c(1, 23, 5, 14, 2, 16)
 ifelse(x < 10, x * 2, x ^ 2)
```

### Creating functions in R

- Functions enable you to reuse R code in different contexts
- Functions can take parameters and return a result
- Any variables created in a function are destroyed when the function finishes
- Parameters can be given default values
- Functions are data objects; other functions can use them as parameters

```R
# Function 생성하기
isNegativeNum <- function(n) {
  if (!is.numeric(n)) {
    return (NA)
  } else if (n < 0) {
    return (TRUE)
  } else {
    return (FALSE)
  }
}
```

### Incorporating R packages and libraries
- R has many packages available in CRAN
- Commonly used packages include:
  - stats
  - rodbc
  - **tidyr**
  - readr
  - **ggplot2** [대부분의 데이터 Vizualize처리가 가능하다]
  - **DBI**
  - lubridate
  - modelr
  - **dplyr**
  - tibble

```r
library(dplyr)

myFrame %>%
  filter(inStock == TRUE) %>%
  select(productName, price, size) %>%
  group_by(size) %>%
  summarize(mean(price))
```



### Visualizing data in R

- Use the **ggplot2** package to generate **graphs and charts**

- ggplot2 charts consist of:
  - Data
  - Aesthetic mappings
  - Geometric objects (geoms)
  - A coordinate system
  - Statistical transformations (stats)
  - Facets

- You can create composite charts by overlaying geometries

### Working with dates and times in R

- R provides the **Date** datatype for handling dates
  - Internally, dates are stored as the number of days since January 1, 1970
  - **<u>There is no built-in time datatype</u>**

- The **lubridate** library <u>provides extended support for dates and times</u>
  - Formatting
  - **POSIXct** and **POSIXlt** for <u>handling dates and times</u> 

- Use the **xts** library to <u>manage time-series data</u>
  - Data is indexed and organized by datetime values
  - You can query data by date and time more easily

### Demonstration: Processing and visualizing data in R
- Import movie data
- Find the average rating for each movie
- Find out how frequently users post ratings

``` R
# Download the movie ratings and IMDB movie titles from the sample datasets collection
library("AzureML")
ws <- workspace()
ratings <- download.datasets(ws, "Movie Ratings")
titles <- download.datasets(ws,"IMDB Movie Titles")
```

```R
# Examine the first few rows in each dataset
head(ratings) 
head(titles)
```

![image](https://user-images.githubusercontent.com/46669551/56332461-6313ad00-61cb-11e9-9494-e6937d604ac3.png)

```R
# Merge the two datasets over the movie id
movieData <- merge(ratings, titles, by.x = "MovieId", by.y = "Movie.ID")
head(movieData)
```

![image](https://user-images.githubusercontent.com/46669551/56332499-7e7eb800-61cb-11e9-80ec-b33afd520ee1.png)

```R
# What is the average rating for each movie?
library(dplyr)

select(movieData, MovieId, Movie.Name, Rating) %>%
  group_by(MovieId) %>%
  summarize("MeanRating" = mean(Rating)) %>%
  arrange(desc(MeanRating))
```

![image](https://user-images.githubusercontent.com/46669551/56332520-922a1e80-61cb-11e9-89c9-f72b89988df5.png)

```R
# Install the lubridate and xts packages
# 시간 날짜를 다루는 패키지
install.packages("lubridate")
library(lubridate)

# 시계열 데이터 객체 생성에 유용
install.packages("xts")
library(xts)
```

```R
# 출력 
Installing package into ‘/home/nbuser/R’
(as ‘lib’ is unspecified)
also installing the dependency ‘stringr’

Warning message in install.packages("lubridate"):
“installation of package ‘lubridate’ had non-zero exit status”
Attaching package: ‘lubridate’

The following object is masked from ‘package:base’:

    date

Installing package into ‘/home/nbuser/R’
(as ‘lib’ is unspecified)
Loading required package: zoo

Attaching package: ‘zoo’

The following objects are masked from ‘package:base’:

    as.Date, as.Date.numeric


Attaching package: ‘xts’

The following objects are masked from ‘package:dplyr’:

    first, last

The following object is masked from ‘package:AzureML’:

    endpoints
```

``` 
# How frequently do viewers post ratings?
# Step 1: Convert the dataset into an xts object (the Timestamp is a POSIXct datetime)
xtsMovieData <- xts(movieData[c("MovieId", "UserId", "Rating", "Movie.Name")], order.by=as.POSIXct(movieData$Timestamp, origin = "1970-01-01"))
head(xtsMovieData)
```

``` R
# 출력 값
                    MovieId   UserId  Rating
2013-02-28 14:38:27 "2171847" "18507" " 6"  
2013-02-28 14:43:44 " 444778" "16458" " 8"  
2013-02-28 14:47:18 "1411238" " 3136" " 6"  
2013-02-28 14:58:23 "1496422" "21655" " 7"  
2013-02-28 15:00:53 " 118799" "16777" " 5"  
2013-02-28 15:04:39 " 338013" "16777" " 4"  
                    Movie.Name                                    
2013-02-28 14:38:27 "Dead Mine (2012) "                           
2013-02-28 14:43:44 "Mah nakorn (2004) "                          
2013-02-28 14:47:18 "No Strings Attached (2011)"                  
2013-02-28 14:58:23 "The Paperboy (2012)"                         
2013-02-28 15:00:53 "La vita \x8a bella (1997) "                
2013-02-28 15:04:39 "Eternal Sunshine of the Spotless Mind (2004)"
```

``` R
# Step 2: Count the number of ratings posted per day
ratingsPerDay <- apply.daily(xtsMovieData, function(data) { nrow(data$Rating) })
head(ratingsPerDay)
# apply 함수 syntex
# apply(array, margin, fun)
# 해석 : apply(object, direction, function to apply)
# 적용방향 - 1:가로방향, 2: 세로방향
# 예시 : apply(a, 2, max), apply(a, 1, max)
```

![image](https://user-images.githubusercontent.com/46669551/56333221-3f059b00-61ce-11e9-8bf6-0a840555a633.png)

``` R
# 출력 값
                    [,1]
2013-02-28 23:55:41  245
2013-03-01 23:53:21  509
2013-03-02 23:55:52  672
2013-03-03 23:58:43  905
2013-03-04 23:58:42  570
2013-03-05 23:58:38  433
```

``` 
# Install the broom and ggplot2 packages
install.packages("broom")
library(broom)

install.packages("ggplot2")
library(ggplot2)
```

``` R
# 출력 값
Installing package into ‘/home/nbuser/R’
(as ‘lib’ is unspecified)
also installing the dependency ‘generics’

Installing package into ‘/home/nbuser/R’
(as ‘lib’ is unspecified)
Warning message in install.packages("ggplot2"):
“installation of package ‘ggplot2’ had non-zero exit status”
```

```R
# Step 3: Graph the results
graphData <- tidy(ratingsPerDay)
graphData$index <- as.POSIXct(graphData$index,  origin="1970-01-01")

options(repr.plot.width=15, repr.plot.height=4)
ggplot(graphData, aes(x = index, y = value)) +
  ggtitle("Ratings Posted Per Day") +
  xlab("Date") +
  ylab("Number of Ratings") +
  geom_line(color = "blue")
```

![image](https://user-images.githubusercontent.com/46669551/56332639-1b415580-61cc-11e9-9d5e-10df91caeb22.png)





## Lesson 2: Using Python

개발적 요소와 분석의 요소를 고루 갖춘 언어이다.

- Why use Python for machine learning?
- Common Python **types** and **data structures**
- Python operators and **functions**
- Python **programming constructs**
- Creating Python functions
- Incorporating Python libraries
- Visualizing data with Python
- Demonstration: Processing and visualizing data with Python

### Why use Python for machine learning?
- Fully-fledged programming language
- Portable, and runs on many different operating systems
- Frequently used to provide the *glue* to integrate components developed in different languages
- Excellent for transforming data between formats
- More complex than R; it supports advanced OO features
- Packages developed in other compiled languages can be easily incorporated

### Common Python types and data structures
- Numerics:
  - int, long
  - float
  - Complex

- Booleans
  - True/False

- Sequences:
  - strings (immutable)
  - byte arrays (raw binary data)
  - tuples (fixed length, immutable)
  - lists (variable length, mutable)

- Dicts:
  - Key/value pairs

- Sets
  - Unordered collections
  - Support set operations
  - Can be immutable (frozen) and mutable

- None
  - Indicates value unknown
  - Can be applied to any type

### Python operators and functions

- Numeric
  - +, -, *, /, //, %, **

- Attempts to divide by zero always result in an exception
  - // and % not available for complex numbers

- Relational:

  - <, >, <=, >=, == !=

  - Effects on non-numeric data depend on how the type is implemented

- Logical:
  - **and**, **or**, **not**

- Sequence:

  - **in**, **not** **in**, **+**, **[n]**, **[n:m]**, **len**, **minb** **max**, **count**

  - Mutable – assignment, **del**, **append**, **clear**, **insert**, **pop**, **remove**, **reverse** 

- Set:

  - &, | , -, <, >, ==, !=

  - Mutable – **add**, **remove**, **clear**

- Dict:
  - d[k] = v

### Python programming constructs

- Indentation is important
- Decision making
  - *if-elif-else*

```python
a = 99
 if a < 100:
    a = a + 1
 else:
    a = a - 1
 print(a) 
```



- Looping
  - **for**
  - **while**

- Exception handling:
  - **try**
  - **except**

``` python
for i in customers:
    customers[i] = "Customer: " + customers[i]
    print(customers[i])
```

### Creating Python functions

- Functions enable you to reuse Python code
- Functions can take parameters and return a result
  - If you want to return more than one result, return a sequence

- Parameters can be given default values
- Object-based parameters are passed by reference
- Functions should implement exception handling to capture unexpected input

```python
def swap(a, b):
     b, a = a, b     
     return (a, b) 
# 함수를 지정하는데 JAVA와 다르게 return type이 꼭 필요한 사항은 아니다.
```

### Incorporating Python libraries

- Python.org maintains a collection of open source packages in the PyPI (Python Package Index)
- Common packages useful for machine learning include:
  - **datetime**
  - **numpy**
  - **pandas**
  - SciPy 
  - **Scikit-Learn**
  - **Tensorflow**
  - **Matplotlib**
  - **Seaborn**

```python
!pip install pandas
Import pandas as pd

productData = pd.DataFrame(
 {'Name': ['Widget', 'Flange', 
           'Sprocket','Grommit'],
  'Price': [13.25, 15.80, 7.25, 0.10],
  'NumSold': [100, 10, 55, 125]}, 
   index = ['P1', 'P2', 'P3', 'P4'])
```

### Visualizing data with Python

- The **matplotlib library** can work with **NumPy** and **pandas** to **visualize data**

- Use the pyplot interface to matplotlib to generate:
  - **Scatter plots**, Histogram [분포 또는 빈도 확인시 사용]
  - **Line plots**
  - **Bar charts**
  - **Pie charts**
  - **3D charts**
  - and many others

- The seaborn package provides extended functionality and aesthetics

### Demonstration: Processing and visualizing data with Python
- Convert the movie data
- Import movie data
- Find the average rating for each movie
- Find out how frequently users post ratings

[Microsoft Azure Machine Learning Studio](https://studio.azureml.net/) 에서 새로운 dataset을 만든다.

![image](https://user-images.githubusercontent.com/46669551/56337305-88121b00-61df-11e9-9e99-50e5c8ad8fe6.png)

```R
# R Scripts
# Map 1-based optional input ports to variables
dataset <- maml.mapInputPort(1) # class: data.frame
maml.mapOutputPort("dataset")
```

Python 3 notebook을 사용하여 선행한 Demonstration의 파일과 R을 통해 만든 dataset을 호출한다.

```python
# Download the movie ratings and IMDB movie titles from the sample datasets collection
from azureml import Workspace

ws = Workspace()
dsRatings = ws.datasets['Movie Ratings']
ratings = dsRatings.to_dataframe()

dsMovies = ws.datasets['Movie Names']
movies = dsMovies.to_dataframe()
```

데이터가 잘 들어왔는지 확인한다.

``` 
# Examine the first few rows in each dataset
print(ratings.head())
print()
print(movies.head())
```

```python
   UserId  MovieId  Rating   Timestamp
0       1    68646      10  1381620027
1       1   113277      10  1379466669
2       2   454876       8  1394818630
3       2   790636       7  1389963947
4       2   816711       8  1379963769

   Movie ID                                     Movie Name
0         8  Edison Kinetoscopic Record of a Sneeze (1894)
1        91                     Le manoir du diable (1896)
2       417                  Le voyage dans la lune (1902)
3       628                        The  s of Dollie (1908)
4       833                      The Country Doctor (1909)
```

데이터의 column명을 바꾸어 준다.

```python
# Rename the columns in the movies dataset and reindex it using the MovieId
# Makes it easier to join the datasets later
movies.rename(columns = {'Movie ID': 'MovieId', 'Movie Name': 'MovieName'}, inplace = True)
movies = movies.set_index('MovieId')
movies.head()
```

``` python
										   MovieName
MovieId	
	  8	Edison Kinetoscopic Record of a Sneeze (1894)
	 91					   Le manoir du diable (1896)
	417					Le voyage dans la lune (1902)
	628						   The s of Dollie (1908)
	833						The Country Doctor (1909)
```

Pandas와 Numpy를 import시켜준다.

``` python
# Import the numpy and pandas modules
import numpy as np
import pandas as pd
```

MovieId 를 기준으로 각 영화들의 평점 평균을 구한다.

```python
# What is the average rating for each movie?
meanRatings = ratings.groupby(['MovieId']).mean()
meanRatings.head()
```

```python

		 UserId	Rating	   Timestamp
MovieId			
	  8	 3296.0	   5.0	1.396981e+09
	 91	 4879.0	   6.0	1.385233e+09
	417	15463.0	   7.0	1.392806e+09
	628	13752.0	   4.5	1.383588e+09
	833	19326.0	   3.0	1.385739e+09
```

두개의 Dataset을 Join하고 필요없는 Column을 지워준다.

```python
# Join the results with the movie data (containing the movie names), and sort by rating
movieData = pd.concat([meanRatings, movies], axis = 1).sort_values(['Rating'], ascending = False)
del movieData['UserId']
del movieData['Timestamp']
movieData
```

```python
		  Rating								    MovieName
MovieId		
 283742	  	10.0						    Inspiracion (2001)
2461862	  	10.0							 The Oscars (2013)
2374002	  	10.0						Minte-ma frumos (2012)
 119843	  	10.0					  Oscar and Lucinda (1997)
 254481	  	10.0						Koi... Mil Gaya (2003)
 254679	  	10.0						 Pesar-e Mariam (1998)
  97202	  	10.0					Dip huet seung hung (1989)
  44860	  	10.0						  The Lusty Men (1952)
  44821	  	10.0	Lambert the Sheepish Lion (1952) Animation
  44517	  	10.0					 The Crimson Pirate (1952)
 497876	  	10.0					   46-okunen no koi (2006)
.
.
. (생략)
```

Timestamp를 활용하고 Timestamp를 Index값으로 사용하기

```python
# How frequently do viewers post ratings?

# Step 1: Reorganize the ratings data to index by the timestamp
ratings.index = ratings.Timestamp
ratings.index = ratings.index.astype('datetime64[s]')
ratings.index
del ratings['Timestamp']
ratings.head()
```

```python
					UserId	MovieId	Rating
Timestamp			
2013-10-12 23:20:27		 1	  68646		10
2013-09-18 01:11:09		 1	 113277		10
2014-03-14 17:37:10		 2	 454876		 8
2014-01-17 13:05:47		 2	 790636		 7
2013-09-23 19:16:09		 2	 816711		 8
```

Timestamp의 기준을 Day로 바꾸어주고 일별 Rating수를 구한다.

```python
# Step 2: Count the number of ratings for each day ('D')
dailyRatings = ratings.resample('D').count()
del dailyRatings['UserId']
del dailyRatings['MovieId']
dailyRatings.rename(columns = {'Rating': 'NumRatings'}, inplace = True)
dailyRatings.head()
```

```python
			 NumRatings
Timestamp	
2013-02-28			245
2013-03-01			509
2013-03-02			672
2013-03-03			905
2013-03-04			570
```

일별 데이터로 바꾼 데이터를 그래프로 그려준다.

```python
#Step 3: Graph the results
import matplotlib.pyplot as plt
get_ipython().magic('matplotlib inline')

plt.rcParams["figure.figsize"] = [12, 9] 
plt.plot(dailyRatings)
```

![image](https://user-images.githubusercontent.com/46669551/56337860-4df64880-61e2-11e9-99ec-6813eda46a1e.png)

Azure Machine Learning의 Convert CSV한 Dataset을 code를 통해 호출 가능하다.

```python
# GENERATE DATA ACCESS CODE 를 활용한다.
from azureml import Workspace
ws = Workspace(
    workspace_id='c50f1d10ff6b41a2a4c4ff8c90af2020',
    authorization_token='It0it9x1MCvxyjfoja6VfrWcaXY3TQRgcRWtbtagS2c46l76p9pWRKbdhkRFrjYRHKKmroatI6fYNizC6ro+1A==',
    endpoint='https://studioapi.azureml.net'
)
experiment = ws.experiments['c50f1d10ff6b41a2a4c4ff8c90af2020.f-id.117f2970345a476a953cfe8fe0f1b49d']
ds = experiment.get_intermediate_dataset(
    node_id='3667fc65-bda8-47b6-a798-4ea12dface54-2271',
    port_name='Results dataset',
    data_type_id='GenericCSV'
)
frame = ds.to_dataframe()
frame.head()
```

```python
	   Movie ID						  			   Movie Name
0			  8	Edison Kinetoscopic Record of a Sneeze (1894)
1			 91					   Le manoir du diable (1896)
2			417					Le voyage dans la lune (1902)
3			628						   The s of Dollie (1908)
4			833						The Country Doctor (1909)
```



## Lesson 3: Incorporating R and Python into Machine Learning experiments
- Creating and using Jupyter notebooks
- Exploring a dataset with a Jupyter notebook
- Using R and Python in Machine Learning experiments
- Creating custom modules
- Selecting the appropriate language

### Creating and using Jupyter notebooks
- Jupyter notebooks enable you to:
  - Prototype and test code (R and Python)
  - Document code
  - Run code and capture the output
  - Perform scripted tasks

- A Jupyter notebook consists of a series of *Cells*
  - A cell can hold code, documentation (in Markdown format), or the results of running code (output, graphics, …)

- Be cautious when opening a shared notebook
- You cannot upload a notebook directly into Machine Learning Studio

### Exploring a dataset with a Jupyter notebook
- To explore a dataset generated by a Machine Learning experiment:
  - Right-click the module that generates the dataset
  - Click **Open in new Notebook**
  - <u>Select your programming language</u>

- You can also explore previously saved datasets by using the **Datasets** tab:

  - Select the dataset

  - Click **Open in Notebook**

  - Select your language

- To access shared datasets, you must use **Generate Data Access Code** which creates code that provides authentication tokens

### Using R and Python in Machine Learning experiments
- Use the **Execute R Script** or **Execute Python Script** modules in an experiment
- Input ports provide access to datasets passed in from the workflow
- An output port enables you to pass a dataset back out to the workflow
- Inside a script module, the datasets are presented as dataframes (R and pandas)
- You can import additional script code and packages using the zip input port
- View the results using the Visualize command on the output ports

### Creating custom modules

- A custom module is a prepackaged R function that can be incorporated into an experiment workflow
- Use a custom module when you require detailed control over an operation
- You create an XML description of the input and output datasets, parameters, and any dependencies
- After packaging, you can upload the module to your workspace
  - Custom modules are listed in the Custom folder in the items pane on the experiment canvas
  - Input and output datasets appear as ports in the experiment workflow
  - Parameters appear on the Properties pane

### Selecting the appropriate language

- Language selection is a personal choice, largely dependent on experience and familiarity

- In general:
  - R is favored by data scientists because it expresses statistical concepts concisely
  - R is favored by programmers because it is more general purpose and powerful
  - R has a broader range of statistical packages available
  - Python has a more consistent syntax
  - Both languages can interoperate with each other

- Note: A Machine Learning experiment can incorporate modules written in both languages

## Lab: Using R and Python with Machine Learning
- Exercise 1: Preparing the lab

![image](https://user-images.githubusercontent.com/46669551/56340953-7c7a2080-61ee-11e9-8a72-1e8fcce8b7c2.png)

Convert된 CSV 파일을 Dataset (Wide World Importers)로 저장해준다.

Dataset 에서 R NoteBook을 실행 시켜준다.

![image](https://user-images.githubusercontent.com/46669551/56341077-e1ce1180-61ee-11e9-8661-836f8181103e.png)

1. 데이터 처리 시작 [데이터 확인하기]

``` R
library("AzureML")
ws <- workspace()
dat <- download.datasets(ws, "Wide World Importers")
```

```R
head(dat)
```

![image](https://user-images.githubusercontent.com/46669551/56341182-32456f00-61ef-11e9-89a5-d3ffaee58b36.png)

- Exercise 2: Exploring data using R

2. 상품 판매를 평가하자

```R
# Evaluate Product Sales

# Exploratory exercises over the product orders data for Wide World Importers

# - What are the top 20 most popular products?
# - How do sales of the most popular product vary over time?
# - Is there a pattern to these sales?
```

3. 필요한 Package를 설치해 주자

```R
library(AzureML)
library(dplyr)
library(ggplot2)
library(scales)

install.packages("xts") # You also need to install the xts package
library(xts)

install.packages("broom") # And the broom package
library(broom)
```

4. `AzureML` Package 를 이용하여 Dataset을 호출도 해보자

```R
library("AzureML")
ws <- workspace()
ordersDataSet <- download.datasets(ws, "Wide World Importers")
head(ordersDataSet)
```

![image](https://user-images.githubusercontent.com/46669551/56341182-32456f00-61ef-11e9-89a5-d3ffaee58b36.png)

5. 물품들을 간추려서 아이템의 설명을 출력하자

```R
# The same product might occur in more than one order. Generate a list of products and their descriptions that have been ordered at least once. Each product should occur only once in the list. Store the result in another dataset called *stockItemsDataSet*.
```

```r
ordersDataSet %>%
  select(StockItemID, Description) %>%
  distinct() -> stockItemsDataSet

head(stockItemsDataSet)
```

![image](https://user-images.githubusercontent.com/46669551/56341564-69685000-61f0-11e9-9199-8256ceb0fde5.png)

6. 가장 인기있는 상품 순으로 나열해 보자

```R
# Find which products are the most popular, using a *dplyr* pipeline as follows:

# - Extract the StockItemID and quantity sold for each order
# - Group the results by StockItemID
# - Sum the quantity sold for each group, and name the column as *numOrdered*
# - Order the results in descending order of *numOrdered* (the most popular items will be at the top of the list)
# - Limit the results to the first 20 rows
```

```r
# Save the results in another dataset named *numOrderedDataSet*
```

```R
ordersDataSet %>%
  select(StockItemID, Quantity) %>%
  group_by(StockItemID) %>%
  summarize(numOrdered = sum(Quantity)) %>% 
  arrange(desc(numOrdered)) %>%
  filter(row_number() <= 20) -> numOrderedDataSet

head(numOrderedDataSet)
```

![image](https://user-images.githubusercontent.com/46669551/56341673-c106bb80-61f0-11e9-8a1c-119e59cae06e.png)

7. ID를 기준으로 '아이템 설명', '주문누적횟수'의 데이터를 Join해준다

```R
# Combine the *numOrderedDataSet* and the *stockItemsDataSet* over the *StockItemID* column so that the list contains the *StockItemID*, *numOrdered*, and *Description* columns
```

```R
results <- inner_join(numOrderedDataSet, stockItemsDataSet, by = "StockItemID")

head(results)
```

![image](https://user-images.githubusercontent.com/46669551/56342239-6a9a7c80-61f2-11e9-82c3-e19576853173.png)

8. 아이템들당 주문누적 수를 그래프로 출력해 준다.

```R
# Generate a graph showing the product descriptions on the X-axis and the number ordered on the Y-axis
```

```R
options(repr.plot.width=10, repr.plot.height=8)  
ggplot(results) +
  geom_point(mapping = aes(x = reorder(Description, -numOrdered), y = numOrdered), color = "red", size = 5) +
  labs(x = "Product", y = "Total Ordered") +
  scale_x_discrete(labels = function(x) { lapply(strwrap(x, width = 25, simplify = FALSE), paste, collapse = "\n")}) +
  theme(axis.text.x = element_text(angle = 90, size = 10))
```

![image](https://user-images.githubusercontent.com/46669551/56342439-00360c00-61f3-11e9-84a1-ac63a3ca8f17.png)

9. 가장 인기 있는 상품에 대한 분석을 진행하자

```R
## How do product sales vary over time?

# Product 191 (Black and orange fragile despatch tape 48mmx75m) is the most popular product. How do sales of this product vary over time (if at all). 

# Find all sales of product 191.
```

```R
ordersDataSet %>%
  filter(StockItemID == 191) -> productSalesDataSet

head(productSalesDataSet)
str(productSalesDataSet)
```

![image](https://user-images.githubusercontent.com/46669551/56342546-40958a00-61f3-11e9-85d0-53a90c1dfd68.png)

10. 일별 상품 판매 수를 출력한다.

```R
# Reorganize the data as a time series, based on the *PickingCompletedWhen* column. Note that this column is actually a string (chr) in month/day/year format, so it needs to be converted to a datetime.
```

```R
timeSeriesOrders <- xts(productSalesDataSet[c("StockItemID", "Quantity")], 
                        order.by = as.POSIXct(productSalesDataSet$PickingCompletedWhen, format = "%m/%d/%Y"))
head(timeSeriesOrders)
```

![image](https://user-images.githubusercontent.com/46669551/56342608-6c187480-61f3-11e9-8043-9183efb9345e.png)

11. 일별 합산 판매수를 구한다.

```R
# Work out how many units where ordered each day.
```

```r
dailyTotals <- apply.daily(timeSeriesOrders, function(x){ apply(x$Quantity, 2, sum)})

head(dailyTotals)
```

![image](https://user-images.githubusercontent.com/46669551/56342699-b26dd380-61f3-11e9-92d8-f31944c08b5b.png)

12. 일별 판매량을 그래프로 나타내어 보자

```R
# Plot a graph showing how the sales vary by day.
```

```R
# First, the time series must be converted back into a dataframe to work with ggplot.
```

```R
graphData <- tidy(dailyTotals)
head(graphData)
```

![image](https://user-images.githubusercontent.com/46669551/56342769-e517cc00-61f3-11e9-9b24-017eddf01134.png)

```R
# Then convert the index column back into a datetime value.
```

```R
graphData$index <- as.POSIXct(graphData$index, origin="1970-01-01")
head(graphData)
```

![image](https://user-images.githubusercontent.com/46669551/56342879-2a3bfe00-61f4-11e9-81ca-0732b1ff7302.png)

```R
# Finally, plot the data.
```

```R
options(repr.plot.width=15, repr.plot.height=5)
ggplot(graphData, aes(x = index, y = value)) +
  ggtitle("Product Sales Over Time for Product 191") +
  xlab("Date") +
  ylab("Units Sold") +
  scale_x_datetime(labels = date_format("%Y-%m"), breaks = date_breaks("months")) +
  theme(axis.text.x = element_text(angle = 45)) +
  geom_point(color = "blue")
```

![image](https://user-images.githubusercontent.com/46669551/56342949-5f485080-61f4-11e9-92db-0cf2df6a69ee.png)

13. 판매의 패턴이 존재하는지 알아보자

```R
## Is there a pattern to these sales?

# Focus on sales for 2013.
```

```R
firstDay <- as.POSIXct("2013-01-01")
lastDay <- as.POSIXct("2013-12-31")
day1 <- as.numeric(firstDay)
dayN <- as.numeric(lastDay)
productSalesFor2013 <- filter(graphData, (index >= day1) & (index <= dayN))

options(repr.plot.width=15, repr.plot.height=5)
ggplot(productSalesFor2013, aes(x = index, y = value)) +
  ggtitle("Product Sales for Product 191 in 2013") +
  xlab("Date") +
  ylab("Units Sold") +
  scale_x_datetime(labels = date_format("%Y-%m"), breaks = date_breaks("months")) +
  theme(axis.text.x = element_text(angle = 45)) +
  geom_point(color = "blue")
```

![image](https://user-images.githubusercontent.com/46669551/56343063-af271780-61f4-11e9-9618-5a51fc972fbe.png)

```R
# The graph and curve for 2014.
firstDay <- as.POSIXct("2014-01-01")
lastDay <- as.POSIXct("2014-12-31")
day1 <- as.numeric(firstDay)
dayN <- as.numeric(lastDay)
productSalesFor2014 <- filter(graphData, (index >= day1) & (index <= dayN))

ggplot(productSalesFor2014, aes(x = index, y = value)) +
  ggtitle("Product Sales for Product 191 in 2014") +
  xlab("Date") +
  ylab("Units Sold") +
  scale_x_datetime(labels = date_format("%Y-%m"), breaks = date_breaks("months")) +
  theme(axis.text.x = element_text(angle = 45)) +
  geom_point(color = "black", alpha = 0.2) +
  geom_smooth(method = "lm", formula = y ~ poly(x, 9))
```

![image](https://user-images.githubusercontent.com/46669551/56343099-cf56d680-61f4-11e9-95c2-4620e0b3af08.png)

```R
# The graph and curve for 2015.
firstDay <- as.POSIXct("2015-01-01")
lastDay <- as.POSIXct("2015-12-31")
day1 <- as.numeric(firstDay)
dayN <- as.numeric(lastDay)
productSalesFor2015 <- filter(graphData, (index >= day1) & (index <= dayN))

ggplot(productSalesFor2015, aes(x = index, y = value)) +
  ggtitle("Product Sales for Product 191 in 2015") +
  xlab("Date") +
  ylab("Units Sold") +
  scale_x_datetime(labels = date_format("%Y-%m"), breaks = date_breaks("months")) +
  theme(axis.text.x = element_text(angle = 45)) +
  geom_point(color = "black", alpha = 0.2) +
  geom_smooth(method = "lm", formula = y ~ poly(x, 9))
```

![image](https://user-images.githubusercontent.com/46669551/56343135-edbcd200-61f4-11e9-8d64-a12a229c07b4.png)

#### R 전체 코드

```R

# Evaluate Product Sales

Exploratory exercises over the product orders data for Wide World Importers

- What are the top 20 most popular products?
- How do sales of the most popular product vary over time?
- Is there a pattern to these sales?


​```R
library(AzureML)
library(dplyr)
library(ggplot2)
library(scales)

install.packages("xts") # You also need to install the xts package
library(xts)

install.packages("broom") # And the broom package
library(broom)
​```


​```R
library("AzureML")
ws <- workspace()
ordersDataSet <- download.datasets(ws, "Wide World Importers")
head(ordersDataSet)
​```

The same product might occur in more than one order. Generate a list of products and their descriptions that have been ordered at least once. Each product should occur only once in the list. Store the result in another dataset called *stockItemsDataSet*.


​```R
ordersDataSet %>%
  select(StockItemID, Description) %>%
  distinct() -> stockItemsDataSet

head(stockItemsDataSet)
​```

Find which products are the most popular, using a *dplyr* pipeline as follows:

- Extract the StockItemID and quantity sold for each order
- Group the results by StockItemID
- Sum the quantity sold for each group, and name the column as *numOrdered*
- Order the results in descending order of *numOrdered* (the most popular items will be at the top of the list)
- Limit the results to the first 20 rows

Save the results in another dataset named *numOrderedDataSet*


​```R
ordersDataSet %>%
  select(StockItemID, Quantity) %>%
  group_by(StockItemID) %>%
  summarize(numOrdered = sum(Quantity)) %>% 
  arrange(desc(numOrdered)) %>%
  filter(row_number() <= 20) -> numOrderedDataSet

head(numOrderedDataSet)
​```

Combine the *numOrderedDataSet* and the *stockItemsDataSet* over the *StockItemID* column so that the list contains the *StockItemID*, *numOrdered*, and *Description* columns


​```R
results <- inner_join(numOrderedDataSet, stockItemsDataSet, by = "StockItemID")

head(results)
​```

Generate a graph showing the product descriptions on the X-axis and the number ordered on the Y-axis


​```R
options(repr.plot.width=10, repr.plot.height=8)  
ggplot(results) +
  geom_point(mapping = aes(x = reorder(Description, -numOrdered), y = numOrdered), color = "red", size = 5) +
  labs(x = "Product", y = "Total Ordered") +
  scale_x_discrete(labels = function(x) { lapply(strwrap(x, width = 25, simplify = FALSE), paste, collapse = "\n")}) +
  theme(axis.text.x = element_text(angle = 90, size = 10))
​```

## How do product sales vary over time?

Product 191 (Black and orange fragile despatch tape 48mmx75m) is the most popular product. How do sales of this product vary over time (if at all). 

Find all sales of product 191.


​```R
ordersDataSet %>%
  filter(StockItemID == 191) -> productSalesDataSet

head(productSalesDataSet)
str(productSalesDataSet)

​```

Reorganize the data as a time series, based on the *PickingCompletedWhen* column. Note that this column is actually a string (chr) in month/day/year format, so it needs to be converted to a datetime.


​```R
timeSeriesOrders <- xts(productSalesDataSet[c("StockItemID", "Quantity")], 
                        order.by = as.POSIXct(productSalesDataSet$PickingCompletedWhen, format = "%m/%d/%Y"))
head(timeSeriesOrders)
​```

Work out how many units where ordered each day.


​```R
dailyTotals <- apply.daily(timeSeriesOrders, function(x){ apply(x$Quantity, 2, sum)})

head(dailyTotals)
​```

Plot a graph showing how the sales vary by day.

First, the time series must be converted back into a dataframe to work with ggplot.


​```R
graphData <- tidy(dailyTotals)
head(graphData)
​```

Then convert the index column back into a datetime value.


​```R
graphData$index <- as.POSIXct(graphData$index, origin="1970-01-01")
head(graphData)
​```

Finally, plot the data.


​```R
options(repr.plot.width=15, repr.plot.height=5)
ggplot(graphData, aes(x = index, y = value)) +
  ggtitle("Product Sales Over Time for Product 191") +
  xlab("Date") +
  ylab("Units Sold") +
  scale_x_datetime(labels = date_format("%Y-%m"), breaks = date_breaks("months")) +
  theme(axis.text.x = element_text(angle = 45)) +
  geom_point(color = "blue")
​```

## Is there a pattern to these sales?

Focus on sales for 2013.


​```R
firstDay <- as.POSIXct("2013-01-01")
lastDay <- as.POSIXct("2013-12-31")
day1 <- as.numeric(firstDay)
dayN <- as.numeric(lastDay)
productSalesFor2013 <- filter(graphData, (index >= day1) & (index <= dayN))

options(repr.plot.width=15, repr.plot.height=5)
ggplot(productSalesFor2013, aes(x = index, y = value)) +
  ggtitle("Product Sales for Product 191 in 2013") +
  xlab("Date") +
  ylab("Units Sold") +
  scale_x_datetime(labels = date_format("%Y-%m"), breaks = date_breaks("months")) +
  theme(axis.text.x = element_text(angle = 45)) +
  geom_point(color = "blue")
​```

Fit a curve to the sales, and then compare to curves for 2014 and 2015 to see if there is a regular pattern.


​```R
ggplot(productSalesFor2013, aes(x = index, y = value)) +
  ggtitle("Product Sales for Product 191 in 2013") +
  xlab("Date") +
  ylab("Units Sold") +
  scale_x_datetime(labels = date_format("%Y-%m"), breaks = date_breaks("months")) +
  theme(axis.text.x = element_text(angle = 45)) +
  geom_point(color = "black", alpha = 0.2) +
  geom_smooth(method = "lm", formula = y ~ poly(x, 9))
​```

The graph and curve for 2014.


​```R
firstDay <- as.POSIXct("2014-01-01")
lastDay <- as.POSIXct("2014-12-31")
day1 <- as.numeric(firstDay)
dayN <- as.numeric(lastDay)
productSalesFor2014 <- filter(graphData, (index >= day1) & (index <= dayN))

ggplot(productSalesFor2014, aes(x = index, y = value)) +
  ggtitle("Product Sales for Product 191 in 2014") +
  xlab("Date") +
  ylab("Units Sold") +
  scale_x_datetime(labels = date_format("%Y-%m"), breaks = date_breaks("months")) +
  theme(axis.text.x = element_text(angle = 45)) +
  geom_point(color = "black", alpha = 0.2) +
  geom_smooth(method = "lm", formula = y ~ poly(x, 9))
​```

The graph and curve for 2015.


​```R
firstDay <- as.POSIXct("2015-01-01")
lastDay <- as.POSIXct("2015-12-31")
day1 <- as.numeric(firstDay)
dayN <- as.numeric(lastDay)
productSalesFor2015 <- filter(graphData, (index >= day1) & (index <= dayN))

ggplot(productSalesFor2015, aes(x = index, y = value)) +
  ggtitle("Product Sales for Product 191 in 2015") +
  xlab("Date") +
  ylab("Units Sold") +
  scale_x_datetime(labels = date_format("%Y-%m"), breaks = date_breaks("months")) +
  theme(axis.text.x = element_text(angle = 45)) +
  geom_point(color = "black", alpha = 0.2) +
  geom_smooth(method = "lm", formula = y ~ poly(x, 9))
​```

```

- Exercise 3: Analyzing data using Python

1. 데이터를 준비하자 

![image](https://user-images.githubusercontent.com/46669551/56343520-f3ff7e00-61f5-11e9-8d81-510d5b86d0e7.png)

**Selected columns:**
**Column names**: age,fnlwgt,education-num,sex,native-country,income

![image](https://user-images.githubusercontent.com/46669551/56344213-cf0c0a80-61f7-11e9-9ee7-89b412fcc6f5.png)

**Python Scripts**

```python
# The script MUST contain a function named azureml_main
# which is the entry point for this module.

# imports up here can be used to 
import pandas as pd

# The entry point function can contain up to two input arguments:
#   Param<dataframe1>: a pandas.DataFrame
#   Param<dataframe2>: a pandas.DataFrame
def azureml_main(dataframe1 = None):

    import pandas as pd

    # Only use the columns of interest and restrict the rows to those in the US
    censusData = dataframe1[['age', 'fnlwgt', 'education-num', 'sex', 'native-country', 'income']]
    censusData = censusData.loc[censusData['native-country'] == "United-States"]
    del censusData['native-country']

    # factorize the sex column
    censusData['sex'], sex_index = pd.factorize(censusData['sex'])

    return censusData
```

![image](https://user-images.githubusercontent.com/46669551/56344322-15fa0000-61f8-11e9-8f6b-4a6d7afe370f.png)

![image](https://user-images.githubusercontent.com/46669551/56346434-07621780-61fd-11e9-95b0-991bf68a73e1.png)



Test Data와 Train Data의 분할은 0.9로 진행 한다.

Python Script를 이용하여 데이터를 분석하자.

```python
# Data안의 요소인 age,working calss, education, 그리고 gender의 요소를 바탕으로 income을 예측하는 Model을 생성하고, 테스트를 진행한다. 
# 필요한 모듈을 설치해준다.
import pandas as pd
import sklearn.ensemble as ensemble
import sklearn.metrics as metrics
import matplotlib
matplotlib.use("agg")
import matplotlib.pyplot as plt

# 새로운 함수를 정의해준다.
def azureml_main(censusTraining = None, censusTest = None):

    # 모델을 Train한다.
    classifier = ensemble.AdaBoostClassifier()# 가중치를 두어 분류 예측하는 클래스
    classifier.fit(censusTraining[["age", "fnlwgt", "education-num", "sex"]], censusTraining["income"])
        
    # test data와 model을 사용하여 예측한다.
    # 예측값은 0또는 1이다.
    predictions = classifier.predict(censusTest[["age", "fnlwgt", "education-num", "sex"]])
    
    # confusion matrix를 시험하여 model의 정확도를 알아본다.
    conf = metrics.confusion_matrix(censusTest["income"], predictions)
    print(pd.crosstab(censusTest["income"], predictions, rownames=['True'], colnames=['Predicted'], margins=True))
    
    # confusion matrix를 시각화 한다.
    plt.title('Confusion Matrix')
    plt.imshow(conf, cmap='binary', interpolation='None')
    plt.savefig("confusion.png")
    plt.clf()
    
    # ROC AUC score를 계산한다.
	# ROC 곡선(수신자 조작 특성 곡선)은 모든 분류 임계값에서 분류 모델의 성능을 보여주는 그래프입	  니다. 이 곡선은 다음 두 매개변수를 표시합니다.

	# 참 양성 비율(TPR)
	# 허위 양성 비율(FPR)
	# 참 양성 비율(TPR)은 재현율의 동의어
    # False Positive rate 원래는 Positive 값인데, 잘못해서 Negative로 판단한 비율로
  
    censusTest['income'], income_index = pd.factorize(censusTest['income'])
    # Pandas의 factorize를 사용하여 Labeling과 Unique value로 바꾸어 준다.
    # 이때 Label은 0또는1이다. 왜냐하면 income은 5만달러 이하와 5만달러 초과 이기 때문이다.
    predictedIncomes = pd.factorize(predictions)
    rocData = metrics.roc_curve(censusTest["income"], predictedIncomes[0])
    rocAuc = metrics.roc_auc_score(censusTest["income"], predictedIncomes[0])

    # ROC curve 그리기
    # ROC Curve는 Receiver-Operating Characteristic curve의 줄임말로, 특정 진단 방법의 민		  감도와 특이도가 어떤 관계를 갖고 있는지를 표현한 그래프이다. 
    # ROC (Receiver Operating Characteristics)
	# ROC 그래프는 가로축을 FP Rate (Specificity) 값의 비율로 하고 세로축을 TP Rate 			  (Sensitive) 로 하여 시각화 한 그래프이다.
	
    # Specificity (True negative rate)Specificity 값은 Negative 로 판단한것중에, 실제 		  Negative 값의 비율이다.
    
    # Sensitivity (Recall or True positive Rate)
	# 민감도라고도 하는데, Sensitive 또는  Recall이라고도 하는데, 원래 Positive 데이타 수에서 	  Positive로 분류된 수를 이야기 한다. 에를 들어 원본 데이타에 암 양성이 100개 있었는데, 모델	  에 있어서 90개가 분류되었으면, Sensitive Rate = 0.9 가된다.
    # 그래프가 위로 갈 수록 좋은 모델이고, 적어도 Y=X 그래프보다 위에 있어야 어느정도 쓸모 있는 	  모델로 볼 수 있다.
	# 출력 그래프의 Area 값이 AUC 값이다.
    # AUC 값의 범위는 0~1입니다. 예측이 100% 잘못된 모델의 AUC는 0.0이고 예측이 100% 정확한 모		 델의 AUC는 1.0입니다.

	# AUC는 다음 두 가지 이유로 이상적입니다.

	# AUC는 척도 불변입니다. AUC는 절대값이 아니라 예측이 얼마나 잘 평가되는지 측정합니다.
	# AUC는 분류 임계값 불변입니다. AUC는 어떤 분류 임계값이 선택되었는지와 상관없이 모델의 예측 	   품질을 측정합니다.
	# 하지만 이러한 두 이유는 특정 사용 사례에서 AUC의 유용성을 제한할 수 있다는 단점이 있습니다.

	# 척도 불변이 항상 이상적인 것은 아닙니다. 예를 들어 잘 보정된 확률 결과가 필요한 경우가 있는		  데 AUC로는 이 정보를 알 수 없습니다.

	# 분류 임계값 불변이 항상 이상적인 것은 아닙니다. 허위 음성(FN) 비용과 허위 양성(FP) 비용에 		큰 차이가 있는 경우 한 가지 유형의 분류 오류를 최소화하는 것은 위험할 수 있습니다. 예를 들어 		 이메일 스팸 감지를 실행할 때 허위 양성(FP)의 최소화로 인해 허위 음성(FN)이 크게 증가한다고 	   해도 허위 양성(FP) 최소화를 우선시하고 싶을 수 있습니다. AUC는 이런 유형의 최적화에 유용한 		 측정항목이 아닙니다.

    plt.plot(rocData[0], rocData[1], label='ROC curve (area = %0.3f)' % rocAuc)
    plt.plot([0, 1], [0, 1], 'k--')  # random predictions curve
    plt.xlim([0.0, 1.0])
    plt.ylim([0.0, 1.0])
    plt.xlabel('False Positive Rate')
    plt.ylabel('True Positive Rate')
    plt.title('Receiver Operating Characteristic')
    plt.legend(loc="lower right")
    plt.show()
    plt.savefig("roc.png")

    return censusTraining
```



![image](https://user-images.githubusercontent.com/46669551/56351509-3fbb2300-6208-11e9-9a6b-bb9529b137ad.png)





> Lab Scenario
>
> You work as a data scientist for Adatum Consultants, a company that provides
> machine learning services and advice for a range of clients. One of your
> clients is Wide World Importers, who are transitioning from a Business
> Intelligence practice to a Business Analytics practice. As part of this
> transition, Wide World Importers are looking for insights from operational data
> sources throughout the organization.  
>
> You are working with a team of Wide World Importers business analysts,
> who write reports using data that is stored in a variety of locations,
> including Azure SQL Database. The business analysts want to investigate the
> potential for developing custom models that make use of R and Python scripts,
> and how to document processes by using a Jupyter notebook.

> Lab Review
>
> - What conclusions can you draw from the confusion matrix for the census income
>   predictions about the accuracy of the model?
> - What value for the AUC does the ROC curve show?

> **Question**
>
> What conclusions can you draw from the confusion matrix for the census income predictions about the accuracy of the model?
>
> **Answer**
>
> The decision matrix shows that the model was reasonably good at predicting incomes less than or equal to 50 K, but not so good at predicting incomes greater than 50 K (the number of errors exceeds the number of correct results). This shows that some factors might be missing from the model (such as race), or maybe the model itself needs some refinement. The Scikit-learn **AdaBoostClassifier** has a number of parameters that you can use to tweak the way in which it learns.
>
> **Question**
>
> What value for the AUC does the ROC curve show?
>
> **Answer**
>
> The AUC should be calculated as somewhere around 0.64 (barely acceptable).
>
> These results might look disappointing, but remember that this is simply a first attempt at constructing a predictive model. Both Python and R provide many different libraries with a large number of highly tunable algorithms that you can plug into an Azure Machine Learning experiment using the techniques shown in this lab.

> Module Review and Takeaways
>
> In this module, you learned how to:
>
> - Describe how to use R code to analyze and visualize data
> - Explain how to use Python code process data
> - Use Jupyter notebooks to document your experiments, and use R and Python code to augment your experiments

