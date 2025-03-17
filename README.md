# The-time-series-data-for-Microsoft-MSFT-
Analyzing and visualizing the weekly time series data for Microsoft (MSFT) that was retrieved using the Alpha Vantage API. 
In this project, I analyze and visualize weekly time series data for Microsoft (MSFT) obtained from the Alpha Vantage API, focusing on trends, patterns, and key performance indicators over a specified period. The visualizations provide insights into stock performance, helping to inform investment decisions and understand market behavior. 
 Load Data into a DataFrame

import pandas as pd

import json

import requests


url = "https://alpha-vantage.p.rapidapi.com/query"


querystring = {"function":"TIME_SERIES_WEEKLY","symbol":"MSFT","datatype":"json"}


headers = {

    "x-rapidapi-key": "263978fb61mshb11546a82627679p10f09cjsne32abb0b7b85",  # Your API key

    "x-rapidapi-host": "alpha-vantage.p.rapidapi.com"

}


response = requests.get(url, headers=headers, params=querystring)



# Assuming 'response' is your API response object

data = response.json()


# Extracting the relevant part of the JSON (the time series data)

time_series = data['Weekly Time Series']


# Convert the JSON to a DataFrame

df = pd.DataFrame.from_dict(time_series, orient='index')


# Convert the index to a datetime object

df.index = pd.to_datetime(df.index)


# Rename the columns for easier access

df.columns = ['open', 'high', 'low', 'close', 'volume']


# Convert data types to float for numerical operations

df = df.astype(float)


# Display the first few rows

df.head()



2. Data Analysis and Transformation 

# Calculate 4-week and 12-week moving averages

df['4_week_MA'] = df['close'].rolling(window=4).mean()

df['12_week_MA'] = df['close'].rolling(window=12).mean()


# Display the first few rows to check the moving averages

df[['close', '4_week_MA', '12_week_MA']].head(10)


 3. Calculate Weekly Percentage Change 

 # Calculate weekly percentage change

df['pct_change'] = df['close'].pct_change()


# Display the first few rows to check the percentage change

df[['close', 'pct_change']].head(10)



4.Visualization Using Databricks 

import matplotlib.pyplot as plt


# Plot the closing prices and moving averages

plt.figure(figsize=(14, 7))

plt.plot(df.index, df['close'], label='Close Price', color='blue')

plt.plot(df.index, df['4_week_MA'], label='4 Week MA', color='red')

plt.plot(df.index, df['12_week_MA'], label='12 Week MA', color='green')


# Adding title and labels

plt.title('MSFT Weekly Close Price and Moving Averages')

plt.xlabel('Date')

plt.ylabel('Price')

plt.legend()

plt.show()



# Plot the weekly trading volume

plt.figure(figsize=(14, 7))

plt.bar(df.index, df['volume'], color='purple')


# Adding title and labels

plt.title('MSFT Weekly Trading Volume')

plt.xlabel('Date')

plt.ylabel('Volume')

plt.show()



The weekly trading volume plot for Microsoft (MSFT) reveals several key insights:

1. Volume Trends: Observing the overall trend in trading volume helps identify shifts in investor interest over time.

2. Volatility Indicators: Sharp spikes in volume often correlate with significant price movements or market events, highlighting periods of heightened volatility.

3. Market Sentiment: High trading volumes can indicate strong investor sentiment—whether optimistic during price rises or pessimistic during declines.

4. Support and Resistance Analysis: Volume can validate support and resistance levels; increased buying at support suggests stronger conviction, while high selling at resistance indicates strong selling pressure.

5. Comparative Analysis: Comparing current volumes to historical averages provides context for assessing activity levels—whether they are above or below average.

6. Correlation with Price Movements: Examining volumes alongside price data can reveal relationships between trading activity and price trends.

7. Long-Term vs Short-Term Trends: Differentiating short-term spikes from long-term patterns aids in identifying strategic accumulation or distribution phases among investors.

In summary, analyzing MSFT's weekly trading volume offers valuable insights into market dynamics, helping investors make informed decisions about their strategies regarding the stock.
