# Problem Statement

With the rise of social media and the ability to be virtually anonymous on the internet, the number of people that can and do post to the internet has exploded exponentially. There is no automatic fact-checker before posting, there is no one to ensure that everything on the internet is based in truth. While not everyone is out to spread misinformation, there are a number of people who are, whether it be for fun or a serious goal. With this in mind, we aim to create a model that can tell a fake story from a real one.

# Summary

The models are trained on r/nosleep and r/LetsNotMeet. In their own words, here is a quick summary of each subreddit:

r/nosleep: “Nosleep is a place for redditors to share their scary personal experiences. Please read our guidelines in the sidebar/"about" section before proceeding.”

r/LetsNotMeet: “A place to read spine-tingling, unusual, terrifyingly true stories about people you never want to meet again.”

The first subreddit is dedicated to horror stories that are fake, but have just enough details that someone could interpret it as real if they did not know the context; the idea of the subreddit is to treat the story like it is real. The second subreddit is about actual, real-life encounters that go beyond the normal "creepy encounter" and could be a horror story if the reader did not know the context.

After pulling 11,000 posts from January 2017 to July 2021 with the Pushshift API, we created a dataframe from the data and cleaned it. We dropped posts that were removed or deleted and tokenized and lemmatized the posts that were left.

The baseline accuracy we were interested in exceeding was 64.3%. Most models were able to get a higher accuracy, but many of them did have a level of overfitting.

# Workflow

**1. Data collection**<br />
Pulled from chosen subreddits and created dataframe of scrape

**2. Data cleaning, feature engineering**<br />
Dropped all columns except 'subreddit', 'selftext', 'title', dropped certain special characters, dropped submissions that were removed by moderators or deleted by the author. Created column of binary values (1 if the post is a fake story, 0 if it is not), created column combining title and selftext.

**3. Extra data processing, analysis, modeling**<br />
Dropped basic stopwords, tokenized and lemmatized posts and labeled types of words. For modeling: used CountVectorizer in a Random Forest Classifier and Extra Trees Classifier, TF-IDF in a Multinomial Naive-Bayes Classifier, created a Classification and Regression Tree. Performed sentiment analysis to see subreddit polarity

# Conclusions

With an accuracy score of 92.1%, the multinomial Naive-Bayes model performed the best classification, but there is still room for error. Models can classify fake/real stories relatively well, but there will be some that get through. For this reason, it's probably in our best interest to allow for human intervention. While there is a risk that this option will be misused and weaponized, it is still the best path (currently available) to limiting fiction being marketed as reality.

# Files

| File/Folder | Description |
| --- | --- |
| [Scraping](https://git.generalassemb.ly/yeccaluh/project_3/blob/main/scraping.ipynb) | Explained above |
| [Data Cleaning](https://git.generalassemb.ly/yeccaluh/project_3/blob/main/data_cleaning.ipynb) | Explained above |
| [Analysis](https://git.generalassemb.ly/yeccaluh/project_3/blob/main/analysis.ipynb) | Explained above |
| [Presentation](https://git.generalassemb.ly/yeccaluh/project_3/blob/main/Project%203.pdf) | PDF of presentation slides |
| [README.md](https://git.generalassemb.ly/yeccaluh/project_3/blob/main/README.md) | Description of repository and project |
| [data](https://git.generalassemb.ly/yeccaluh/project_3/tree/main/data) | All of the scraped data in its totality is located [here](https://git.generalassemb.ly/yeccaluh/project_3/blob/main/data/total_subreddit_data.csv), the cleaned dataframe is located [here](https://git.generalassemb.ly/yeccaluh/project_3/blob/main/data/clean_subreddit_data.csv) |

# **Sources**

- [r/nosleep](https://www.reddit.com/r/nosleep/)
- [r/LetsNotMeet](https://www.reddit.com/r/LetsNotMeet)
- [Gwen Rathgeber's Subreddit Classification Project](https://github.com/gwenrathgeber/subreddit_text_classification)
- [Epoch Time Converter](https://www.epochconverter.com/)
- [Tokenizing, labeling and lemmatizing](https://towardsdatascience.com/preprocessing-text-data-using-python-576206753c28)
- [Accuracy vs. F1 Score](https://towardsdatascience.com/accuracy-precision-recall-or-f1-331fb37c5cb9)
- [Another Accuracy vs. F1 Score Explainer](https://towardsdatascience.com/a-look-at-precision-recall-and-f1-score-36b5fd0dd3ec)
- [Regex code](https://stackoverflow.com/questions/11331982/how-to-remove-any-url-within-a-string-in-python/49257661)
- [Markdown](https://www.markdownguide.org/cheat-sheet/)

