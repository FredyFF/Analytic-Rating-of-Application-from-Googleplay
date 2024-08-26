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

### Import Library Scraper

```html
<script>
# Import Library of google play Scarper

from google_play_scraper import Sort, reviews
from google_play_scraper import app
import pandas as pd
import numpy as np
import datetime

# using now() to get current time when Scraping is begin
current_time = datetime.datetime.now()

</script>
```

### Get Token
```html
<script>
# Get Token from com.instagram.android

result, continuation_token = reviews(
    'com.instagram.android',  #INSTAGRAM
    lang='id', #bahasa (Indonesia), language where review is issued
    country='id', # Country where reviewer come from
    sort=Sort.MOST_RELEVANT, #sorting the most relevant
    count=2000, #count of dataset requested
    filter_score_with= None  #filling with 1, 2, 3, 4, 5 None if tobe mixed
)

</script>
```

### Get Dataset form Review List
```html
<script>
# Dataframe With Name

data = pd.DataFrame(np.array(result),columns=['review'])
data = data.join(pd.DataFrame(data.pop('review').tolist()))
data.head()

</script>
```
_
![alt text](https://fredyfirmansyah107.wordpress.com/wp-content/uploads/2024/08/screen-shot-2024-08-26-at-08.59.48.png?w=1024)


In this process use 2000 rows, show lets check data with Len
```html
<script>
#check length of dataset

len(data)

</script>
```
Because we only need 2 columns in this analysis, we can split it by displaying only the relevant columns


```html
<script>
# use relevant column 

data = data[['content','score']]
data.head()

</script>
```

In data analysis we can download the data set that we have scaping, making it easier to do ETL

```html
<script>
# export to csv 

data.to_csv("Data Review.csv", index = False  , encoding='utf-8')

</script>
```
Modify Rating to score analyst, at this stage we can modify the rating which was previously an integer from the range 1 to 5, we change it to a perception measuring rating such as: 
- 5 - Very Good
- 4 - Likes
- 3 - Neutral
- 2 - Not Good
- 1 - Bad

```html
<script>
import pandas as pd

dataInstagram = pd.read_csv('/Users/fredyfirmansyah/Desktop/TRAINING DS/Data Review.csv')


for i in range(len(dataInstagram ['score'])):
    if dataInstagram ['score'][i] == 5:
        dataInstagram['score'][i] = 'Very Good'
    if dataInstagram ['score'][i] == 4:
        dataInstagram['score'][i] = 'Like'
    if dataInstagram['score'][i] == 3:
        dataInstagram['score'][i] = 'Neutral'
    if dataInstagram['score'][i] == 2:
        dataInstagram['score'][i] = 'Not Good'
    if dataInstagram['score'][i] == 1:
        dataInstagram['score'][i] = 'Bad'

dataInstagram.to_csv("Result Data Review.csv", index = False  , encoding='utf-8')
</script>
```
# Vsualization











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

