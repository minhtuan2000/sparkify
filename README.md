# Churn predicion with Spark

Sparkify is a fictional music stream service created by [Udacity](https://www.udacity.com/) for the capstone project of the Data Scientist Nanodegree. The goal of this project is to predict the churn rate of users on the platform. 

As a streaming service, Sparkify generates a large dataset of user interactions and presumably, will continue to generate even more data in the future. Thus, it has entered the realm of Big Data and I used Spark to work with the data in the project.

## Repository

`Sparkify.ipynb` and `Sparkify.html` are the main Jupyter Notebook and its corresponding HTML version.

The folder `graphs` contains some useful visualizations.

## Getting started

The notebook is originally executed on IBM Watson Studio with `Python 3.7` and `Spark 3.0.1` (2 Executors: 1 vCPU and 4 GB RAM, Driver: 1 vCPU and 4 GB RAM). In order to run the notebook, you will need to fill in the fields `service_id`, `iam_service_endpoint`, `configuration_name` and `bucket_name` in the first cell.

## Summary

The detailed process of data cleaning, exploration, modeling and results are provided in my blog post. Here are just some key points.

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

Using Random Forest classifier, the model was able to reach F1 score of 0.88 and accurately predict 34 out of 36 users in the test dataset.

![image](https://github.com/minhtuan2000/sparkify/blob/main/graphs/prediction.png?raw=true)

