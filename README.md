# CHALLENGE_11
## Background

In this scenario, you’re a growth analyst at [Mercado Libre](http://investor.mercadolibre.com/investor-relations). With over 200 million users, Mercado Libre is the most popular e-commerce site in Latin America. You've been tasked with analyzing the company's financial and user data in clever ways to help the company grow. 

In a bid to drive revenue, you’ll produce a Jupyter notebook that contains your data preparation, your analysis, and your visualizations for all the time series data that the company needs to understand. You’ll use text and comments to document your findings. And, you’ll answer the question prompts in the instructions. Specifically, this notebook should contain the following:

- Visual depictions of seasonality (as measured by Google Search traffic) that are of interest to the company.

- An evaluation of how the company stock price correlates to its Google Search traffic.

- A Prophet forecast model that can predict hourly user search traffic.

- Answers to the questions in the instructions that you write in your Jupyter notebook.

- (Optional) A plot of a forecast for the company’s future revenue.

When you finish, you’ll push your final notebook to your GitHub repository so that others can review your work.

You’ll gain proficiency in the following tasks:

- Identifying patterns in time series data.

- Mining for patterns in seasonality by using visualizations.

- Building sales-forecast and user-interest predictive models.

---

## Instructions

First, configure a Google Colaboratory, or Colab, workspace as follows:

1. Open [Google Colab](https://colab.research.google.com/), and then upload your starter notebook.

2. Run the provided code in the “Install and import the required libraries and dependencies” section. Note the following:

   - The first cell installs the necessary libraries into the Google Colab runtime.

   - The second cell imports the dependencies for use in the notebook.

With your workspace configured, you can begin the assignment. The instructions are divided into four steps and an optional fifth step as follows:

- Step 1: Find unusual patterns in hourly Google search traffic.

- Step 2: Mine the search traffic data for seasonality.

- Step 3: Relate the search traffic to stock price patterns.

- Step 4: Create a time series model by using Prophet.

- Step 5 (optional): Forecast the revenue by using time series models.

The following subsections detail these steps.

### Step 1: Find Unusual Patterns in Hourly Google Search Traffic

The data science manager at Mercado Libre asks you if the Google search traffic for the company links to any financial events at the company. Or, does the search traffic data just present random noise? To answer this question, you’ll pick out any unusual patterns in the Google search data for the company, and connect them to the corporate financial events.

Answering the question requires you to complete the following steps:

1. Read the search data into a DataFrame, and then slice the data to just the month of May 2020. (During this month, Mercado Libre released its quarterly financial results.) Use hvPlot to visualize the results. Do any unusual patterns exist?

2. Calculate the total search traffic for the month, and then compare the value to the monthly median across all months. Did the Google search traffic increase during the month that Mercado Libre released its financial results?

<img width="1032" alt="Screenshot 2024-03-07 at 9 18 46 PM" src="https://github.com/kimrodriguezFINTECH/CHALLENGE_11/assets/152752672/26429509-ef93-4589-be93-3b71fa00f888">


**Question:** Did the Google search traffic increase during the month that MercadoLibre released its financial results?

**Answer:** The monthly search traffic was roughly 35,172 while the search traffic in May 2020 was 38,181. This showed an increase in search traffic that could be caused by the release of financial results.



### Step 2: Mine the Search Traffic Data for Seasonality

The Marketing department realizes that they can use the hourly search data, too. If they can track and predict interest in the company and its platform for any time of day, they can focus their marketing efforts around the times that have the most traffic. This will get a greater return on investment (ROI) from their marketing budget.

To help Marketing, you'll want to mine the search traffic data for predictable seasonal patterns of interest in the company. Complete the following steps:

1. Group the hourly search data to plot the average traffic by the day of the week (for example, Monday vs. Friday).

2. Using hvPlot, visualize this traffic as a heatmap, referencing `index.hour` for the x-axis and `index.dayofweek` for the y-axis. Does any day-of-week effect that you observe concentrate in just a few hours of that day?

3. Group the search data by the week of the year. Does the search traffic tend to increase during the winter holiday period (weeks 40 through 52)?

<img width="1008" alt="Screenshot 2024-03-07 at 9 19 10 PM" src="https://github.com/kimrodriguezFINTECH/CHALLENGE_11/assets/152752672/d1c160a5-375a-4e04-930d-2c31ddad890c">

<img width="720" alt="Screenshot 2024-03-07 at 9 19 18 PM" src="https://github.com/kimrodriguezFINTECH/CHALLENGE_11/assets/152752672/3626e579-c3a4-4bac-8c09-d5620e529b49">

Question: Does any day-of-week effect that you observe concentrate in just a few hours of that day?

Answer: Looking at the heatmap we can see that during the initial hours of the day and the last few hours of the day have an increase in search traffic. One possibility of why this is, that people look at their phones first thing in the morning and before they fall asleep. Another possibility is between the hours 6 & 10 there is a decrease because people are at work or school and cannot view their phones. It also seems like the search traffic starts off very high during the beginning of the week and slows down during the weekend.

<img width="1006" alt="Screenshot 2024-03-07 at 9 29 58 PM" src="https://github.com/kimrodriguezFINTECH/CHALLENGE_11/assets/152752672/bf42fe8a-9097-432d-ab0f-5b9bfcb9ce29">


### Step 3: Relate the Search Traffic to Stock Price Patterns

During a meeting with people in the Finance group, you mention your work on the search traffic data. They want to know if any relationship between the search data and the company stock price exists, and they ask if you can investigate.

You can find out the answer by completing the following steps:

1. Read in and plot the stock price data. Concatenate the stock price data to the search data in a single DataFrame.

2. Note that market events emerged during 2020 that many companies found difficult. But after the initial shock to global financial markets, new customers and revenue increased for e-commerce platforms. So, slice the data to just the first half of 2020 (`2020-01` to `2020-06` in the DataFrame), and then use hvPlot to plot the data. Do both time series indicate a common trend that’s consistent with this narrative?

3. Create a new column in the DataFrame named “Lagged Search Trends” that offsets, or shifts, the search traffic by one hour. Create two additional columns:

   - “Stock Volatility”, which holds an exponentially weighted four-hour rolling average of the company’s stock volatility

   - “Hourly Stock Return”, which holds the percentage of change in the company stock price on an hourly basis

4. Review the time series correlation, and then answer the following question: Does a predictable relationship exist between the lagged search traffic and the stock volatility or between the lagged search traffic and the stock price returns?

<img width="1000" alt="Screenshot 2024-03-07 at 9 48 47 PM" src="https://github.com/kimrodriguezFINTECH/CHALLENGE_11/assets/152752672/b1c9fd34-b82d-417f-8d22-3153e1b88c69">


<img width="1029" alt="Screenshot 2024-03-07 at 9 42 05 PM" src="https://github.com/kimrodriguezFINTECH/CHALLENGE_11/assets/152752672/d8a3d3b5-0a01-4eea-8145-18e34b62ca4c">

<img width="1022" alt="Screenshot 2024-03-07 at 9 42 34 PM" src="https://github.com/kimrodriguezFINTECH/CHALLENGE_11/assets/152752672/1188faeb-3c2b-45da-bf98-469781d0df29">

**Question:** Do both time series indicate a common trend that’s consistent with this narrative?

**Answer:** Looking at the plots above, during the months of February 2020 and March 2020, there is a clear downtrend in stock price and search traffic. As the stock price increased during May so did a huge spike occur in search traffic. Thus, as the stock price increases, the search traffic becomes highly volatile during those moments.

<img width="991" alt="Screenshot 2024-03-07 at 9 51 06 PM" src="https://github.com/kimrodriguezFINTECH/CHALLENGE_11/assets/152752672/e49f9f54-5a58-4d3e-8367-d69bf691c8fa">

**Question:** Does a predictable relationship exist between the lagged search traffic and the stock volatility or between the lagged search traffic and the stock price returns?

**Answer:** Based off of the correlation table above, we can see that there is a weak positive correlation among Stock Volatility & Hourly Stock Return and a weak negative correlation among Lagged Search Trends & Stock Volatility. Also note worth there is a weak positive correlation among Hourly Stock Return & Stock Volatility & Lagged Search Trends.

### Step 4: Create a Time Series Model by Using Prophet

Now, you need to produce a time series model that analyzes and forecasts patterns in the hourly search data. Complete the following steps to create the model:

1. Set up the Google search data for a Prophet forecasting model.

2. After estimating the model, plot the forecast. What is the near-term forecast for the popularity of Mercado Libre?

3. Plot the individual time series components of the model to answer the following questions:

   - What time of day exhibits the greatest popularity?

   - Which day of the week gets the most search traffic?

   - What's the lowest point for search traffic in the calendar year?

<img width="983" alt="Screenshot 2024-03-07 at 9 54 48 PM" src="https://github.com/kimrodriguezFINTECH/CHALLENGE_11/assets/152752672/aca750ac-6510-45ca-a423-2eed0bdf7d3e">

<img width="979" alt="Screenshot 2024-03-07 at 9 54 52 PM" src="https://github.com/kimrodriguezFINTECH/CHALLENGE_11/assets/152752672/8d003f89-7b4b-4f04-8a50-a1e512731f4a">

**Question:**  How's the near-term forecast for the popularity of MercadoLibre?

**Answer:** The forecast shows that the popularity gradually decreases towards the end of 2020.

<img width="963" alt="Screenshot 2024-03-07 at 9 56 21 PM" src="https://github.com/kimrodriguezFINTECH/CHALLENGE_11/assets/152752672/e6b90ede-02ad-4d21-be60-5396f7045149">

<img width="896" alt="Screenshot 2024-03-07 at 9 56 28 PM" src="https://github.com/kimrodriguezFINTECH/CHALLENGE_11/assets/152752672/372f99e3-9a07-415e-a3e4-f282fd607298">

<img width="878" alt="Screenshot 2024-03-07 at 9 56 30 PM" src="https://github.com/kimrodriguezFINTECH/CHALLENGE_11/assets/152752672/e3dbfbcd-79e9-468f-89e2-90084427fd47">

<img width="894" alt="Screenshot 2024-03-07 at 9 56 35 PM" src="https://github.com/kimrodriguezFINTECH/CHALLENGE_11/assets/152752672/9ba098cc-41e8-4253-81f8-061831aea8a2">

<img width="892" alt="Screenshot 2024-03-07 at 9 56 37 PM" src="https://github.com/kimrodriguezFINTECH/CHALLENGE_11/assets/152752672/50dad966-adda-4736-8772-58184a271d8f">

**Question:** What time of day exhibits the greatest popularity?

**Answer:** Towards the end of the day 00:00:00 (24 hour mark).

**Question:** Which day of week gets the most search traffic?
   
**Answer:** Monday's & Tuesday's have the most search traffic.

**Question:** What's the lowest point for search traffic in the calendar year?

**Answer:** The lowest point of search traffic was during the end of September.
