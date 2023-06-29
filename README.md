# Stocks-Data-Analysis

## Description

This project performs data analysis on the stock price action of several large-cap companies over a specific time period. The EDA uses the pandas, numpy, and matplotlib.pyplot packages to load the data, clean it, and visualize it. The results of the EDA are available in the Stocks-Exploratory-Analysis-Python.ipynb File.

## Variables
- Ticker: The stock symbol, such as "AAPL" for Apple Inc.
- Date: The date of the stock trade, in the format "YYYY-MM-DD".
- Open: The opening price of the stock on the given date.
- High: The highest price of the stock on the given date.
- Low: The lowest price of the stock on the given date.
- Close: The closing price of the stock on the given date.
- Adj_Close: The adjusted closing price of the stock, which takes into account dividends and stock splits.
- Volume: The total number of shares traded on the given date.

## Objective
1. Conduct an in-depth analysis of the data to identify and understand the prevailing trends and patterns.

2. Offer valuable insights regarding the performance of AAPL stocks.

## Analysis
1. Conduct an in-depth analysis of the data to identify and understand the prevailing trends and patterns.
First, let's take a look at the descriptive statistics of the dataset in python.

```python
#Gives a descriptive statistics about the data
round(df.describe(), 1)
```
**Results**

|      |Open	|High|	Low|	Close	|Adj Close|	Volume|
|------|------|------|------|-------|-------|------|
|count	|248.0	|248.0	|248.0	|248.0	|248.0	|248.0|
|mean	|215.3	|217.9	|212.7	|215.4	|215.4	|32,082,104.0|
|std	|91.7	|92.9	|90.1	|91.5	|91.5	|22,335,898.6|
|min	|89.5	|90.1	|88.9	|89.4	|89.4	|2,657,900.0|
|25%	|135.2	|137.4	|134.8	|136.3	|136.3	|17,141,800.0|
|50%	|208.8	|212.6	|208.2	|209.9	|209.9	|27,340,000.0|
|75%	|304.2	|307.6	|295.4	|303.9	|303.9	|47,717,725.0|
|max	|372.4	|373.8	|361.7	|366.8	|366.8	|113,316,400.0|

