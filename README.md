# Jane Street Market Prediction - AE & MLP
AE & MLP approach to predict real-time financial market data and select the right trades to execute.

## About
Jane Street hosted on Kaggle a code competition of predicting the stock market from February to August 2021 using the past high-frequency trading data. The competition involves predicting whether a trade will be profitable or not given the input. The training data provided contain 500 days of high-frequency trading data, a total of 2.4 million rows. The public leaderboard data contain 1 year of high-frequency trading data from some time before Aug 2020 and up to that. The private ranges from a random time from Summer 2020 up to August 2021. Additional information about the competition can be found on the [Kaggle Competition page](https://www.kaggle.com/c/jane-street-market-prediction).


## Datasets
The dataset is provided by Jane Street and contains an anonymized set of features, feature_{0...129}, representing real stock market data. Each row in the dataset represents a trading opportunity, for which you will be predicting an `action` value (1 to make the trade, 0 to pass on it). Each trade has an associated `weight` and `resp`, which together represents a return on the trade. The date column is an integer that represents the day of the trade, while ts_id represents a time ordering. In addition to anonymized feature values, you are provided with metadata about the features in features.csv. Additional information about the datasets can be found on the [Kaggle Data Description page](https://www.kaggle.com/c/jane-street-market-prediction/data).


## Model Overview
The solution is based on an Autoencoder and Multilayer Perceptrons (MLP). The autoencoder learns a representation (encoding) for a set of data, typically for dimensionality reduction, by training the network to ignore insignificant data in order to minimize the noise. And the MLP predicts profitable trades.


## Metrics
This competition is evaluated on a utility score. Each row in the test set represents a trading opportunity for which you will be predicting an `action` value, 1 to make the trade and 0 to pass on it. Each trade *j* has an associated `weight` and `resp`, which represents a return.

<p align="center">
  <img src="https://render.githubusercontent.com/render/math?math=%5Cdisplaystyle%20p_i%20%3D%20%5Csum_%7Bj%7D%20w_%7Bij%7D%20r_%7Bij%7D%20a_%7Bij%7D," />
</p>

<p align="center">
  <img src="https://render.githubusercontent.com/render/math?math=%5Cdisplaystyle%20t%20%3D%20%5Cfrac%7B%5Csum%20p_i%20%7D%7B%5Csqrt%7B%5Csum%20p_i%5E2%7D%7D%20*%20%5Csqrt%7B%5Cfrac%7B250%7D%7B%7Ci%7C%7D%7D%2C" />
</p>

where \(|i|\) is the number of unique dates in the test set. The utility is then defined as:

<p align="center">
  <img src="https://render.githubusercontent.com/render/math?math=%5Cdisplaystyle%20u%20%3D%20%5Cmin(%5Cmax(t%2C0)%2C%206)%20%20%5Csum_i%20p_i." />
</p>

## Contributing
Github issues and pull requests are welcome. Your feedback is much appreciated!

August 2021, Abdelghani Belgaid
