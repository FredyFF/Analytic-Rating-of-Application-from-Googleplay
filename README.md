# Title : Analytic-Rating-of-Application-from-Googleplay



## Table of Contents

- [Project Overview](#project-overview)
- [Data Sources](#data-sources)
- [Recommendations](#recommendations)

### Project Overview
This data analysis project aims to provide insight into scraping rating data for an application in Playstore. Even though the data drawn is small, this technique simply describes how web scraping works, then an analysis is carried out in the form of the score level obtained so that it can be briefly visualized. with eye gaze analysis of rating data from the last 2000 reviewers.



Data Sources
In searches related to ratings using the Google Play site where the application being reviewed is downloaded [Instagram] 

Tools
Excel - Data Cleaning
Download here
SQL Server - Data Analysis
PowerBI - Creating reports
Data Cleaning/Preparation
In the initial data preparation phase, we performed the following tasks:

Data loading and inspection.
Handling missing values.
Data cleaning and formatting.
Exploratory Data Analysis
EDA involved exploring the sales data to answer key questions, such as:

What is the overall sales trend?
Which products are top sellers?
What are the peak sales periods?
Data Analysis
Include some interesting code/features worked with

SELECT * FROM table1
WHERE cond = 2;
Results/Findings
The analysis results are summarized as follows:

The company's sales have been steadily increasing over the past year, with a noticeable peak during the holiday season.
Product Category A is the best-performing category in terms of sales and revenue.
Customer segments with high lifetime value (LTV) should be targeted for marketing efforts.
Recommendations
Based on the analysis, we recommend the following actions:

Invest in marketing and promotions during peak sales seasons to maximize revenue.
Focus on expanding and promoting products in Category A.
Implement a customer segmentation strategy to target high-LTV customers effectively.

Results/Findings
The analysis results are summarized as follows:

The company's sales have been steadily increasing over the past year, with a noticeable peak during the holiday season.
Product Category A is the best-performing category in terms of sales and revenue.
Customer segments with high lifetime value (LTV) should be targeted for marketing efforts.

Limitations
I had to remove all zero values from budget and revenue columns because they would have affected the accuracy of my conclusions from the analysis. There are still a few outliers even after the omissions but even then we can still see that there is a positive correlation between both budget and number of votes with revenue.

References
SQL for Businesses by werty.
Stack Overflow
https://github.com/Irene-arch/Documenting_Example/blob/main/README.md
https://python-graph-gallery.com/90-heatmaps-with-various-input-format/

