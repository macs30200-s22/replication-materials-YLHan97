# The Influence of Investor Sentiment on Stock Volatility: Empirical Tests from the Financial Social Media Platform

## Project Workflow

The code is written in Python 3.8.12 and all of its dependencies can be installed by running the following in the terminal (with the `requirements.txt` file included in this repository):

```
pip install -r requirements.txt
```

### Step 1: Data Collection (in the folder `Data`)
- Social Media Data: 10 target companies' text data (posts). The data is in the folder `Data/scrapped_data`.
  - Using data crawler `scraper_stocktwits.ipynb`, collecting the data of each stock's posts, date, user id and trading decision from StockTwits.
  - `stocks`: 10 folders, included 10 target companies’ posts in json.file and Jupiter notebook of json merger 
	- file name: stocks/AAPL/453309404.json
  - `posts_data`: 10 json files, organized posts in one json.file
	- file name: posts_data/posts_aapl.json
  - `polarity_data`: 10 csv files, using `polarity_sentiment_analysis.ipynb` to calculate polarity, and the files include each post’s polarity
	- file name: polarity_data/polarity_aapl.csv
  - `analysis_data`: 10 csv files, using “data_analysis_30200.ipynb” to calculate daily polarity and combine VIX daily close price into the file. Using this files to do grander causality test and time series analysis in “data_analysis_30200.ipynb”
	- file name:  analysis_data/analysis_aapl.csv  
- Stock Volatility Data (`VIX.csv`): VIX's historical data, which is downloaded from Yahoo Finance.


### Step 2: Sentiment Analysis
- Sentiment Analysis for this project uses Harvard IV-4 sentiment dictionary as frequency dictionaries by applying Python library `pysentiment2`.
  - Calculate each post's polarity by using `polarity_sentiment_analysis.ipynb`

### Step 3: Time Series Analysis
- The reseach involved Granger Causality Test and Vector Autoregression model to investigate the casual and correlation relation between investor sentiment and stock volatility. 
  - Data Analysis: `final_data_analysis_multivariable_30200.ipynb`

## Finding 1
As the Figure 1 shown, there is strongly lagging and unidirectional causal relation between the investor sentiment and the volatility of the stock; however, for the stock in consumer cyclical, stock volatility causes its investor sentiment. 

<img src="./Data%20Visualization/Granger Causality Test Result.png" width="70%" height="70%">

To prove the causal relation is unidirectional, the study take "msft" as an example.

<img src="./Data%20Visualization/Granger Causality for msft.png" width="30%" height="30%">


## Finding 2
Based on the result of VAR model, the investor sentiment is correlated with the stock volatility, but the results of stocks in different sectors are inconsistent. Specifically, investor sentiment of stock in communication services sector tends to have positive correlation with stock volatility. And, there is negative correlation between the investor sentiment of stock in consumer defensive sectors and stock volatility. However, for stocks in technology sectors, their investor sentiments have both positive and negative correlation relation with stock volatility. 
<img src="./Data%20Visualization/Features Correlating Result.png" width="45%" height="45%">


## How to Cite
```
@software{YLHan97,
  author       = {Yulun Han},
  title        = {macs30200-s22/replication-materials-YLHan97},
  month        = apr,
  year         = 2022,
  publisher    = {Github},
  journal      = {Github repository},
  howpublished = {\url{https://github.com/macs30200-s22/replication-materials-YLHan97}},
  commit       = {}
}
```
