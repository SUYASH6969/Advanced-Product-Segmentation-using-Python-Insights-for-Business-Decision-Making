A statistical methodology to segment your products based on turnover and demand variability





As a Logistics Manager, you rarely care about the product itself when managing goods flows; except for the dangerous and oversized products.

Your attention is mainly focused on the sales volumes distribution (fast/slow movers), demand variability and delivery lead time.

You want to put efforts into managing products that have:

The highest contribution to your total turnover: ABC Analysis
The most unstable demand: Demand Variability
In this project, I will introduce simple statistical tools to combine ABC Analysis and Demand Variability to perform products segmentation.


SUMMARY
I. Scenario
1. Problem Statement
2. Scope Analysis
3. Objective
II. Segmentation
ABC Analysis
Demand Stability: Coefficient of Variation
Normality Test
III. Conclusion

I. Scenario

1. Problem Statement
You are the Operational Director of a local Distribution Center (DC) that delivers 10 Hypermarkets.

In your scope you have the responsibility of

Preparation and delivery of replenishment orders from stores
Demand Planning and Inventory Management


2. Scope Analysis
This analysis will be based on the M5 Forecasting dataset of Walmart stores' sales records .

We suppose that we only have the first-year data (d_1 to d_365):

10 stores in 3 states (USA)
1,878 unique SKU
3 categories and 7 departments (sub-category)
Except for the warehouse layout, categories and departments have no impact on your ordering, picking or shipping processes.


3. Objective
What does impact your logistic performance?
Products Rotation
What are the references that are driving most of your sales?

Very Fast Movers: top 5% (Class A)
The following 15% of fast movers (Class B)
The remaining 80% of very slow movers (Class C)
This classification will impact,

Warehouse Layout
Reduce Warehouse Space with the Pareto Principle using Python

How the 80/20 rule implemented using python can optimize your layout, reduce space utilization and improve the picking productivity


Picking Process
Improve Warehouse Productivity using Order Batching with Python

Design a simulation model to estimate the impact of several Single Picker Routing Problem strategies in your Picking Productivity



Demand Variability
How stable is your customers’ demand?

Average Sales: µ
Standard Deviation:
Coefficient of Variation: CV = σ/µ
For SKUs with a high value of CV, you may face unstable customer demand that would lead to workload peaks, forecasting complexity and stock-outs.


II. Product Segmentation
This analysis will be done for the SKU in the HOBBIES category.

1. ABC Analysis
What are the references that are driving most of your sales?

Pareto Analysis for Retail
ABC Analysis of HOBBIES SKU — (Image by Author)
Class A: the top 5%- Number of SKU: 16- Turnover (%): 25%Class B: the following 15%- Number of SKU: 48- Turnover (%): 31%Class C: the 80% slow movers- Number of SKU: 253- Turnover (%): 43%
In this example, we cannot clearly observe the Pareto Law (20% of SKU making 80% of the turnover).

However, we still have 80% of our portfolio making less than 50% of the sales.


2. Demand Stability: Coefficient of Variation
How stable is your customers’ demand?

From the Logistics Manager's point of view, it is way more challenging to handle a peak of sales than a uniform distribution throughout the year.

In order to understand which products will bring planning and distribution challenges, I will compute the coefficient of variation of the yearly distribution of sales of each reference.

ABC Analysis for Retail using Coefficient of Variation (CV)
CV = f(%TO) for HOBBIES SKU
Class AFortunately, most of the A SKUs have a quite stable demand;We won't be challenged by the most important SKUs.

Class A reference with low CV 
Class BThe majority of SKUs are in the stable area;However, we still spend effort on ensuring optimal planning for the few references that have a high CV.

Class B reference with high CV 
Class CMost of the SKUs have a high value of CV;For this kind of reference, a cause analysis would provide better results than a statistical approach for forecasting.

Class C reference with very high CV 

3. Normality Test
Can we assume that the sales follow a normal distribution?

Most of the simple inventory management methods are based on the assumption that the demand follows a normal distribution.

Why?
Because it’s easy.

Sanity Check
Before starting to implement rules and perform forecasts it’s better to verify that this hypothesis cannot be refuted.

I’ll be using the Shapiro-Wilk test for normality; it can be implemented using the Scipy library. The null hypothesis will be (H0: the demand sales follow a normal distribution).



Bad News
For an alpha = 0.05, I can reject the null hypothesis for most of the SKUs. This will impact the complexity of inventory management assumptions.


III. Conclusion
This operationally driven segmentation gives us a few insights into the challenges your operations will face for planning and managing the goods flows to meet your store's demand.
