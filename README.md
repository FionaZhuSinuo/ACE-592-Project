# ACE-592-Project

# Project Description:
This project consists in analyzing data from the famous subreddit WallStreetBets (WSB). In this subreddit, participants discuss option and stocks trading. It became popular in 2021 for the GameStop (GME) episode, in which users massively bought stocks from this company, increasing its price artificially and causing bilions in losses to the hedge funds shorting GME.

To run the code, it is necessary to move data files to the same directory than the Jupyter Notebook file. The packages that figure in the first cell must be installed. The code will automatically read all files and compute the correlation matrix between the sentiment scores of the WSB posts and the change in stock price for the most commented companies in WSB.

The code will first start by reading the screener file, which includes the names and the symbols for all the 8000+ companies quoted in the stock exchanges NASDAQ and NYSE (https://www.nasdaq.com/market-activity/stocks/screener). It will then read the WSB data, obtained through Kaggle (https://www.kaggle.com/datasets/gpreda/reddit-wallstreetsbets-posts). The data includes, among other variables: the title of the post, the score, the number of comments, the timestamp and the body.  

The code follows by creating a regular expression which allows to extract all blocks of text in capital letters, which will be useful for identifying which posts mention companies in NASDAQ or NYSE. Using the countVectorizer, it is determined that GME and AMC are the most commented stocks on the subreddit. 24 different companies are mentioned more than 100 times in the title of the posts. These are the companies which will be used to compute the correlation matrix.

Stock price data for the 24 companies are obtained through https://www.nasdaq.com/market-activity/stocks in .csv format. The data comprises a period of five years (2017-2022) with daily frequency, so the code filters it to include only the period of the WSB posts, which is from September 2020 to August 2021. The stock price data is formatted to include variables of interest, such as the difference of stock price in a day, and the maximum variance.

After that, a sentiment analysis is run on the WSB posts, both in the titles and the body. A sentiment value is assigned for each of the text chunks. For calculating the correlation, this program uses a sentiment score which is based on the sentiment value of both text and body, and the logarithm of the positive votes of the post. This metric attempts to capture the overall sentiment of the WSB community for a given post. The more extreme the sentiment value, and the higher the positive votes, the higher will be the sentiment score. The scores can range from 0 to 348k. The logarithm is used to moderate the impact of this value, as it is unlikely that a stock price will change 10 times more if the post is 10 time more voted.

The script separates all the posts in the data into 24 different dataframes, each of which contains the posts in which one of the 24 companies is mentioned. The correlation matrix is calculated 24 times, for each of these datasets, but the results are just kept for the "sentiment score" row, and merged into a single dataframe for convenience.

Results show that sentiment score has almost no correlation with stock price change, not even with stock price change in the previous day, and in the following day. However, a slight correlation is seen with respect to the trade volume and maximum variance. This can indicate WSB sentiment does not affect change in stock prices or viceversa, but that increase in trade volume or rapid changes in price can trigger passionate reactions in the WSB community.

One of the main limitations of this analysis is the accuracy of the sentiment score. Several posts with a negative score have been identified to be positive towards the stock in consideration. 
Also, further analysis should be done to capture the positive or negative impact of emojis in the sentiment analysis.

# Repository Structure
 - **Write Up**: includes the Python code files called "Reddit.ipynb", "Xide chen.ipynb".
 - **Datasets**: are Documents needed to run code and includes the datasets the above Python code references.
 - **Write Up**: includes the final report for this project and its findings in a document called "Write_Up.docx" on slide links file. 

# Authors
 - Àlex Alonso: aa66@illinois.edu
 - Xide Chen: xidec2@illinois.edu
 - Sinuo Zhu: sinuoz2@illinois.edu

Students at ACE 592 SAE: Data Science for Applied Economics the University of Illinois Urbana-Champaign

It was created to fulfill the requirements for a final group project for a graduate-level course entitled Data Science for Applied Economics taught by Dr. Jared Hutchins at the University of Illinois Urbana-Champaign for the Spring 2022 semester.
