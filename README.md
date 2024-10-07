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
- rare-disease_monthly_desktop_2015070100-2024093000
  - This is a JSON file of the monthly page traffic for the specified pages in rare-disease_cleaned.AUG.2024.csv accessed by desktop for the the date rage July 1, 2015 through September 30, 2024.
  - Data Schema:
    ```
    {
    "Disease_Name_1": [
        {
            "timestamp": "YYYYMMDDHH",
            "views": Integer
        },
        ...
    ],
    "Disease_Name_2": [
        {
            "timestamp": "YYYYMMDDHH",
            "views": Integer
        },
        ...
    ]
    }
    ```
    

