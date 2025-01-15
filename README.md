In this repo, we build statistical (GARCH) and machine learning based (LSTM) models to predict volatility of the closig price for IBM stock.
We pull the daily historical stock price data through the alpha vantage API.

# Feature Engineering
For both the GARCH and LSTM models we need to perform feature engineering from the raw (open, close, high, low, volume) features. 
<br>
* For the GARCH model we calculate the log return and the rolling standard deviation (volatility). The GARCH model is then built on the historical volatility data.
* For the LSTM model we engineer price-based features, rolling price based features), volume-based features, trading range and technical indicators such as Relative Strength Index (RSI), Bollinger Bands, and Moving Average Convergence Divergence (MACD). 

