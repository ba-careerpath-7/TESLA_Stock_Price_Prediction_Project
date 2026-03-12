# 🚗 TESLA Stock Price Prediction Project

---

## 1. ⭐ What is this Tesla Stock Price Project about?

In this project, we will try to find ways to visualize Tesla stock price trends and forecast stock prices. This can be useful for someone who wants to figure out if he should keep his/her stocks or sell them to assist in long term investment strategies.  More specifically, this project will use 2016 to 2025 Tesla Stock Prices from the NASDAQ website.

For the most current NASDAQ Tesla stock prices, here is the website: https://www.nasdaq.com/market-activity/stocks/tsla/historical?page=1&rows_per_page=10&timeline=y10


---

## 2. 💵 The Business Problem: Can we generalize and predict future Tesla Stock Prices? 

Tesla stock prices are known to be extremely volatile.

* Can we observe their trends and seasonality?
* Can we possibly make business insights from them?
* Can we make a time series model 


---
## 3. ❗❗❗ Problem: Using Machine Learning (ML) Models to predict many future daily prices is not realistic!

My training set contained 2016 to 2024 daily stock prices. The testing set contained 2025 daily stock prices. 

Linear Regression was the best model out of all models since it had the lowest rMSE (It appears that many of the predictors were linearly correlated).

[insert bar chart of model rMSEs]


Here is a plot of Linear Regression's predicted stock price values for 2025:

[insert linear regression stock price predictions and actual 2025 predictions]


There is one BIG problem. 

* Notice that we have information of each 2025 day! However, how would we predict the stock price days of the year 2026 and onwards? We do not have any 2026 data for that!

* Therefore, using Machine Learning (ML) Models to predict many future daily prices such as the next years or next months is not realistic!


* Perhaps ML models can predict the next day's stock price. Then we could keep training the ML models as days go on by. But this is only short term predictions.

* Can we get long term predictions without "future" data? 


---
## 4. 💡 Improved Approach: Using Time Series Models to forecast future  

My training set contained 2016 to 2024 **monthly** stock prices. The testing set contained 2025 **monthly** stock prices. 

But after fitting many time series models, it appears that the year of 2025 was significant and needed to be included in the training set in order to forecast well.




---
## 5. 📔 The Methodology of what I did: 

### Firstly, I did exploratory data analysis.

Plots of predictor variables against response variables were made.
Additionally, predictor variables against other predictor variables were made.

### Secondly, regression machine learning models and time series models were created.
  
* **Stack:** Python (NumPy, pandas, matplotlib, seaborn, scikit-learn, XGBoost, Statsmodel, Prophet)

### Thirdly, I tried to gather insights about which machine learning model or time series model had the best metric and if we found any discoveries about Tesla Stock Prices. 

For a refresher, check them out at [point 3!](#3--key-insights-and-final-conclusions) 

---
## 6. 💻 Technical Log

<details>
<summary><b> Click this Arrow to expand the Comprehensive Model Library! </b></summary>

Each Model contains:
- A explanation of how the model works.
- The code of the model.
- Insights or results. (Some models such as PCA or Prophet contain visuals.)


### Un-Supervised 🧩:
1. PCA
2. LLE 
3. DBSCAN
4. Isolation Forests


### Regression 📈:
1. Linear Regression
2. Ridge
3. LASSO
4. SVR 
5. Regression Random Forests
6. Regression XGBoost
7. Regression Neural Network 

### Time Series ⌚:
1. SARIMA
2. SARIMAX
3. Prophet
4. State-Space Model


</details> 
