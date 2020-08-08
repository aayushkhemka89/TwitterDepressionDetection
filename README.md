# TwitterDepressionDetection
Detect depression in tweets from Twitter using Keras 

### Retrieving Test Data


There are two kinds of tweets that are needed for this project: random tweets that do not indicate depression and tweets that show the user may have depression. The random tweets dataset can be found from the Kaggle dataset [twitter_sentiment](https://www.kaggle.com/ywang311/twitter-sentiment/data). It is harder to get tweets that indicate depression as there is no public dataset of depressive tweets, so in this project tweets indicating depression are retrieved using the Twitter scraping tool [TWINT](https://github.com/haccer/twint) using the keyword `depression` by scraping all tweets in an one day span. The scrapped tweets may contain tweets that do not indicate the user having depression, such as tweets linking to articles about depression. As a result, the scrapped tweets need to be manually checked for better testing results. A csv file of scrapped tweets is provided, however the following code can be used to obtain depressive tweets for this project, keep in mind that the date in the code should be changed and the generated .csv file should be manually checked and moved to the project directory:
```sh
twint -s depression --since 2020-07-15 -o depressive_tweets_processed.csv --csv
```

#### Test Data Split
Collected tweets are split into training, testing, and validation sets with a ratio of 60%:20%:20%.

|               | Depressive Tweets           | Normal Tweets  |
| ------------- | --------------------------- | -------------- |
| Training      | 3600                        | 6000           |
| Validation    | 1200                        | 2000           |
| Testing       | 1200                        | 2000           |
| Total         | 6000                        | 10000          |

### Required Libraries
* ftfy - fixes Unicode that's broken in various ways
* gensim - enables storing and querying word vectors
* keras - a high-level neural networks API running on top of TensorFlow
* matplotlib - a Python 2D plotting library which produces publication quality figures
* nltk - Natural Language Toolkit
* numpy - the fundamental package for scientific computing with Python
* pandas - provides easy-to-use data structures and data analysis tools for Python
* sklearn - a software machine learning library
* tensorflow - an open source machine learning framework for everyone

In addition, the pretrained vectors for the Word2Vec model is from [here](https://s3.amazonaws.com/dl4j-distribution/GoogleNews-vectors-negative300.bin.gz).

