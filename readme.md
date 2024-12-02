# Overview 
This project demonstrates big data analysis of Classified Ads for Cars using a multi-node cluster and apache spark. The main goal is to process, clean, and analyze the data to derive meaning such as how other features influece the price. This project also focuses on using dataprocessing to explore the Big Data Vs.

Link to dataset: https://www.kaggle.com/datasets/mirosval/personal-cars-classifieds

# Car Listings Dataset

This dataset was scraped over a period of more than a year from various car listing websites in the Czech Republic and Germany. The purpose of the original scraping was to build a model that could estimate whether a car is a good or bad buy based on the car listing details. However, after encountering challenges with building a satisfactory model, I decided to make the dataset available as open data for others to use.


## Setup 
## Prerequisites
- **Java 13**
- **Hadoop 3.1.3**
- **Spark 3.5.3**
- **Anaconda** for Python and Jupyter Notebook
- **Scala**

## environment variable setup
HADOOP_HOME = Path to haddop bin and sbin
JAVA_HOME= Path to java
PYSPARK_DRIVER_PYTHON= Path to jupyter
PYSPARK_DRIVER_PYTHON_OPTS= notebook
PYTHON_HOME= Path to python
SPARK_HOME= Path to spark 



## Hadoop Configuration
Create data folder and in the following directories: datanode, namenode, and temp.
Configure hdfs-site.xml(give path of namenode and datanode) and core-site.xml(Add hadoop namenode address) in the etc/hadoop directory.
Worker File: add worker node IPs.


## How to Upload a file to HDFS
hadoop fs -mkdir -p /user/hdfs/

hadoop fs -put "C:\Users\yuvraj\Downloads\archive (4)\all_anonymized_2015_11_2017_03.csv" /user/hdfs/

hadoop fs -ls /user/hdfs/


# Steps to Run the Code
## Master Run
- start-all (in admin cmd)
- go to spark bin folder in cmd and type( spark-class org.apache.spark.deploy.master.Master)
-go to anaconda shell-> pyspark --master spark://masterIP:port


## Worker Run 
- start-dfs (in admin cmd)
- go to spark bin folder in cmd and type( spark-class org.apache.spark.deploy.worker.Worker spark://master-ip:port)

## Data analysis
The run the python notebook 
### What does the notebook contain 
#### Data Cleaning and Preprocessing
The dataset contains missing values and erroneous data (e.g., phone numbers scraped as mileage).
We filtered out rows with null values in key columns (maker, manufacture_year, fuel_type, etc.) and performed aggregations and visualizations.
### Visualizations
##### Top 10 Car Make and Model Distribution (No Nulls): 

A pie chart displaying the distribution of car makes and models by count after filtering out rows with null values.

##### Price Distribution by Fuel Type: 

A bar chart showing the average price of cars by fuel type (gasoline, diesel, electric, etc.).

##### Price Distribution by Body Type: 

A horizontal bar chart showing the average price of cars grouped by body type.

##### Listings Over Time: 

A line plot showing the trends in car listings over time (grouped by year and month).

##### Word Cloud of Car Makers:

A word cloud visualization of the most common car makes in the dataset.

### Count for Volume
### Statistics of the data for Veracity 
### Schema for Variety 

### Machine Learning Pipeline
We built a predictive model using Spark MLlib to estimate the car price based on various features:

Categorical columns (maker, model, body_type, fuel_type, transmission) were encoded using StringIndexer.

A VectorAssembler was used to combine features into a single vector column for the model.

A Linear Regression model was trained to predict price_eur using the features.

The model's performance was evaluated using Root Mean Squared Error (RMSE) and R-squared metrics.

#### Model Evaluation
After training the model, the predictions were evaluated using the following metrics:

Root Mean Squared Error (RMSE): Indicates the model's prediction error.

R-squared: A measure of the model's fit.


## License

This dataset is provided under an open data license for use in research, analysis, and model development. Please respect privacy and data use regulations.

---

If you use this dataset for research or any project, please acknowledge the source.

