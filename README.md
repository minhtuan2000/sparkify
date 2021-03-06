# Churn predicion with Spark

Sparkify is a fictional music streaming service created by [Udacity](https://www.udacity.com/). It offers a large database on the activities of thousands of unique users on its platform. 

## Motivation

Presuming it exists, Sparkify will continue to generate even more data in the future. In this case, Spark proves to be a suitable tool to work with the data as it offers the much-needed scalability.

As big data is becoming increasingly popular in the industry, I believe that being able to work with big data is one of the key skills to learn in data science. This project is an exellent chance for me to learn Spark and apply to a real-world problem. Moreover, as it also conclude my journey with the Data Scientist Nanodegree, I will be able to apply all of my knowledge from data analysis and visualization to building machine learning pipelines.

## Directories

- `Sparkify.ipynb` and `Sparkify.html` are the main Jupyter Notebook and its corresponding HTML version.

- `graphs` contains some useful visualizations.

## Getting started

The notebook is originally executed on IBM Watson Studio with `Python 3.7` and `Spark 3.0.1` (2 Executors: 1 vCPU and 4 GB RAM, Driver: 1 vCPU and 4 GB RAM). In order to run the notebook, you will need to replace in the fields `service_id`, `iam_service_endpoint`, `configuration_name` and `bucket_name` in the first cell. The access key shown is revoked.

List of required Python libraries to run the notebook:

- PySpark (including PySpark ML)
- Numpy
- Pandas
- Matplotlib
- Seaborn

## Summary

The detailed process of data cleaning, exploration, modeling and results are provided in [my blog post](https://minhtuan270820000.medium.com/churn-prediction-with-spark-e16d96bbf147). Here are just some key points.

### Dataset

The dataset used in this project is a small subset (~200MB) of the original dataset (~12GB) provided by Udacity. In this dataset, there are 448 unique users and 99 cancelations / churners (~22%).

### Key data visualizations

The last interaction timestamp is the key feature to distinguish churner.

![image](https://github.com/minhtuan2000/sparkify/blob/main/graphs/distribution_last_interation_user.png?raw=true)

Longtime users are more loyal to the service.

![image](https://github.com/minhtuan2000/sparkify/blob/main/graphs/distribution_user_lifetime.png?raw=true)

Subscription level has no effect on churn rate.

![image](https://github.com/minhtuan2000/sparkify/blob/main/graphs/distribution_user_level.png?raw=true)

In average, churned users have less `Thumbs Up`, less `NextSong`, less `Add to Playlist`, more `Thumbs Down`, more `Roll Advert` and more `Downgrade`. Note that `Downgrade` is not the actual account downgrading event but the page where users can choose to downgrade their account.

![image](https://github.com/minhtuan2000/sparkify/blob/main/graphs/distribution_page_percentage.png?raw=true)

### Model 

Using Random Forest classifier, the model was able to reach F1 score of 0.88 and accurately predict 33 out of 36 users in the test dataset.
