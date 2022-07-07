# Data Wrangling: Twitter - WeRateDogs
## by Dane

## Overview

Since data rarely comes clean, the goal of the project was to use a variety of sources for data and clean it up for use later on.  Specpfically, the goal was to pull data from: an API, csv file, and from a file downloaded from the internet.

This project was intended to collect data from the [WeRateDogs Twitter profile](https://twitter.com/dog_rates?) and to collect it into a CSV file in order some data analysis.  WeRateDogs is a Twitter account that rates people's dogs with a humorous comment about the dog. These ratings almost always have a denominator of 10. The numerators, though? Almost always greater than 10. 11/10, 12/10, 13/10, etc. Why? Because ["they're good dogs Brent."](https://knowyourmeme.com/memes/theyre-good-dogs-brent) WeRateDogs has over 4 million followers and has received international media coverage.

The project consists of 3 different sources for the data:

- **image-prediction.csv**: this is a file provided that has dog breed predictions from 2017 tweets and used a neural network written by Udacity.
- **twitter_master_archive.csv**: this is a file provided by WeRateDogs containing a lot information from the account’s Tweets until August 2017.  This file was further compiled by Udacity.
- **Twitter API (tweepy)**: this was used to pull additional data from the Tweet IDs in the above file. 

### Twitter API (tweepy) use:

- The data pulled using the Twitter API are the tweets’ retweet count and like count.
- Since the update to Twitter’s API (v2), the script is set up to pull it using their basic (free), developer account.  It can take up to 2 hours to run due to the rate limits imposed by Twitter.
- Any tweet where the information was not found, or could not be pulled for some reason, were organized into a Python dictionary for viewing.
- All the information is written to a JSON file to work with and use later on.
- To write to a JSON file, the data pulled from Twitter had to be flattened as it is a Tweet Object that could not be easily written to a JSON.  The tweet_flatten function takes a Tweet Object and returns a dictionary of the tweet ID, retweet count, and tweet likes.
- Beyond the above, there was not much data manipulations that needed to be made.

### image-predictions.csv:

- This file was provided by Udacity and contained dog breed predictions based on the photos uploaded by WeRateDogs.
- This file required minimal data manipulation in order to prepare for analysis.
- The dog breed names contained underscores that were removed and the letter case was standardized to title.
- Additionally, the predictions stated if the prediction was a dog or not as strings “True” and “False”.  Those were converted to Boolean values.

### twitter_master_archive.csv:

- This file contained the bulk the data and the corrections that needed to be made.
- All expanded_urls were corrected 
- All posting sources were sliced to just including the actual source and removed the HTML link tag information.
- The rating numerator was corrected (pulled from Tweet text) to include a decimal and converted to float (vs integer).
- Many string columns contained ‘None’ (as a string) and all those values were corrected to NaN.
- Any retweets or replies were removed from the data.


## Conclusion 

All three sources were combined into a master file and saved to be used for further analysis.  Afterwards, some basic visualizations were prepared and summarized in a small writeup, called [Data Wrangling - Twitter Visualizations](/data-wrangling-twitter-visualizaitons.pdf).

