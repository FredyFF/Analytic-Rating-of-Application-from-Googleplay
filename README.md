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

Data can be imagined in visualizations which can be realized with useful tools, such as existing data visualizations. We can see the complexity of the data by creating a bar plot so we can see the bars of the data set.

```html
<script>
# Create Barplot Visualization

from matplotlib import pyplot as plt

verg = (dataInstagram['score'] == 'Very Good').sum()
like = (dataInstagram['score'] == 'Like').sum()
Neu = (dataInstagram['score'] == 'Neutral').sum()
notg = (dataInstagram['score'] == 'Not Good').sum()
bad = (dataInstagram['score'] == 'Bad').sum()


sen = ['Very Good', 'Like', 'Neutral', 'Not Good', 'Bad']

data = [verg, like, Neu,notg,bad]

plt.bar(sen, data, color ='blue', 
        width = 0.4)

plt.xlabel("Sentimen Result")
plt.ylabel("No. of Rating Sentimen")
plt.title("Sentimen analysis Application of Instagram")
plt.show()
</script>
```

![alt text](https://fredyfirmansyah107.wordpress.com/wp-content/uploads/2024/08/screen-shot-2024-08-26-at-16.28.30.png?w=610)

_

From the bar diagram above, it shows that the differences in height have a fairly descriptive appearance, what if we use another diagram, for example a pie chart. let's look at the visualization form

_

![alt text](https://fredyfirmansyah107.wordpress.com/wp-content/uploads/2024/08/screen-shot-2024-08-26-at-16.36.47.png?w=610)


### Results/Findings
The analysis results are summarized as follows:

- Rating :  2.5775
- Count Data :  2000
- Scraping Time execution :  2024-08-23 17:05:49

This is an easy way to see a summary of the data that has been obtained, with this script it will show the conclusions that have been made. 

```html
<script>
# Conclusion

import pandas as pd

dataInstagram = pd.read_csv('/Users/fredyfirmansyahit/Desktop/TRAINING DS/Data Review.csv')
avg = (dataInstagram['score']).mean()

print('Rating : ', avg)
print('Count Data : ', len(dataInstagram['score']))
print('Scraping Time execution : ', current_time )

</script>
```
_

From this data analysist we can gain insight into where at a certain time the 2000 data taken actually only had a rating of less than 3, but if the time span and data used were more diverse then there would be differences in the processing of this data. Regarding the existing ratings, so far we know that the ratings will continuously change.

### Limitations
In general, this analyst can be used as an example in data scraping, the data used is only around 2000, which is quite small. Next, the analysis generally describes how the data is interpreted.


References


