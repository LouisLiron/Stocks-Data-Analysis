```python
import necessary libraries
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
#Dropping the volume column to make plotting the other values easier because it it way too big
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


    
![png](output_5_0.png)
    



```python
#Visualizing the Volume column in the APPL dataframe
AAPL['Volume'].plot()
plt.xlabel('Dates')
plt.ylabel('Shares/1,000,000')
plt.title('AAPL shares')
plt.grid()
```


    
![png](output_6_0.png)
    



```python
#showing the disribution of data 
fig, axs = plt.subplots(nrows =1 , ncols =2 , figsize = (15,5))

# AAPL Histogram
AAPL['Close'].plot(kind = 'hist', bins = 20, ax = axs[0], title = 'AAPL Histogram')

# AAPL Boxplot 
AAPL['Close'].plot(kind = 'box', ax = axs[1], title = 'AAPL Boxplot',ylabel = 'Price', vert = True)
```
