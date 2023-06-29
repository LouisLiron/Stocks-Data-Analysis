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

The count value of 248 indicates that there are 248 data points or entries in the dataset. The mean represents the average value for each column, while the standard deviation (std) measures the variability or dispersion of the data.

The min and max values represent the minimum and maximum values observed for each column, respectively. The quartiles (25%, 50%, 75%) divide the data into four equal parts, with the median (50%) representing the middle value.

Since we previously analyzed the AAPL stocks separately, let's now shift our focus to the MSFT stock and examine its performance on a graph.


### MSFT

![image](https://github.com/LouisLiron/Stocks-Data-Analysis/assets/124049051/2745b9bf-f406-4312-9680-6bce30a5f144)

Based on the graph, we can observe that the MSFT stock initially had relatively lower prices and reached its lowest points in the beginning of March. However, there was a notable shift in the middle of March, leading to a consistent upward trend in stock prices. The prices continued to rise steadily, reaching their highest points in early May. Overall, the graph demonstrates a clear upward trend in the performance of the MSFT stock.

![image](https://github.com/LouisLiron/Stocks-Data-Analysis/assets/124049051/cec3fd78-1dd2-48a4-8351-7d4f3953a013)

It's worth noting that a low stock price can sometimes lead to an increase in demand for the stock, especially if investors perceive it as undervalued. This increased demand may lead to a rise in the stock price over time. However, the increase in price does not directly produce more shares for the ticker; it reflects changes in market sentiment and investor demand. Over here it can be clearly noticed that, when the prices of the stocks go up, the shares of the ticker go up in accordance. When stock prices decrease, it generally indicates a decrease in investor confidence, negative market sentiment, or unfavorable news or events surrounding the company or the broader market. Investors may sell their shares, leading to downward pressure on the stock price.

### NFLX

The next will be NFLX; 

![image](https://github.com/LouisLiron/Stocks-Data-Analysis/assets/124049051/63d8390d-2f14-4c35-9f9a-748880fcc54e)

During the observed timeframe, the stock prices of NFLX began on a positive note, reaching high levels initially. However, they gradually declined until reaching their lowest point in the middle of March. Subsequently, there was a period of slow and gradual increases in early April. However, momentum slowed down, and for the remainder of the time period, the prices experienced small drops.

![image](https://github.com/LouisLiron/Stocks-Data-Analysis/assets/124049051/0acfefe7-687b-4062-b4d4-d30013af0c60)

When examining the relationship between shares and prices of NFLX, three notable spikes in the number of shares bought can be observed. The first spike took place at the beginning of March when the stock prices were on a downward trend, although still at relatively high levels. The next spike occurred towards the end of March, coinciding with a period of consistent upward movements in stock prices. The most recent spike occurred in mid-April, aligning with a favorable pricing period.

It's worth noting that throughout this timeframe, the prices of NFLX stocks have not fallen below 285, indicating that investors maintain confidence in the stock ticker. This suggests that despite fluctuations, the stock has retained a certain level of stability and attracted continued investor interest.

### GOOG

![image](https://github.com/LouisLiron/Stocks-Data-Analysis/assets/124049051/dd5640be-453d-4fba-8b71-1f7131ca590f)

The GOOG stocks exhibit a similar pattern to the NFLX stocks. Throughout the observed timeframe, the GOOG stock prices started on a positive trajectory, initially reaching high levels. However, they gradually declined until reaching their lowest point in the middle of March. Following this, there was a period of slow and gradual increases in early April. However, the momentum slowed down, and for the rest of the timeframe, the prices experienced minor drops.


![image](https://github.com/LouisLiron/Stocks-Data-Analysis/assets/124049051/9a898b9f-0b6f-4176-95ad-c17480d47911)

The GOOG stocks displayed two notable spikes during the observed period. The first spike occurred when the stock prices were at a high level, indicating a strong investor confidence, which resulted in a significant increase in the number of shares bought. The second spike took place in the middle of March when the prices had undergone a significant drop but were in the process of recovering with positive movements.

Following these spikes, the subsequent shares bought remained below 50,000,000, indicating relatively lower buying activity compared to the earlier spikes.


## Conclusions

- An observed trend is that whenever stock prices were high, there was a corresponding increase in the number of shares bought. This can be attributed to investors' confidence in the stock ticker during these periods. Another instance where an increase in stock price was observed was when prices showed a steady upward trend, indicating positive market sentiment and potentially attracting more investors to purchase shares.

- One potential strategy for determining the optimal time to buy shares of a ticker is to consider two factors: high prices and an upward trend. When stock prices are high and displaying a consistent upward trend, it can be seen as a potential signal to buy and hold shares of that particular company.

High prices suggest positive market sentiment and demand for the stock, while the upward trend indicates that the stock has been steadily appreciating in value over time. Combining these two factors may indicate that the company is performing well and has positive prospects for future growth.

However, it's important to note that investing in stocks involves various risks and uncertainties, and timing the market perfectly is difficult. It's advisable to conduct thorough research, analyze the company's fundamentals, and consider other relevant factors before making any investment decisions.

## Happy investing!!!

