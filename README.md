# Time Series Demand Forecasting
The airline daily passengers are predicted by using LSTM model.

The dataset is based on the International Airline Passengers dataset (https://raw.githubusercontent.com/jbrownlee/Datasets/master/airline-passengers.csv).  
Here is the tutorial of the dataset (https://machinelearningmastery.com/time-series-prediction-lstm-recurrent-neural-networks-python-keras/).

<br>

## Stacked two-layer lstm regression model
* RMSE in test period: 22.66
* MAE is test period: 18.28
![](https://user-images.githubusercontent.com/30923675/78865607-dc5d7d00-7a78-11ea-95ea-13a8f25a57c0.png)

## Stacked two-layer gru regression model
* RMSE in test period: 22.47
* MAE is test period: 18.16
![](https://user-images.githubusercontent.com/30923675/78866401-41fe3900-7a7a-11ea-985f-75fdb9ddcd7b.png)