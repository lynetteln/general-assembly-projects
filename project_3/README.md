## Project 3: Web APIs & Classification

### <u>Problem Statement</u>

Reddit is a platform of over a million communities more commonly known as "subreddits". Each subreddit covers a specific topic. Subreddits work like a forum where users can come together and participate in an online discussion relative to the subreddit.

In this project, we will be building a classifier that uses words to identify subreddits. The two subreddits we will distinguish between are r/BMW and r/teslamotors.

It is a general rule on Reddit that posts made must somewhat pertain to the subreddit it is being posted in. Users may find it difficult to distinguish which subreddit would be more appropriate for them to create a post in. With a classifier that identifies the subreddit based on keywords, it may be easier for the user to identify which subreddit it is more appropriate to make their posting in.

### <u> Methodology </u>
The choice of these two subreddits is rather ambitious given that posts are not text heavy. Only about 20% - 25% of our data used contains selftext - the rest only contain titles.

We will be creating and comparing across 3 models - using both the CountVectorizer and TfidfVectorizer to transform our text across the choices of models.

The models we will be using are:
1) Logistic Regression,
2) Multinomial Naive Bayes Classifier,
3) Bagging Classifier with Decision Trees as Base Estimator

This project will be split up into parts A and B, with 1 and 5 subsections respectively.

<b>Part A:</b>

1. Data Collection

<b>Part B:</b>

1. Data Cleaning

2. Pre-processing & EDA

3. Modelling

4. Evaluation & Conceptual Understanding

5. Conclusion & Recommendations

### <u>Conclusion and Recommendations</u>
The LogReg model with TVEC performed the best in classifying the subreddits.

While it may be difficult to improve our scores for the classification of two highly similar topics, accuracy may be improved if we include a list of specific BMW/Tesla model numbers and names.

Since both subreddits are media-heavy, it may be a good idea to scrape comments as well.
