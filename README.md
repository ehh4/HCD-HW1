# HCD-HW1

### Project goal
The goal of this project is to create and analyze a dataset of monthly article traffic for specified pages from English Wikipedia in the date rage July 1, 2015 through September 30, 2024. The specified pages are related to rare diseases, either about a rare disease or have a section that mentions a rare disease. The list of these pages are given by the rare-disease_cleaned.AUG.2024.csv file. The project collects pageview data using the Wikimedia Analytics Pageviews API, which is documentated [here](https://doc.wikimedia.org/generated-data-platform/aqs/analytics-api/reference/page-views.html). Using the data returned by the API, three JSON files are created with the pageview data for the date range July 1, 2015 through September 30, 2024, one for views from desktop access, one for views from mobile access, and one for cumulative views, all mobile and all desktop. After the files are created, basic visual analysis is conducted to produce three graphs that are saved as .png. There is one graph showing the maximum average and minimum average views for each mobile and desktop, a graph showing the top 10 peak page views for each mobile and desktop access, and the 10 articles with the fewest months of data for each mobile and desktop data. 


### Licensing 
The Wikimedia Analytics Pageviews API source code is licensed by [Wikimedia Analytics Pageviews API] (https://foundation.wikimedia.org/wiki/Policy:Terms_of_Use).
The starter code is adpated from Dr. McDonald's example notebook, wp_article_views_example.ipynb which is licensed [CC-BY](https://creativecommons.org/licenses/by/4.0/). The following changes were made: 
- Added my own UW Net ID
- Added additional packages and changed the comments to reflect multiple imports 
- Removed the access type in the ARTICLE_PAGEVIEWS_PARAMS_TEMPLATE variable 
- Modified the request_pageviews_per_article funtion to take access_type argument and changed function logic to take input into API request template, similarly to how the article argument is handled

The code specified as created by Chat GPT is licensed by [Open AI Terms of Use](https://openai.com/policies/row-terms-of-use/).
All other code not designated as starter code from Dr. McDonald or copied from Chat GPT is created by Elizabeth Holden and licensed [CC-BY](https://creativecommons.org/licenses/by/4.0/).

### Files
The notebook that contains all project code, HCD-HW1.ipynb, creates the following files:
JSON Files:
- rare-disease_monthly_desktop_2015070100-2024093000
  - This is a JSON file of the monthly page traffic for the specified pages in rare-disease_cleaned.AUG.2024.csv accessed by desktop for the the date rage July 1, 2015 through September 30, 2024.
- rare-disease_monthly_mobile_2015070100-2024093000
  - This is a JSON file of the monthly page traffic for the specified pages in rare-disease_cleaned.AUG.2024.csv accessed by mobile-app or mobile-web for the the date rage July 1, 2015 through September 30, 2024.
- rare-disease_monthly_cumulative_2015070100-2024093000
  - This is a JSON file of the monthly page traffic for the specified pages in rare-disease_cleaned.AUG.2024.csv accessed by desktop, mobile-app, or mobile-web for the the date rage July 1, 2015 through September 30, 2024
  
  Data Schema for JSON files:
  The JSON files contain a dictionary where the keys are the disease name (str type) from the csv file and the value for each key is a list of dictionaries of the returned value of the API request for each timestamp that   page view data is available for. The 'access' field of the returned value of the API request is not included in the JSON. The dictionaries for the returned value of the API request contain the keys which are all type str and the values are all str except the 'views' value is an int. 
    ```
    {
    'Disease Name 1': [
        {  'project': 'en.wikipedia', 
           'article': 'article title',
           'granularity': 'monthly',
           'timestamp': 'YYYYMMDDHH',
           'agent': 'user',
           'views': int
        },
        ...
    ],
    'Disease Name 2': [
        {  'project': 'en.wikipedia', 
           'article': 'article title',
           'granularity': 'monthly',
           'timestamp': 'YYYYMMDDHH',
           'agent': 'user',
           'views': int
        },
        ...
    ]
    }
    ```
PNG Files:
- max_min_avg_views.png: This is a graph containing time series for the articles that have the highest average page requests and the lowest average page requests for desktop access and mobile access over July, 2015 through September, 2024.
- top10_peak_views.png: This is a graph showing the the top 10 article pages by largest number page views at one timestamp (a peak in views) over the entire time series for both mobile and desktop platforms over over July, 2015 through September, 2024. 
- 10_least_months.png: This is a graph showing the 10 articles with the least months of available data for both mobile and desktop platforms over July, 2015 through September, 2024..
    
Considerations:
- The notebook currently throws an exception for the following three articles from the csv due to the url not handling the '/':
  - Sulfadoxine/pyrimethamine
  - Cystine/glutamate transporter
  - Trimethoprim/sulfamethoxazole
 
- The notebook analysis for finding the top 10 peak views and top 10 least months available does not handle the situation where muliple articles have the same values, it takes whichever of the tied articles is first in the dataframe. 
