# Udacity_DS_Recommendation_Engine
- [Project Overview](#Project-Overview)
- [Installation](#Installation)
- [Project Structure](#Project-Structure)
- [Project Components](#Project-Components)

## Project Overview<a name="Project-Overview"></a>
The **Recommendations with IBM** is a part of the Udacity Data Science Nanodegree Program in collaboration with IBM who provides a large number of anonymised data of interactions between all of different kinds of article in the community and users from the IBM Watson Studio platform. The IBM is hoping to use this project to build an application for better understanding their users' tastes in articles and making personalised experience for individual user on articles recommendations.

## Installation<a name="Installation"></a>
The following packages and versions are used in this jupyter notebook. Any recent versions should work. 
`Note: Updating your packages before executing the project is recommended!`

| Package  | Version |
| ------------- | ------------- |
| python  | 3.8.3  |
| pandas  | 1.3.2  |
| numpy   | 1.18.5 |
| matplotlib | 3.1.1|
| nltk    | 3.5|
| plotly  | 4.14.3|
| pickle  | 1.6.0|


## Project Structure<a name="Project-Structure"></a>
```
├── data
│   ├── articles_community.csv-------------------# article information data
│   └── user-item-interactions.csv---------------# user-article interaction history data
├── src
|   ├── project_tests.py-------------------------# tasks evaluation, provided by Udacity
│   ├── Recommendations_with_IBM.html------------# tasks submission in HTML format
│   ├── Recommendations_with_IBM.ipynb-----------# tasks submission in Jupyter Notebok format
│   └── archive----------------------------------# files archived
├── test
│   ├── top_5.p----------------------------------# pickle file with top 5 articles interacted
│   ├── top_10.p---------------------------------# pickle file with top 10 articles interacted
│   ├── top_20.p---------------------------------# pickle file with top 20 articles interacted
│   └── user_item_matrix.p-----------------------# pickle file with user-item interaction matrix saved
│    
```

## Project Components<a name="Project-Components"></a>
There are 5 main components in this project.

### 1. Exploratory Data Analysis
In this section, we provide some insights into the descriptive statistics of the data and answer question in data exploration:
- what is the distribution of how many articles a user interacts with in the dataset?
- the number of unique articles that have an interaction with a user.
- the number of unique articles in the dataset (whether they have any interactions or not).
- the number of unique users in the dataset. (excluding null values)
- the number of user-article interactions in the dataset.
- the most viewed article_id

### 2. Rank Based Recommendations
In this section, since there are no ratings for any of the articles, we make recommendations by evaluating the popularity of an article based on how often an article was interacted with.

### 3. User-User Based Collaborative Filtering
In this section, we look at users that are similar in terms of the items they have interacted with. These items could then be recommended to the similar users. There are some functions generated below:
- function to find similar users based on similarity of their interactions
- function to return article names based on their IDs
- function to return all articles the user interacted
- function that sorts articles by popularity
- function that sorts users by the number of their activity

### 4. Content Based Recommendations
In this section, we look at articles that are similar in terms of the content they have. These articles with a higher similarity score could then be recommended to the target user. The process can be summarised in this orider:
- creating sparse matrix of features (i.e., articles by content tokens) by implementing countvectorizer and tfidf techniques.
- geting articles that the user has already seen, ordered by interaction rank.
- looping these articles and considering each as a group.
- for the each group, finding and ranking articles with a similar content, based on dot product value (i.e., content similarity score) between articles' title.
- filtering similar articles that are still in "Live" status in the article community and articles that user has not seen yet.
- finding the article with the highest similarity score within a group and adding it into the recommendation list.
- for the rest in each group, adding them to a candidates list.
- finally, randomly selecting articles from the candidates (i.e, similar article candidates for all groups) until n recommendations are found.

### 5. Matrix Factorization
In this section, we have implemented Singular Value Decomposition (SVD) approach to build recommendations. We builded out a matrix decomposition by using the user-item interactions. Using the decomposition, we got an idea of how well we can predict new articles an individual might interact with. We finally discussed which methods we might use moving forward, and how we might test how well our recommendations are working for engaging users.
