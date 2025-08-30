# PySpark Exercises

A comprehensive collection of hands-on exercises designed to help data scientists and learners master data manipulation and analysis using the PySpark API. This repository covers 11 core topics, each with practical notebooks and solutions, adapted from the original Pandas Exercises [Guipsamora's Pandas Exercises](https://github.com/guipsamora/pandas_exercises) project to focus on PySpark.

Tutorials are great resources, but to learn is to do. So unless you practice you won't learn. Pyspark is no exception!

There will be three different types of files:

1. Exercise instructions
2. Solutions without code
3. Solutions with code and comments

My suggestion is that you learn a topic in a tutorial, video or documentation and then do the first exercises. Learn one more topic and do more exercises. If you are stuck, don't go directly to the solution with code files. Check the solutions only and try to get the correct answer.
Suggestions and collaborations are more than welcome.🙂 Please open an issue or make a PR indicating the exercise and your problem/solution.

## Local Setup / Installation on Mac

#### Local setup of apache spark with jupyter-notebook

- Download the apache-spark latest version from [here](https://spark.apache.org/downloads.html).
- Unzip the directory to the chosen folder.
- Add `spark` path in the `.bashrc` or `.zshrc` file.

```sh
export SPARK_HOME=/tools/spark-3.4.3-bin-hadoop3
export PATH=$SPARK_HOME/bin:$PATH
```

- Install following `apache-spark` dependency either by pip or poetry in virtual environment

```sh
# with pip manuall create virtaul env using below command
python3 -m venv .venv
source .venv/bin/activate
# with pip install below dependency
pip3 install pyspark findspark jupyter
# start jupyter notebook
jupyter notebook
```

```sh
# with poetry
poetry new <prpject-name>
cd <project-name>
poetry install
poetry add pyspark findspark jupyter
# start jupyter notebook
poetry run jupyter notebook
```

- Once the jupyter notebook is up and running add below lines to the first cell.

```python
import findspark
findspark.init()
import pyspark

import random
sc = pyspark.SparkContext(appName="Pi")
num_samples = 100000000
def inside(p):
  x, y = random.random(), random.random()
  return x*x + y*y < 1
count = sc.parallelize(range(0, num_samples)).filter(inside).count()
pi = 4 * count / num_samples
print(pi)

from pyspark.sql import SparkSession
spark = SparkSession.builder.appName("demo").getOrCreate()

df = spark.createDataFrame(
    [
        ("sue", 32),
        ("li", 3),
        ("bob", 75),
        ("heo", 13),
    ],
    ["first_name", "age"],
)
df.show()
```

---

As a community project, we're seeking help to converting this repo into a complete repository for mastering Pyspark.

We need assistance with the following:

## Convert existing `.ipynb` files with Pandas solutions to Pyspark solutions.

Select an issue in the Issues tab corresponding to one of the tutorial directories. In your pull request, re-write the directory using Pyspark instead of pandas. So far, we've listed issues for every exercise in the repo.

## Create new issues

We have a lot of refactoring to do outside of the lessons. If you see something that needs to be changed, please raise an issue. To contribute, please either raise an issue in the `Issues` tab, or raise a pull request for an existing issue.

## Readme's

Our readme section could use some work. For instance, we should list ways to run Pyspark on local machines (Windows, MacOS, Linux).

# Lessons

|                                                 |                                                                   |                             |
| :---------------------------------------------: | :---------------------------------------------------------------: | :-------------------------: |
|   [Getting and knowing](#getting-and-knowing)   |                          [Merge](#merge)                          | [Time Series](#time-series) |
| [Filtering and Sorting](#filtering-and-sorting) |                          [Stats](#stats)                          |    [Deleting](#deleting)    |
|              [Grouping](#grouping)              |                  [Visualization](#visualization)                  |          Indexing           |
|                 [Apply](#apply)                 | [Creating Series and DataFrames](#creating-series-and-dataframes) |          Exporting          |

### [Getting and knowing](https://github.com/guipsamora/pandas_exercises/tree/master/01_Getting_%26_Knowing_Your_Data)

[Chipotle](https://github.com/guipsamora/pandas_exercises/tree/master/01_Getting_%26_Knowing_Your_Data/Chipotle)  
[Occupation](https://github.com/guipsamora/pandas_exercises/tree/master/01_Getting_%26_Knowing_Your_Data/Occupation)  
[World Food Facts](https://github.com/guipsamora/pandas_exercises/tree/master/01_Getting_%26_Knowing_Your_Data/World%20Food%20Facts)

### [Filtering and Sorting](https://github.com/guipsamora/pandas_exercises/tree/master/02_Filtering_%26_Sorting)

[Chipotle](https://github.com/guipsamora/pandas_exercises/tree/master/02_Filtering_%26_Sorting/Chipotle)  
[Euro12](https://github.com/guipsamora/pandas_exercises/tree/master/02_Filtering_%26_Sorting/Euro12)  
[Fictional Army](https://github.com/guipsamora/pandas_exercises/tree/master/02_Filtering_%26_Sorting/Fictional%20Army)

### [Grouping](https://github.com/guipsamora/pandas_exercises/tree/master/03_Grouping)

[Alcohol Consumption](https://github.com/guipsamora/pandas_exercises/tree/master/03_Grouping/Alcohol_Consumption)  
[Occupation](https://github.com/guipsamora/pandas_exercises/tree/master/03_Grouping/Occupation)  
[Regiment](https://github.com/guipsamora/pandas_exercises/tree/master/03_Grouping/Regiment)

### [Apply](https://github.com/guipsamora/pandas_exercises/tree/master/04_Apply)

[Students Alcohol Consumption](https://github.com/guipsamora/pandas_exercises/tree/master/04_Apply/Students_Alcohol_Consumption)  
[US_Crime_Rates](https://github.com/guipsamora/pandas_exercises/tree/master/04_Apply/US_Crime_Rates)

### [Merge](https://github.com/guipsamora/pandas_exercises/tree/master/05_Merge)

[Auto_MPG](https://github.com/guipsamora/pandas_exercises/tree/master/05_Merge/Auto_MPG)  
[Fictitious Names](https://github.com/guipsamora/pandas_exercises/tree/master/05_Merge/Fictitous%20Names)  
[House Market](https://github.com/guipsamora/pandas_exercises/tree/master/05_Merge/Housing%20Market)

### [Stats](https://github.com/guipsamora/pandas_exercises/tree/master/06_Stats)

[US_Baby_Names](https://github.com/guipsamora/pandas_exercises/tree/master/06_Stats/US_Baby_Names)  
[Wind_Stats](https://github.com/guipsamora/pandas_exercises/tree/master/06_Stats/Wind_Stats)

### [Visualization](https://github.com/guipsamora/pandas_exercises/tree/master/07_Visualization)

[Chipotle](https://github.com/guipsamora/pandas_exercises/tree/master/07_Visualization/Chipotle)  
[Titanic Disaster](https://github.com/guipsamora/pandas_exercises/tree/master/07_Visualization/Titanic_Desaster)  
[Scores](https://github.com/guipsamora/pandas_exercises/tree/master/07_Visualization/Scores)  
[Online Retail](https://github.com/guipsamora/pandas_exercises/tree/master/07_Visualization/Online_Retail)  
[Tips](https://github.com/guipsamora/pandas_exercises/tree/master/07_Visualization/Tips)

### [Creating Series and DataFrames](https://github.com/guipsamora/pandas_exercises/tree/master/08_Creating_Series_and_DataFrames)

[Pokemon](https://github.com/guipsamora/pandas_exercises/tree/master/08_Creating_Series_and_DataFrames/Pokemon)

### [Time Series](https://github.com/guipsamora/pandas_exercises/tree/master/09_Time_Series)

[Apple_Stock](https://github.com/guipsamora/pandas_exercises/tree/master/09_Time_Series/Apple_Stock)  
[Getting_Financial_Data](https://github.com/guipsamora/pandas_exercises/tree/master/09_Time_Series/Getting_Financial_Data)  
[Investor_Flow_of_Funds_US](https://github.com/guipsamora/pandas_exercises/tree/master/09_Time_Series/Getting_Financial_Data)

### [Deleting](https://github.com/guipsamora/pandas_exercises/tree/master/10_Deleting)

[Iris](https://github.com/guipsamora/pandas_exercises/tree/master/10_Deleting/Iris)  
[Wine](https://github.com/guipsamora/pandas_exercises/tree/master/10_Deleting/Wine)

# Video Solutions

Video tutorials of data scientists working through the above exercises:

[Data Talks - Pandas Learning By Doing](https://www.youtube.com/watch?v=pu3IpU937xs&list=PLgJhDSE2ZLxaY_DigHeiIDC1cD09rXgJv)
