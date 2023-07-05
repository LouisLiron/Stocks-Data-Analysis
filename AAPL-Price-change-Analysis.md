# AAPL Stock Price Action
Upon conducting an in-depth analysis of the AAPL stocks, a wealth of valuable insights has been extracted. By delving into the intricacies of the data, numerous meaningful observations and trends have come to light. These insights provide a comprehensive understanding of the dynamics and patterns inherent within the AAPL stock market, allowing for more informed decision-making and strategic planning.

```python
#importing necessary libraries 
import numpy as np
import matplotlib.pyplot as plt
import pandas as pd
import seaborn as sns
import warnings 
warnings.filterwarnings("ignore")
```

```python
#load data
df = pd.read_csv('stock.csv', infer_datetime_format=True, parse_dates=True, index_col=1, header=0, dayfirst=True)
df
```





<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Ticker</th>
      <th>Open</th>
      <th>High</th>
      <th>Low</th>
      <th>Close</th>
      <th>Adj Close</th>
      <th>Volume</th>
    </tr>
    <tr>
      <th>Date</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2023-02-07</th>
      <td>AAPL</td>
      <td>150.64</td>
      <td>155.23</td>
      <td>150.64</td>
      <td>154.65</td>
      <td>154.41</td>
      <td>83322600.0</td>
    </tr>
    <tr>
      <th>2023-02-08</th>
      <td>AAPL</td>
      <td>153.88</td>
      <td>154.58</td>
      <td>151.17</td>
      <td>151.92</td>
      <td>151.69</td>
      <td>64120100.0</td>
    </tr>
    <tr>
      <th>2023-02-09</th>
      <td>AAPL</td>
      <td>153.78</td>
      <td>154.33</td>
      <td>150.42</td>
      <td>150.87</td>
      <td>150.64</td>
      <td>56007100.0</td>
    </tr>
    <tr>
      <th>2023-02-10</th>
      <td>AAPL</td>
      <td>149.46</td>
      <td>151.34</td>
      <td>149.22</td>
      <td>151.01</td>
      <td>151.01</td>
      <td>57450700.0</td>
    </tr>
    <tr>
      <th>2023-02-13</th>
      <td>AAPL</td>
      <td>150.95</td>
      <td>154.26</td>
      <td>150.92</td>
      <td>153.85</td>
      <td>153.85</td>
      <td>62199000.0</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>2023-05-01</th>
      <td>GOOG</td>
      <td>107.72</td>
      <td>108.68</td>
      <td>107.50</td>
      <td>107.71</td>
      <td>107.71</td>
      <td>20926300.0</td>
    </tr>
    <tr>
      <th>2023-05-02</th>
      <td>GOOG</td>
      <td>107.66</td>
      <td>107.73</td>
      <td>104.50</td>
      <td>105.98</td>
      <td>105.98</td>
      <td>20343100.0</td>
    </tr>
    <tr>
      <th>2023-05-03</th>
      <td>GOOG</td>
      <td>106.22</td>
      <td>108.13</td>
      <td>105.62</td>
      <td>106.12</td>
      <td>106.12</td>
      <td>17116300.0</td>
    </tr>
    <tr>
      <th>2023-05-04</th>
      <td>GOOG</td>
      <td>106.16</td>
      <td>106.30</td>
      <td>104.70</td>
      <td>105.21</td>
      <td>105.21</td>
      <td>19780600.0</td>
    </tr>
    <tr>
      <th>2023-05-05</th>
      <td>GOOG</td>
      <td>105.32</td>
      <td>106.44</td>
      <td>104.74</td>
      <td>106.21</td>
      <td>106.21</td>
      <td>20705300.0</td>
    </tr>
  </tbody>
</table>
<p>248 rows × 7 columns</p>

```python
#checking for the number of rows and columns
df.shape
```
  (248, 7)

```python
#creating a separate dataframe for AAPL stocks to work on
AAPL = df.query('Ticker == "AAPL"')
AAPL
```
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Ticker</th>
      <th>Open</th>
      <th>High</th>
      <th>Low</th>
      <th>Close</th>
      <th>Adj Close</th>
      <th>Volume</th>
    </tr>
    <tr>
      <th>Date</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2023-02-07</th>
      <td>AAPL</td>
      <td>150.64</td>
      <td>155.23</td>
      <td>150.64</td>
      <td>154.65</td>
      <td>154.41</td>
      <td>83322600.0</td>
    </tr>
    <tr>
      <th>2023-02-08</th>
      <td>AAPL</td>
      <td>153.88</td>
      <td>154.58</td>
      <td>151.17</td>
      <td>151.92</td>
      <td>151.69</td>
      <td>64120100.0</td>
    </tr>
    <tr>
      <th>2023-02-09</th>
      <td>AAPL</td>
      <td>153.78</td>
      <td>154.33</td>
      <td>150.42</td>
      <td>150.87</td>
      <td>150.64</td>
      <td>56007100.0</td>
    </tr>
    <tr>
      <th>2023-02-10</th>
      <td>AAPL</td>
      <td>149.46</td>
      <td>151.34</td>
      <td>149.22</td>
      <td>151.01</td>
      <td>151.01</td>
      <td>57450700.0</td>
    </tr>
    <tr>
      <th>2023-02-13</th>
      <td>AAPL</td>
      <td>150.95</td>
      <td>154.26</td>
      <td>150.92</td>
      <td>153.85</td>
      <td>153.85</td>
      <td>62199000.0</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>2023-05-01</th>
      <td>AAPL</td>
      <td>169.28</td>
      <td>170.45</td>
      <td>168.64</td>
      <td>169.59</td>
      <td>169.59</td>
      <td>52472900.0</td>
    </tr>
    <tr>
      <th>2023-05-02</th>
      <td>AAPL</td>
      <td>170.09</td>
      <td>170.35</td>
      <td>167.54</td>
      <td>168.54</td>
      <td>168.54</td>
      <td>48425700.0</td>
    </tr>
    <tr>
      <th>2023-05-03</th>
      <td>AAPL</td>
      <td>169.50</td>
      <td>170.92</td>
      <td>167.16</td>
      <td>167.45</td>
      <td>167.45</td>
      <td>65136000.0</td>
    </tr>
    <tr>
      <th>2023-05-04</th>
      <td>AAPL</td>
      <td>164.89</td>
      <td>167.04</td>
      <td>164.31</td>
      <td>165.79</td>
      <td>165.79</td>
      <td>81235400.0</td>
    </tr>
    <tr>
      <th>2023-05-05</th>
      <td>AAPL</td>
      <td>170.98</td>
      <td>174.30</td>
      <td>170.76</td>
      <td>173.57</td>
      <td>173.57</td>
      <td>113316400.0</td>
    </tr>
  </tbody>
</table>
<p>62 rows × 7 columns</p>

```python
#Dropping the volume column to make plotting the other values easier because it is way too big
AAPL_without_volume = AAPL.drop('Volume', axis=1)
```
```python
#Plotting a line graph
AAPL_without_volume.plot(figsize=(15, 16))
plt.xlabel('Dates')
plt.ylabel('Values')
plt.title('AAPL_without_volume')
plt.grid()
```

![AAPL1](https://github.com/LouisLiron/Stocks-Data-Analysis/assets/124049051/1ec66c4a-5956-4d0b-9e33-12ec67e98f25)

This graph illustrates a noteworthy trend, indicating a suboptimal start during the initial phase of the year, followed by a distressing decline. However, subsequent observations reveal a gradual recovery, culminating in the attainment of its highest point thus far.

```python
#Visualizing the Volume column in the APPL dataframe
AAPL['Volume'].plot()
plt.xlabel('Dates')
plt.ylabel('Shares/1,000,000')
plt.title('AAPL shares')
plt.grid()
```


![AAPL2](https://github.com/LouisLiron/Stocks-Data-Analysis/assets/124049051/1544a5c0-5844-4a9c-8a09-1a13dec2c6f8)

This graph depicting the shares of AAPL stocks reveals a notable absence of stability. Notably, there are prominent spikes observed in the months of March, mid-April, and the end of May.

```python
round(AAPL['Volume'].describe(), 0)
```

**Results**

|count|62.0|
|------|------|
|mean | 60,282,958.0|
|std  | 14,306,053.0|
|min  | 41,516,200.0|
|25%  | 49,607,025.0|
|50%  | 56,094,550.0|
|75%  | 68,376,175.0|
|max  | 113,316,400.0|


```python
plt.boxplot(AAPL['Volume'], vert=False)
plt.xlabel('Shares')
plt.ylabel('Boxplot')
plt.title('AAPL Volumes Boxplot')
plt.show()
```

**Results**

![image](https://github.com/LouisLiron/Stocks-Data-Analysis/assets/124049051/63099be5-89c6-464b-bfc9-8b161ba10680)

Viewing the boxplot together with the 

```python
AAPL['Volume'].hist()
plt.xlabel('Shares/100,000,000')
plt.ylabel('Frequency')
plt.title('Volume/shares histogram')
plt.show()
```

**Results**

![image](https://github.com/LouisLiron/Stocks-Data-Analysis/assets/124049051/b67a185c-adb7-4e7c-aff9-ba421b305930)

```python
import seaborn as sns
sns.set(style='ticks', palette='deep')
from matplotlib import style
## AAPL Histogram
style.use('ggplot')
plt.hist(AAPL['Close'], color = 'blue', histtype = 'bar', rwidth=0.8)
plt.xlabel('Values')
plt.ylabel('Frequency')
plt.title('Stock Prices histogram')
```
**Results**

![image](https://github.com/LouisLiron/Stocks-Data-Analysis/assets/124049051/70a73064-4c7f-43c3-a168-15c9cf7d0228)

Let's begin by understanding the insights that histograms can provide. A histogram allows us to identify subgroups or clusters within a dataset, determine the central tendency or mode, and assess the skewness of the data.

Regarding subgroups or clusters, the histogram displays two prominent clusters on the chart: one centered around $153 and another around $166. This indicates that these regions serve as central points for the clusters, with the majority of prices concentrated around them.

In terms of the mode, it is evident that each cluster has a bar with the highest frequency. This bar represents the mode of that particular cluster, highlighting the central point around which most prices are concentrated.

Assessing the skewness of the data becomes challenging due to its bimodal nature. To resolve this issue, we can calculate the skewness of the dataset below;

```python

from scipy.stats import skew
skewness = skew(AAPL['Close'])
print('Skewness :', skewness)

```
**Results**

Skewness : 0.02853740556215772

Based on the obtained results, it can be concluded that the dataset exhibits a minimal positive skewness. The skewness value of 0.0285 indicates a very slight deviation from perfect symmetry. This subtle skewness is evident in the corresponding boxplot, where the median line shows a slight shift towards the left, and the right whisker appears marginally longer. The relatively small magnitude of 0.0285 reinforces the observation of this minor skewness effect.


```python
# Create a box plot
plt.boxplot(AAPL['Close'], vert=False)
plt.title("Box Plot of Bimodal Data")
plt.ylabel("Values")
```

![image](https://github.com/LouisLiron/Stocks-Data-Analysis/assets/124049051/fdb3ffc9-6ab4-46e5-b3f6-c1218930d7d4)

Upon examining the boxplot, it is apparent that there are no marks or points beyond the whiskers. This signifies the absence of outliers in the dataset. The lack of any data points outside the whiskers indicates that all values fall within a reasonable range, without any extreme or unusual observations.


~~~SQL
--viewing the date range 
SELECT 
    CAST(MAX(Date)AS date) AS Max_date,
    CAST(MIN(Date)AS date) AS Min_date, 
    CONCAT(CAST(MAX(Date)-MIN(Date)AS INT), ' ', 'days') AS Date_range
FROM 
    stocks
--The timeframe for the dataset is short but can be worked with.
~~~
**Results**
|Max_date |Min_date |Date_range|
|-----|-----|-----|
|2023-05-05	|2023-02-07	|87 days|


~~~SQL
/*Base table. Changed the names of columns 2, 3 and 6 to avoid mix-ups with built-in functions*/
SELECT Ticker, 
    Months, 
    stocks_Year, 
    Avg_price_per_month,
    COALESCE(ROUND(Avg_price_per_month - LAG(Avg_price_per_month, 1) OVER (ORDER BY Months), 2), 0) AS Monthly_changes,
    CONCAT(ROUND(COALESCE((ROUND(Avg_price_per_month - LAG(Avg_price_per_month, 1) OVER (ORDER BY Months), 2) / Avg_price_per_month) * 100, 0), 2), ' ', '%') AS Pct_change
FROM
(
    SELECT DISTINCT
        Ticker,
        Months,
        stocks_Year,
        ROUND(AVG(Closing_price) OVER(PARTITION BY Months), 2) AS Avg_price_per_month
    FROM
    (
        SELECT
            Ticker,
            MONTH(Dates) AS Months,
            YEAR(Dates) AS stocks_Year,
            ROUND(Closing, 2) AS Closing_price
        FROM stocks
        WHERE Ticker = 'AAPL'
    ) AS sub
) AS sub_outer;
~~~
**Results**
|Ticker|	Months|	stocks_Year|	Avg_price_per_month	|Monthly_changes	|Pct_change|
|-----|-----|-----|-----|-----|-----|
|AAPL|	2	|2023|	151.06|	0	|0 %|
|AAPL|	3	|2023|	154.96|	3.9|	2.52 %|
|AAPL|	4	|2023|	165.05|	10.09|	6.11 %|
|AAPL|	5	|2023|	168.99|	3.94|	2.33 %|

Creating a dataframe from the above result

```Python
AAPL_changes = {
    'Ticker':['AAPL', 'AAPL', 'AAPL', 'AAPL'],
    'Month': [2,3,4,5],
    'Year': [2023,2023,2023,2023],
    'Monthly_Price_Avg': [151.06,154.96,165.05,168.99],
    'MoM_Price_Change': [0.0, 3.9,10.09,3.94],
    'MoM_Pct_Change': [0.0,2.52,6.11,2.33]}

AAPL_MoM = pd.DataFrame(AAPL_changes)
AAPL_MoM = AAPL_MoM.set_index(['Month','Year'])

print(AAPL_MoM)
```
**Results**

|Month| Year|Ticker|Monthly_Price_Avg|MoM_Price_Change|MoM_Pct_Change|
|------|------|------|------|------|------|
|2 |2023|AAPL|151.06|0.00|0.0|
|3 |2023|AAPL|154.96|3.90|2.52|
|4 |2023|AAPL|165.05|10.09|6.11|
|5 |2023|AAPL|168.99|3.94|2.33|

```python
# creating subplots

fig,axs = plt.subplots(nrows = 1, ncols = 2, figsize = (15,5))

# Plotting AAPL Metrics

AAPL_MoM['MoM_Price_Change'].plot(kind = 'line', title = 'MoM Price Change', ax = axs[0], ylabel = 'Price Change', marker = 'o', grid=True )
AAPL_MoM['MoM_Pct_Change'].plot(kind = 'line', title = 'MoM Pct Change', ax = axs[1], ylabel = 'Pct Change', marker = 'o', grid=True)
````
**Results**
![immediately1](https://github.com/LouisLiron/Stocks-Data-Analysis/assets/124049051/2196fc44-8efe-4c96-bedb-13b212cebf6a)
The observed patterns in both MoM Price Change and MoM Pct Change exhibit a consistent trend. The data indicates a phase of relatively lower values at the beginning of the year, followed by a gradual upward trajectory. However, this upward movement is accompanied by intermittent drops. These fluctuations illustrate a recurring pattern of increases and subsequent decreases over time.

```python
#plotting the changes in the monthly average separately
AAPL_MoM['Monthly_Price_Avg'].plot(figsize=(5, 5), kind='line', marker='o')
plt.xlabel('Month, Year')
plt.ylabel('Change')
plt.title('Monthly_Price_Avg')
plt.grid()
```
**Result**

![immediately2](https://github.com/LouisLiron/Stocks-Data-Analysis/assets/124049051/2573917a-8890-4fb6-b4e8-6ed75e92c4b3)

In the case of MoM Price Avg, a clear uptrend is evident from the onset of the year, which persistently continues throughout the observed period. This upward trajectory demonstrates a sustained increase, culminating in the attainment of its highest peak. This pattern suggests a positive and consistent growth in average monthly prices over time.
