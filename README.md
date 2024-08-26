# Title : Analytic-Rating-of-Application-from-Googleplay



## Table of Contents

- [Project Overview](#project-overview)
- [Data Sources](#data-sources)
- [Recommendations](#recommendations)

### Project Overview
This data analysis project aims to provide insight into scraping rating data for an application in Playstore. Even though the data drawn is small, this technique simply describes how web scraping works, then an analysis is carried out in the form of the score level obtained so that it can be briefly visualized. with eye gaze analysis of rating data from the last 2000 reviewers.



### Data Sources
In searches related to ratings using the Google Play site where the application being reviewed is downloaded [Instagram] 

### Tools
- Excel - Data Cleaning
- Google Sheet - Data Cleaning
- Jupyter note book


### Process Scraping to Get Dataset
in this process will use Google "Google-Play-Scraper" provides APIs to easily crawl the Google Play Store for Python without any external dependencies! [https://pypi.org/]
pip install google-play-scraper.


![alt text](https://fredyfirmansyah107.wordpress.com/wp-content/uploads/2024/08/screen-shot-2024-08-26-at-08.49.12.png?w=724)

















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

