# Predict-Bond-Sales-Quotes-Acceptance using PYSPARK

<pyspark based implementation>

## Context

The bond sales team requests its data scientists that they would like to have a model that
estimates whether prices quoted to clients in bonds are going to be accepted by them,
therefore resulting in a trade. In this business line, clients can request at any time during the
trading session both buy and sell prices of bonds, for any volume in €. The client might
request quotes from multiple banks at the same time, and therefore will close with the one
that answers the best price (if any of the prices is considered fair by the client). Banks have
no access to the prices quoted by their competitors, they only know the number of
competitors for each request for quote (RfQ) from a client.
For this task, two datasets are provided, in which dataset A contains the information
regarding the request for quote (timestamp, client, volume requested, price quoted by the
bank, number of competitors, …), and dataset B contains intraday historical market
mid-prices of the bonds for which request for quotes are provided in dataset A

## Description of the dataset

### Dataset A: rfqs.csv:
● date_time: date and time at which the quote is requested.
  
● Instrument: the bond for which the customer has requested a price
  
● client: client code (anonymized)
  
● price: price quoted to the client by the bank
  
● mid: market mid-price of the bond captured by the bank's system at the time of the
operation
  
● vol_MM: amount requested by the client (in millions of euros).
  
● dv01: sensitivity of the bond to variations in its yield (a measure of risk of the bond)
  
● num_dealers: number of banks from whom the client has requested a quote
  
● side: 1 if it is buy -1 if it is sell (from the point of view of the bank, not the client)
  
● won: 0 if the bank did not close the operation, 1 if it did.

### Dataset B mids.csv:
● date_time: day and time of the market mid-price of the bond
  
● mid: market mid-price of the bond provided by a data provider with greater reliability
than our platform, sampled with a frequency of 5 minutes
  
● instrument: the bond for which the market price is provided


## Objective

Using these two datasets, build a model that predicts whether the request for quote is going
to be won or not by the bank, given the price quoted and other information provided in the
datasets or derived from them (feature engineering).
Hint: A relevant feature to take into account is the quoted spread. This value is calculated as:
- For a buy: mid - price
- For a sell: price - mid


