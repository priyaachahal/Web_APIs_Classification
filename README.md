#  Project 3 - Web APIs & Classification
-------------------


## Executive Summary

Like any other country, Singapore is also having an increasing depression rate among people. Therefore, in this classification problem, I will be trying to find the common and distinct words used by people who has anxiety or depression. 

This is a binary classification problem.

I will explore the data and train/test multiple classifier models on the collected data for best performance.

The project concludes with recommendations on the best performing classifier model.

In this project, I will be :
1. Using Reddit's API, to collect posts from two subreddits (Depression and anxiety).
2. I'll then use NatutalLanguageProcessing (NLP) to train a classifier to predict which subreddit a given post came from. <br>Thus helping to understand the relationship between the words used and the sentiments.<br>This will further help in understanding that the given person suffers from anxiety or depression.

### Contents:
- [Data Cleaning](#Data-Cleaning)
- [Exploratory Data Analysis](#Exploratory-Data-Analysis)
- [Exploratory Visualizations](#Exploratory-Visualizations)
- [Pre-processing](#Pre-processing)
- [Modeling](#Modeling)
- [Conclusion](#Conclusion)
- [Recommendations](#Recommendations)

### The Dataset:
We will be collecting our data by web scraping two Reddit API's (https://www.reddit.com/).<br>
The two API's I have used in this project are:<br>
1. Anxiety (https://www.reddit.com/r/Anxiety)
2. Depression (https://www.reddit.com/r/depression)

# Problem Statement 

To build a classifier model, to predict that the given post belongs to which subreddit: (Depression or Anxiety).
<br>And to identify the common and distinct words which will help in predicting the subreddit correctly.

This model will also help in detecting whether a person has depression or it is anxiety.

For this project, I will be using below vectorizers (NLP):
1. Count Vectorizer
2. Tf-tdf Vectorizer

The classifier models used are:
1. Naive Bayes
2. Logistic Regression

# Data Cleaning
- The duplicates were dropped from the dataset.
- The **title** and **selftext** featires were concatenated since, they both describe the post.

# EDA
- Common and distinct words were identified and visualized.
- The affect of removing stopwords was also considered.

# Pre-processing
- The stopwords were removed from the dataset.
- Lemmatizer and stemmer affect was studied and choice was made of Lemmatizer.

# Modeling

Baseline score was established to compare further models to it.

Below models were explored:
1. Count Vectorizer + Naive Bayes Model
2. Tf-idf Vectorizer + Naive Bayes Model
3. Count Vectorizer + Naive Bayes Model (with Gridsearch)
4. Tf-idf Vectorizer + Naive Bayes Model(with Gridsearch)
5. Count Vectorizer + Logistic Regression Model (with Gridsearch)
6. Tf-idf Vectorizer + Logistic Regression Model(with Gridsearch)

The final decision of model was based on below matrics:
1. Accuracy
2. ROC curve-AUC score
3. Sensitivity & Specificity (Confusion Matrix)


# Conclusion and Recommendation

#### LogisticRegression Vs Naive Bayes

My choice between these models will be **LogisticRegression**. 

Reasons for choosing LogisticRegression:
- _The drop of accuracy between training and testing set is more in LogisticRegression than Naive Bayes, but it is still accpetable as there is not much difference._
- _The **accuracy score** (for testing data) for LogisticRegression model is better than Naive Bayes._
- _The **AreaUnderCurve** is more in LogisticRegression than Naive Bayes._

#### CountVectorizer+LogisticRegression Vs Tf-idfVectorizer+LogisticRegression

My choice will be CountVectorizer+LogisticRegression because:
- _The **AreaUnderCurve** is more in CountVectorizer (0.942) as compared to Tf-idfVectorizer (0.934).
- _The **specificity** is same for both_.
- _The **senstivity** is more for CountVectorizer (~0.9) as compared to Tf-idfVectorizer (0.87). This is supported by the less number of False Negatives (Type2) errors._

So, the selected **final** model will be : **CountVectorizer + LogisticRegression** model.


>**With the help of this classifier model, we will be able to detect that the given post belongs to which subreddit (depression or anxiety).**

**Industry implementation of this classifier:** This classifier will help to understand whether a person has depression or not based on the words used by him/her. Eg: In a psychiatrist session.

And thus, helping to take appropriate measures to help the person.

# Limitations

There are some limitations also to this model:
1. The model is based on only on approx 2000 posts that have been read from Subreddits. This is only 1 source and thus posing limitation on the modeling.
2. Not everyone who has depression, posts or uses Reddit.
3. People are not open or willing to discuss about their depression due to fact that depression is still considered as a social stigma (Some people still link depression to mental illness). 
4. Reddit.com is an American website, therefore, the data is more relevant to American population.
5. Extending the above point, people in different regions have some specific language words. Thus our model, is limited to plain English language. It can't understand/process the local words.
6. The data available on Reddit doesn't have information like Age, thus making it hard to understand if there is any given pattern that leads to depression.


