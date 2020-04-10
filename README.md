# Time Series Demand Forecasting
In this repository, I implement time-series demand forecasting by using LSTM, GRU, LSTM with seq2seq architecture, and prophet models. 
I use Keras framework to construct deep learning models and the Prophet library to implement prophet.  
The dataset is the monthly passengers of an International Airline [link](https://raw.githubusercontent.com/jbrownlee/Datasets/master/airline-passengers.csv). The tutorial of the dataset is here [link](https://machinelearningmastery.com/time-series-prediction-lstm-recurrent-neural-networks-python-keras/).

<br>

## Two-layer LSTM regression model
This is the result of using two-layer lstm model. All the implemented code is shown in stacked_lstm_regression.ipynb.  
The training dataset is created by using 12 months as an input to the model and the following next one month as output of the model. 
The result below shows that the model predicts future monthly passengers quite well.  
* RMSE in test period: 22.66
* MAE is test period: 18.28
![](https://user-images.githubusercontent.com/30923675/78865607-dc5d7d00-7a78-11ea-95ea-13a8f25a57c0.png)

## Two-layer GRU regression model
This is the result of using two-layer GRU model instead of using LSTM layers. All the implemented code is shown in stacked_gru_regression.ipynb  
The training dataset is created by using 12 months as an input to the model and the following next one month as output of the model.  
The result below shows that the model predicts future monthly passengers slightly better than the LSTM model.  
* RMSE in test period: 22.47
* MAE is test period: 18.16
![](https://user-images.githubusercontent.com/30923675/78866401-41fe3900-7a7a-11ea-985f-75fdb9ddcd7b.png)

## Seq2seq two-layer LSTM model
This is the result of using LSTM model with seq2seq2 (Encoder+Decoder) architecture. This model is motivated by a paper *Deep and Confident Prediction for Time Series at Uber* [blog](https://eng.uber.com/neural-networks-uncertainty-estimation/) [paper](https://arxiv.org/pdf/1709.01907.pdf). All the implemented code is shown in seq2seq_lstm.ipynb  
The training dataset is created by using from *t* to *t + 12* months as an input to the encoder, from *t + 6* to *t + 12* months as an input to the decoder, and from *t + 13* to *t + 18* months as an output of the decoder.  
The result is evaluated on the RMSE and MAE of both the following next month and in the 6 months.

### 1. Result of predicting the following next month passengers.
Note that the test period is diffrent from other models.
* RMSE in test period: 19.38
* MAE is test period: 15.97
![](https://user-images.githubusercontent.com/30923675/78984666-caa3d480-7b61-11ea-9f9e-78534a44cf8b.png)

### 2. Result of predicting in the 6 months passengers.
Note that the test period is diffrent from other models.
* RMSE in test period: 21.51
* MAE is test period: 18.21
![](https://user-images.githubusercontent.com/30923675/78984671-cd9ec500-7b61-11ea-94dd-23def3eb7735.png)

## Prophet library
Finnaly I implement the OSS library, *[prophet](https://facebook.github.io/prophet/)*. Prophet, which is developed by Facebook, is a procedure for forecasting time series data based on an additive model where non-linear trends are fit with yearly, weekly, and daily seasonality, plus holiday effects.  
The result is much worse than using LSTM or GRU models. The figure below indicates that prophet could not predict the incresing trend of the amplitude.
* RMSE in test period: 40.36
* MAE is test period: 31.17
![](https://user-images.githubusercontent.com/30923675/78988604-5f133480-7b6c-11ea-8285-d5e24401a5c7.png)