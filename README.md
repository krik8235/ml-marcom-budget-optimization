# Budget Optimization for Online Retailers

## 1. Introduction 

The business problem can be expressed in the following manner: given a total budget B, calculate the optimum monthly budget allocation {B1, ..., B12} across multiple channels (and potentially campaigns {C1, ..., Cn}) in order to maximize revenue R.

Here's a basic marketing budget allocation that assumes Year to Date (YTD) average Cost-per-Click (CPC), Conversion Rate (CVR) and Average Order Value (AOV) for each channel.

While the task is to optimize the budget allocation between multiple channels & campaigns, some of them are "inner" optimizable (Google Ads, Facebook Ads), others are out of reach: E-mail, SEO, etc. There are multiple "problems" at once that are embedded in this "budget allocation" term and we’ll try to provide a direction to solving the problem using the campaigns as black-boxes, making use only of the cost and the revenue produced.

## 2. Budget Allocation Overview

The task is to allocate budgets to campaigns in order to maximize revenue. The main challenge is that the relationship between budget and revenue is nonlinear, and the projected revenues are likely inaccurate. The solution involves two steps: 1) building a model for each campaign that predicts revenue based on budget, and 2) allocating budgets optimally based on these models.

### 2.1 Time Series Model
We predicted the revenue of a campaign based on its allocated budget and historical data. The model can be built for daily or monthly intervals. The goal is to define the relationship between budget and historical data to predict revenue.

The approach involves using either monthly aggregated data or daily data to model the time series. Monthly aggregated data is the simplest but serves as a baseline, while daily data is expected to improve the model's performance.

The specific modeling technique (RNN, HMM, or linear model) is not specified, but the focus is on creating a revenue prediction function for each campaign.

RevC (ti) = P(B|RevC (t0), . . . RevC (ti−1))

* Monthly aggregated data. This is the easiest case - set as the baseline solution
* Daily data. Use the daily data to model the time series, which should show some improvements
over the baseline solution. 

### 2.2 Optimal Optimization Problem
There are some challenges in a solution to the problem of picking the optimal budget allocation for multiple campaigns. 

We first build a model for each campaign and then use non-convex continuous optimization algorithms like genetic algorithms and colony optimization to find the global optimum, observing that even with dummy data, the global optimum varies greatly when the models are non-linear.