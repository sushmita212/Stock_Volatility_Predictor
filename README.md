# Stock volatility prediction
The stock prices of financial assets vary over time. The degree of variation of the stock price is expressed by volatility. Mathematically, the volatility is equivalent to the standard deviation of the stock price fluctuation over time. Volatily forecasting can be advantageous in trading as it can be used for risk assessment, option pricing, strategy selection etc.

Volatility is usually calculated on returns and not on raw stock prices, because returns capture relative change while prices are absolute. For e.g. the same price change of $10 in a $50 stock and a $500 stock means a price change of 20% and 2% respectivley. Thus we need a scale independent measure of volatility which is obtained by volatility on returns.

<br>
In this repo, we build statistical (GARCH) and machine learning based (LSTM) models to predict volatility of the closig price for IBM stock.
We pull the daily historical stock price data through the alpha vantage API.

## Feature engineering
For both the GARCH and LSTM models we need to perform feature engineering from the raw (open, close, high, low, volume) features. 
<br>
* For the GARCH model we calculate the log return and the rolling standard deviation (volatility). The GARCH model is then built on the historical volatility data.
* For the LSTM model we engineer price-based features, rolling price based features), volume-based features, trading range and technical indicators such as Relative Strength Index (RSI), Bollinger Bands, and Moving Average Convergence Divergence (MACD). 

## Feature selection
Even though we can build a variety of features to build the LSTM model on, a large number of features which may be correlated and may not have enough predictive power may overburden the model and harm it's performance. We therefore perform feature selection using multicolinearity anlysis, and predictive power for the target (rolling volatility). We need to be careful that there is is no data leakage and ensure that we are only using historical data for making the prediction at each time step.

## Data preparation for the LSTM model
We then prepare the data to feed into the LSTM model by scaling the feaures and preparing a sequence of lagged features up to a chosen number of sequence length. 

## Results 
|   |MAE|MSE|R-squared|
|---|----|---|---|
|GARCH|0.26|0.12|0.82|
|LSTM|0.12|0.04|0.96|

