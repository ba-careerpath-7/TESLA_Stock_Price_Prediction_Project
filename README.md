# 🚗 TESLA Stock Price Prediction Project



--- 
## 🌈 Table of Contents for this Project:

![image alt](https://github.com/ba-careerpath-7/TESLA_Stock_Price_Prediction_Project/blob/018ac5556dfec73625e2e402116bbdc75dcbb9ec/github_tesla_content_table.PNG)

---

## 📍 Quick Links
- [What is this Project about?](#about)
- [The Business Problem](#business)
- [Why ML Models are Not Realistic for Daily Stock Prices](#ml-problem)
- [Improved Time Series Approach for Monthly Stock Pries](#timeseries)
- [Methodology](#methodology)
- [Technical Log](#log)

---

<a name="about"></a>
## 1. ⭐ What is this Tesla Stock Price Project about?

In this project, we will try to find ways to visualize Tesla stock price trends and forecast stock prices. This can be useful for someone who wants to figure out if he should keep his/her stocks or sell them to assist in long term investment strategies.  More specifically, this project will use 2016 to 2025 Tesla Stock Prices from the NASDAQ website.

For the most current NASDAQ Tesla stock prices, here is the website: https://www.nasdaq.com/market-activity/stocks/tsla/historical?page=1&rows_per_page=10&timeline=y10

As a bonus, this project will have a crash course for Time Series data and models! If you never worked with Time Series or need a refresher, this project is for you!

---

<a name="business"></a>
## 2. 💵 The Business Problem: Can we generalize and predict future Tesla Stock Prices? 

Tesla stock prices are known to be extremely volatile.

* Can we observe their trends and seasonality?
* Can we possibly make business insights from them?
* Are there some time series models that can make reasonable forecasts? 


---

<a name="ml-problem"></a>
## 3. ❗❗❗ Problem: Using Machine Learning (ML) Models to predict many future daily prices is not realistic!

My training set contained 2016 to 2024 daily stock prices. The testing set contained 2025 daily stock prices. 

Linear Regression was the best model out of all models since it had the lowest rMSE (It appears that many of the predictors were linearly correlated).

**📊 Bar plot of each 7 regression model's rMSE values:**
<img width="1349" height="718" alt="github_tesla_1" src="https://github.com/user-attachments/assets/55930890-a125-42da-8388-884845379f38" />

**📊 Here is a plot of Linear Regression's predicted stock price values for 2025:**
<img width="1653" height="904" alt="github_tesla_2" src="https://github.com/user-attachments/assets/501ac8c5-dba6-416a-91f7-dbed812e60ab" />

**Why do I not see a straight line?**

* You might have been expecting a straight line like $y = mx+b$ since we used a Linear Regression model.

* However, Linear Regression does NOT account for temporal order. Linear Regression first calculates its predictions based on the predictor values. Next, the graph organizes the predictions by the chronological order.

**Summary of the Graph:**

* It seems like Linear Regression forecasted the daily 2025 stock prices well!
* The red line (predicted values) seems to cover the blue lines (actual values) with great accuracy.

### ❗ There is one BIG problem. 

* Notice that we have predictor variable values of each 2025 day! We have the predictor matrix of $X_{test,2025}$.

* However, how would we forecast the stock price days of the year 2026 and onwards? We do not have any 2026 predictor variable values for that! We do not have the predictor matrix of $X_{test, 2026}!$

* Therefore, using Machine Learning (ML) Models to predict many future daily prices such as the next years or next months is not realistic! It is not realistic to obtain $X_{test, future}$ since we currently live in the present. 

* In the current time, we realistically have $X_{train, past}$ and $X_{test,past}$.

* This project was created around December 2025, so at that time the available predictor matrices are: $X_{train,past} = X_{train,2016-2024}$ and $X_{test,past} = X_{train,2025}$  

* Perhaps ML models can predict the next day's stock price. Then we could keep training the ML models as days go on by. But this is only short term predictions.


---

<a name="timeseries"></a>
## 4. 💡 Improved Approach: Using Time Series Models to forecast future monthly prices.

* **Q:** Can we get long term predictions without "future" data? 

* **A:** Yes! We can use Time Series models to forecast long-term stock prices! And most time series models do NOT require future data of $X_{test, future values}$! It will automatically forecast future stock prices. Time Series models mainly require the response variable of $\vec y$, the response variable values. In this case, the response variable is the closing stock prices. 

* We should also use **monthly** Tesla stock prices since we can detect seasonality and trends more effectively. Daily stock prices may have noise or be biased depending on the day. Furthermore, monthly stock prices are more parsimonous (more simple to understand). It would be easier to interpret 12 monthly data points vs 365 daily data points. 

### First Strategy
My training set contained 2016 to 2024 **monthly** stock prices. The testing set contained 2025 **monthly** stock prices. 

But after fitting many time series models, it appears that the year of 2025 was significant and needed to be included in the training set in order to forecast well.
For instance, the AIC/BIC values of SARIMA actually became lower if the 2025 monthly prices got included in the training data. (Lower AIC/BIC scores indicate better model fit.)

### Second Strategy
I then decided to make my training set based on all the 2016 to 2025 **monthly** Tesla Stock price. I then forecasted the next 3 years.

Using the Second Strategy, here are some Time Series models and their forecasts!

Lets first at just the Time Series data itself!


### 📊 Plot of Time Series Data for 2016 to 2025 Monthly Tesla Stock Prices

<img width="1267" height="879" alt="github_tesla_3" src="https://github.com/user-attachments/assets/c0d18784-aad3-4f9c-9600-5b1cde22d9c9" />


Models are not necessary to gain insights! Just looking at the data can give us insights!

**Monthly Patterns:**

* January appears to have the largest spikes in stock prices.

* Spring months tend to decrease in stock prices.

* Summer to late winter months tend to increase in stock prices.


**Business Insights:**

* Based on these trends, an investor might consider buying during early spring months when prices are lower and selling during summer or late winter months when prices tend to peak.

* WARNING: Tesla stocks are highly volatile. These patterns are not guaranteed and should not be relied on as a definitive trading strategy.  


### 📊 SARIMA:

<img width="1296" height="886" alt="github_tesla_4" src="https://github.com/user-attachments/assets/2bc2f004-eb6c-43a6-a0fb-9c83160b8c16" />


The SARIMA model's parameters are: $ARIMA(2,1,2) \times (2,0,0)_{12}$  (More details of how to intepret these parameters are in the project.)       


### 📊 Prophet:


<img width="964" height="600" alt="github_tesla_5" src="https://github.com/user-attachments/assets/e49db406-bab8-4d6f-baa2-326c810b646e" />



Prophet automatically handles trends and seasonality of this data, so we do not have to worry about any configurations!

The black dots represent the 2016 to 2025 stock prices. The shaded blue area represents the prediction intervals. 

This is the Prophet Time Series model formula:

$$\hat y_t = \hat m_t + \hat s_t + \hat h_t$$

Where:

* $\hat y_t$: The predicted/forecasted value at time $t$.

* $\hat m_t$: The predicted trend.

* $\hat s_t$: The predicted seasonal component.

* $\hat h_t$: The predicted holiday effect. (This is optional.) 

### 📊 Space-State Model:

<img width="1267" height="878" alt="github_tesla_6" src="https://github.com/user-attachments/assets/44baee59-9288-451c-833f-420be7d57b44" />


This Space-State model is set to consider a local linear trend.



### Conclusion:

Overall, it appears that these Time Series models have good estimates of what the overall trends and seasonality patterns could be in the future!


---

<a name="methodology"></a>
## 5. 📔 The Methodology of what I did: 

### Firstly, I did Exploratory Data Analysis.

I did feature engineering to create new predictor variables such as $\text{Daily Range} = High - Low$ (Where $High$ represents the highest stock price in a day, and $Low$ represents the lowest stock price in a day.) 

Plots of predictor variables against response variables were made.
Additionally, predictor variables against other predictor variables were made.

### Secondly, Regression ML models and Time Series models were created.
  
* **Stack:** Python (NumPy, pandas, matplotlib, seaborn, scikit-learn, XGBoost, Statsmodel, Prophet)

### Thirdly, I gathered insights and discoveries from ML models, Time Series models, and Time Series data. 

---

<a name="log"></a>
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
