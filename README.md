# Retail Giant Sales & Quantity Forecasting Assignment
#### Problem Statement I - Data Preparation
Global Mart is an online supergiant store that has worldwide operations. This store takes orders and delivers across the globe and deals with all the major product categories — consumer, corporate & home office.
As a sales manager for this store, you have to forecast the sales and quantity of the products for the next 6 months, so that you have an estimate of the demand and the sales of the products in those months and can plan your inventory and business processes accordingly.

**The store dataset has the following 6 attributes and their data description is as given below:**
 

Attributes	Description
------------------------------------
Order Date	- The date on which the order was placed
Segment	    - The  segment to which the product belongs
Market	    - The market to which the customer belongs
Sales	      - Total sales value of the transaction
Quantity    -	Quantity of the product ordered
Profit	    - Profit made on the transaction

If you check the entries in the dataset, you will see that the store caters to 7 different geographical market segments and 3 major customer segments i.e. consumer, corporate and home as can be seen in the table below.

Market	            Segment
---------------------------------------
Africa	            Consumer
APAC (Asia Pacific)	Corporate
Canada	            Home Office
EMEA(Middle East)	 
EU (European Union)	 
LATAM (Latin America)	 
US (United States)	 
 

Based on these, there are 21 unique "Market-Segments" for which the sales and the quantity forecasts can be made. Now, due to certain unpredictable circumstances in the market, as a company, you are prioritizing only the best and most consistent market segment in terms of profitability. You want to see which market segment is the most consistently profitable and accordingly, you would want to check how the sales and quantity forecasts look for the next 6 months. As of now, you do not want to focus on other market segments that might that have not been very consistent and profitable to your company.

--> So, not all of these 21 market segments are important from the store’s point of view. You need to find out the most profitable (and consistent) segment from the above and forecast the sales and demand for that market segment and not for all.

**How to find the most profitable market segment?**
Now, it's clear that you only need to work on one market-segment which is the most consistently profitable. But how do you find the most consistently profitable market-segment? For this, you will be using a measure called "Coefficient of Variation (CoV)". Coefficient of variation or CoV is simply a ratio of the standard deviation to mean.

**But why consider the coefficient of variation here and not the standard deviation? and how will the coefficient of variation lead you to the most profitable market segment?** 
The coefficient of variation is a ratio of the standard deviation to mean. When you carefully observe the dataset, you can see that among the 21 market segments, the mean of the profits for these market segments varies quite a bit. Also, the standard deviation for the profits varies in a similar manner and it is meaningless to compare standard deviations across the 21 market segments. As a better metric to compare the variance between the segments you use the coefficient of variation. It normalises the standard deviation and gives us a comparative figure on the basis of which we can identify the most profitable market segment.

 

You should find out whether the most profitable market segment should have the least values of CoV or the highest values of CoV among the list of the 21. And reason out why that segment should be the most profitable.

You can read more about coefficient of variation here.
### Data Understanding and Preparation
You have seen that the data had 6 attributes. These are Order-Date, Market, Segment, Sales, Quantity and Profit for each transaction. The complete data dictionary has been given below again for your reference. The “Market” attribute has 7-factor levels representing the geographical market sector that the customer belongs to. The “Segment” attribute tells which of the 3 segments that customer belongs to. 

 

Attributes	            Description
--------------------------------------------------------
Order Date	          The date on which the order was placed
Segment	              The segment to which the product belongs
Market	              The market to which the customer belongs
Sales                	Total sales value of the transaction
Quantity	            Quantity of the product ordered
Profit	              Profit made on the transaction
 

**For doing the data preparation —**

--> Find the 21 unique Market Segments
-->Calculate the CoV for each market segment
-->Find the most profitable market segment

Once you have understood the dataset of the global data store, you need to get the order date in the required month-year format to make it a monthly aggregated transaction data. Then, you need to concatenate the market and segment columns such that you get the time series data consisting of order, sales, quantity, profit, market segments. Split the dataset into train and test split (take the test data as 6 months).

For each of the 21 unique market segments calculate the coefficient of variation on the profit for each market segment. Conclude the most profitable market segment. Reason out why that segment should be the most profitable based on what you observe from the CoV values. Mention this as a comment in the Jupyter notebook file or in the presentation asked in the submissions. (Read the detailed note on submissions in the next segments). It is expected that you do some research on understanding CoV and how to find it out for all the given market segments in Python.

### Problem Statement II - Model Building & Evaluation
Once you arrive at the most profitable market segment, the next challenge is to forecast the sales and quantity for the next 6 months (test data) for that market segment. Before you start applying each of the techniques, plot the variation of sales for the concerned market segment and deduce conclusions on the trend and the seasonality of the data. Go back to the flow chart taught in the conceptual lectures and conclude which method as per the flow chart should suit best from the smoothing technique and similarly which method will work best for predicting the sales using the ARIMA set of techniques. Similarly, find which technique will suit best for forecasting the quantity from the flow chart overall and then forecast the quantity for the next 6 months.

### Model Building and Evaluation
Now, even though you have seen which model might work best based on the trend, as a part of this assignment, you are required to build all the models. First, start by applying the smoothing techniques —

--> Simple exponential smoothing
--> Holt’s exponential smoothing
--> Holt-Winters’ exponential smoothing (try both additive and multiplicative techniques here)
Check the forecast plot calculated on the test data and also the MAPE values for each of the above methods. (keep adding the MAPE values in a single table to compare them)
Conclude the method whose forecast is able to predict the sales closer to the actual values and whose MAPE values is the least among all the methods done above. Check if this matches with what you found from the flow chart.
 
Next, you are to apply the ARIMA set of techniques, (use p=1, q=1 and d=1 as the forecasts are relatively better for these values) 

--> AR model
--> MA model
--> ARMA model
--> ARIMA model
--> ARIMAX model (apply this technique if you think there is an exogenous variable in the data)
--> SARIMA model

SARIMAX model (apply this technique if you think there is an exogenous variable in the data)
Check the forecast plot calculated on the test data and also the MAPE values for each of the above methods. (keep adding the MAPE values in a single table to compare them)
Conclude the method whose forecast is able to predict the sales closer to the actual values and whose MAPE values is the least among all the methods done above. Check if this matches with what you found from the flow chart.
After applying each of the above techniques and forecasting the sales for the next 6 months, follow EVERY step explained in the model building and evaluation part for repeating the steps for quantity forecasts on the same market segment that you forecasted the sales for.
