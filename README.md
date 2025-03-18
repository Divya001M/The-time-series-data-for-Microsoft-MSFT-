**MSFT Weekly Time Series Analysis**

**Project Overview**

This project analyzes and visualizes the weekly time series data for Microsoft (MSFT) using data retrieved from the Alpha Vantage API. The goal is to identify trends, patterns, and key performance indicators over a specified period. The visualizations provide insights into stock performance, aiding in investment decision-making and market behavior analysis.

**Data Source**

The data is obtained from the Alpha Vantage API, specifically using the TIME_SERIES_WEEKLY function to extract weekly stock performance details.

**Features and Analysis**

**1. Data Extraction & Transformation**

-Fetching weekly time series data for MSFT.

-Converting JSON response into a Pandas DataFrame.

-Formatting and renaming columns for easier access.

-Converting data types to float for numerical computations.

2.**Data Analysis**

-Calculating 4-week and 12-week moving averages.

-Computing weekly percentage change in closing prices.

3.**Data Visualization (Using Matplotlib in Databricks)**

-Closing Prices & Moving Averages: Plotting weekly close prices alongside 4-week and 12-week moving averages to identify trends.

-Trading Volume: Visualizing weekly trading volume to analyze investor activity and market sentiment.

**Key Insights from Analysis**

-Trend Identification: Moving averages help smooth fluctuations and reveal underlying stock trends.

-Market Volatility: Sudden spikes in trading volume often indicate significant price movements or market events.

-Investor Sentiment: High trading volumes can indicate strong investor interest, either bullish or bearish.

-Support & Resistance Levels: Volume trends help validate stock support and resistance levels.

-Comparative Analysis: Comparing current volumes with historical averages aids in evaluating market activity.

**Technologies Used**

-Python (Pandas, Matplotlib, JSON, Requests)

-Databricks (for analysis & visualization)

-Alpha Vantage API (Stock Market Data)

**Out Put**

![image](https://github.com/user-attachments/assets/09abff55-53d3-416a-bedf-466f9563eced)

![image](https://github.com/user-attachments/assets/ae614268-7d4e-4870-8870-b79ff685907b)
