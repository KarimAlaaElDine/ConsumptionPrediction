# Consumption Prediction for homes

This is a part of a larger project for a recommendation system for buy/selling energy in homes equipped with solar panels and a smart home system specifically Home Assistant.


# Structure

This repository contains the following:

 - *consumption_pred_main.ipynb:* A Jupyter Notebook containing our attempts to create and train a model to predict the consumption on data collected from a user.

 

# Overview

Within this project we go over some different model architectures to enable us to create our model but specifically to utilize RNNs and LSTMs for forecasting purposes as some research suggested.

## Preparation

### Data
The data that was provided was in the form of the 
- *date* :  in the format *YYYY-MM-DD HH:mm:ss
- *state* : energy consumption a float in *KWh
- *metadata_id*:  a key used to relate this table to other data on Home Assistant
- *sum*: an accumulative value of consumption 

### Formatting
Both the *metadata_id* and *sum*  where irrelevant to our model and so were dropped. 
the *sum* column was scaled to between 0 and 1
The data was restructured into arrays of 24 representing lag features


## Results
### RNN
For the RNN based model we used 3 layers and created a model that would predict one day ahead in this case. The Validation MSE was 2.9931e-04.

### LSTM
For the LSTM we used 4 layers as for this model we aimed to create a 24 hour forecast. The Validation MSE was 3.8724e-05 which was an expected improvement as the background for this project was based on the accuracy gains possible by converting to LSTM instead of RNNs.
Once plotted against the real values however, the predictions were subpar.

We regularization to prevent any possible over fitting but the results were not improved.
