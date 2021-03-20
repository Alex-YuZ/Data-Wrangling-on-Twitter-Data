# Project Overview

**Data Wrangling**, being an indespensible part, not only in the data analysis process, but also in the whole data science workflow, this project is right just for that. 

Real-world data rarely comes clean. Using Python and its libraries, this project will demonstrate multiple tasks concerning the data wrangling process including gathering data from a variety of sources and in a variety of formats, assessing data quality and tidiness, finally cleaning it and presenting some basic EDA (Exploratory Data Analysis) as well. 

---

## About the Datasets
The dataset for this project is the tweet archive of Twitter user <a href='https://twitter.com/dog_rates'>@dog_rates</a>, also known as <a href='https://en.wikipedia.org/wiki/WeRateDogs'>WeRateDogs</a>. WeRateDogs is a Twitter account that rates people's dogs with a humorous comment about the dog. These ratings almost always have a denominator of 10. The numerators, though? Almost always greater than 10. 11/10, 12/10, 13/10, etc. Why? Because "<a href='http://knowyourmeme.com/memes/theyre-good-dogs-brent'>they're good dogs Brent</a>." WeRateDogs has **over 4 million** followers and has received international media coverage. One of the dataset used in the project `twitter-archive-enhanced.csv` contains basic tweet data (tweet ID, timestamp, text, etc.) for all 5000+ of their tweets as they stood on August 1, 2017.

<center><img src='./images/img4readme.png' alt='Image via Boston Magazine' width=500></center>

<center>Image via <a href='http://www.bostonmagazine.com/arts-entertainment/blog/2017/04/18/dog-rates-mit/'><i>Bostom Magazine</i></a></center>

<br>

There are two other raw data (namely the `image-predictions.tsv` and `tweet_json.txt`) for this project but need to be acquired from various ways. This will be detailed explained in the complete data wrangling process part.

---

## About the Data Wrangling Process

There are three main important steps for a data wrangling process:

1. Gathering data
2. Assessing data
3. Cleaning data

We implemented the three main steps above thoroughly in the `wrangle_act.ipynb` notebook.

In the **Gathering phase**, we collected data from three different sources:

- `image-predictions.tsv`. This is a tab-separated file stored on a remote server and we download it programmatically using python's [requests](https://requests.readthedocs.io/en/master/) library via a ___url___.


- `twitter-archive-enhanced.csv`. This is a comma-separated file on hand. We only need to load it in panda's DataFrame.


- `tweet_json.txt`. We get this file by a little bit more efforts than the other two as it does not intuitively exist. First we must extract the tweet ids from `image-predictions.tsv`. Then use the ids to acquire the information (i.e. `retweet_count` and `favorite_count`) we need using python's library [Tweepy](https://www.tweepy.org/) to access Twitter's API. Finally we parse the returned results (which is formatted as `JSON`) and extract the information of interest to make our DataFrame.

In the **Assessing phase**, we mainly evaluate the data we collected from the **Gathering phase** and analyze the underlying problems in the data from two perspectives: **data quality** and **data tidiness** issues, by manual and programatic means. 

We concluded the detailed analytical process in the `wrangle_report.ipynb` notebook or `wrangle_report.html` in the project folder. 

In the **Cleaning phase**, we use various functions in the versatile `pandas` library to accomplish our cleaning work and generate our final clean master dataset and store it as `twitter_archive_master.csv`.

Based on the clean master dataset, we came up with five interesting insights for EDA purpose:


> **1. What are the TOP 10 Tweets favored by most users? And how about the retweets?**

> **2. What are the most common dog names?**

> **3. What are the most common dog_stage in these tweets?**

> **4. What is the ratings distributed like?**

> **5. What are the most common breeds found by the neural network?**

<br>

As per each question, we analyzed, visualized and summarized them in the `act_report.ipynb` or  `act_report.html` in the project folder.

 ---

## Dependent Libraries
- [pandas](https://pandas.pydata.org/)
- [NumPy](https://numpy.org/)
- [requests](https://requests.readthedocs.io/en/master/)
- [Tweepy](https://www.tweepy.org/)
- [json](https://docs.python.org/3/library/json.html)

---

## Project Source / Acknowledgement
This project is adapted from **the Data Wrangling Chapter** of <a href='https://www.udacity.com/course/data-analyst-nanodegree--nd002'>___Data Anlalyst___</a> Nanodegree Program from <a href='https://www.udacity.com/'>**Udacity**</a>.