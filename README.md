# 🚗 TESLA Stock Price Prediction Project

## 📍 Quick Links
- [What is this Project about?](#1-what-is-this-tesla-stock-price-project-about)
- [The Business Problem](#2-the-business-problem-can-we-generalize-and-predict-future-tesla-stock-prices)
- [Why ML Models are Not Realistic](#3-problem-using-machine-learning-ml-models-to-predict-many-future-daily-prices-is-not-realistic)
- [Improved Time Series Approach](#4-improved-approach-using-time-series-models-to-forecast-future-monthly-prices)
- [Methodology](#5-the-methodology-of-what-i-did)
- [Technical Log](#6-technical-log)
  
---

## 1. ⭐ What is this Tesla Stock Price Project about?

In this project, we will try to find ways to visualize Tesla stock price trends and forecast stock prices. This can be useful for someone who wants to figure out if he should keep his/her stocks or sell them to assist in long term investment strategies.  More specifically, this project will use 2016 to 2025 Tesla Stock Prices from the NASDAQ website.

For the most current NASDAQ Tesla stock prices, here is the website: https://www.nasdaq.com/market-activity/stocks/tsla/historical?page=1&rows_per_page=10&timeline=y10

As a bonus, this project will have a crash course for Time Series data and models! If you never worked with Time Series or need a refresher, this project can help you!

---

## 2. 💵 The Business Problem: Can we generalize and predict future Tesla Stock Prices? 

Tesla stock prices are known to be extremely volatile.

* Can we observe their trends and seasonality?
* Can we possibly make business insights from them?
* Are there some time series models that can make reasonable forecasts? 


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


---
## 4. 💡 Improved Approach: Using Time Series Models to forecast future monthly prices.

* **Q:** Can we get long term predictions without "future" data? 

* **A:** Yes! We can use Time Series models to forecast long-term stock prices! And most time series models do NOT require future data! It will automatically forecast future stock prices.

* We should also use **monthly** Tesla stock prices since we can detect seasonality and trends more effectively. Daily stock prices may have noise or be biased depending on the day. Furthermore, monthly stock prices are more parsimonous (more simple to understand). It would be easier to interpret 12 monthly data points vs 365 daily data points. 

### First Strategy
My training set contained 2016 to 2024 **monthly** stock prices. The testing set contained 2025 **monthly** stock prices. 

But after fitting many time series models, it appears that the year of 2025 was significant and needed to be included in the training set in order to forecast well.
For instance, the AIC/BIC values of SARIMA actually became lower if the 2025 monthly prices got included in the training data. (Lower AIC/BIC scores indicate better model fit.)

### Second Strategy
I then decided to make my training set based on all the 2016 to 2025 **monthly** Tesla Stock price. I then forecasted the next 3 years.

Using the Second Strategy, here are some Time Series models and their forecasts!



### Plot of Time Series Data for 2016 to 2025 Monthly Tesla Stock Prices

[insert regular time series data plot here]

Models are not necessary to gain insights! Just looking at the data can give us insights!

**Monthly Patterns:**

* January appears to have the largest spikes in stock prices.

* Spring months tend to decrease in stock prices.

* Summer to late winter months tend to increase in stock prices.


**Business Insights:**

* Based on these trends, an investor might consider buying during early spring months when prices are lower and selling during summer or late winter months when prices tend to peak.

* WARNING: Tesla stocks are highly volatile. These patterns are not guaranteed and should not be relied on as a definitive trading strategy.  


### SARIMA:

Here is a plot of the SARIMA model with its prediction intervals and forecasted values:

[plot of 2nd SARIMA model]

The SARIMA model's parameters are: $ARIMA(2,1,2) \times (2,0,0)_{12}$  (More details of how to intepret these parameters are in the project.)       


### Prophet:

Here is a plot of the SARIMA model with its prediction intervals and forecasted values:

[plot of PROPHET model]

Prophet automatically handles trends and seasonality of this data, so we do not have to worry about any configurations!

Here is the Prophet time series model formula:

$$\hat y_t = \hat m_t + \hat s_t + \hat h_t$$

Where:

* $\hat y_t$: The predicted/forecasted value at time $t$.

* $\hat m_t$: The predicted trend.

* $\hat s_t$: The predicted seasonal component.

* $\hat h_t$: The predicted holiday effect. (This is optional.) 

### Space-State Model:

[plot of Space-State Model]


This Space-State model is set to consider a local linear trend.


---
## 5. 📔 The Methodology of what I did: 

### Firstly, I did Exploratory Data Analysis.

I did feature engineering to create new predictor variables such as $\text{Daily Range} = High - Low$ (Where $High$ represents the highest stock price in a day, and $Low$ represents the lowest stock price in a day.) 

Plots of predictor variables against response variables were made.
Additionally, predictor variables against other predictor variables were made.

### Secondly, Regression ML models and Time Series models were created.
  
* **Stack:** Python (NumPy, pandas, matplotlib, seaborn, scikit-learn, XGBoost, Statsmodel, Prophet)

### Thirdly, I gathered insights and discoveries from ML models, Time Series models, and Time Series data. 

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
