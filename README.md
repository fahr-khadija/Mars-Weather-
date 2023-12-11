# Mars_news_Weather

# Overview
In this challenge we are  now ready to take on a full web-scraping and data analysis project. You’ve learned to identify HTML elements on a page, identify their id and class attributes, and use this knowledge to extract information via both automated browsing with Splinter and HTML parsing with Beautiful Soup. You’ve also learned to scrape various types of information. These include HTML tables and recurring elements, like multiple news articles on a webpage.

# Work Flow 
## Technical Develloppement 
    work in pandas files By  collecting data, organizing and storing data, analyzing data, and then visually communicating your insights

## Part 1: Scrape Titles and Preview Text from Mars News
           ## Code file 
part_1_mars_news.ipynb

### General Import Splinter and BeautifulSoup ChromeDriverManager
            from splinter import Browser
            from bs4 import BeautifulSoup as soup
            from webdriver_manager.chrome import ChromeDriverManager
         
### Step 1: Visit the Website
          # Visit the Mars news site
            url = 'https://static.bc-edx.com/data/web/mars_news/index.html'
            browser.visit(url)
### Step 2: Scrape the Website
            # Create a Beautiful Soup object
            html = browser.html
            soup = soup(html,"html.parser")
            # Extract all the text elements
            text_elements = soup.find_all('div', class_='list_text')
### Step 3: Store the Results
            # Create an empty list to store the dictionaries
            list = []
            # Loop through the text elements,Extract the title and preview text from the elements
            # Store each title and preview pair in a dictionary,Add it to the list,Loop through the text elements
            for text_element in text_elements:
            title = text_element.find('div', class_='content_title').text
            preview = text_element.find('div', class_='article_teaser_body').text
             title_preview_list = {
            "Title" : title,
            "Preview" : preview
             }
             list.append(title_preview_list)

## Part 1: Scrape and Analyze Mars Weather Data

### General Import relevant libraries
            from splinter import Browser
            from bs4 import BeautifulSoup as soup
            import matplotlib.pyplot as plt
            import pandas as pd
            from webdriver_manager.chrome import ChromeDriverManager
            from bs4 import BeautifulSoup as bs
            import numpy as np
### Step 1: Visit the Website
             url = "https://static.bc-edx.com/data/web/mars_facts/temperature.html"
             browser.visit(url)
### Step 2: Scrape the Table
            # Create a Beautiful Soup Object
            html = browser.html
            soup = bs(html, 'html.parser')
            # Extract all rows of data
            table = soup.find('table', class_='table')
### Step 3: Store the Data

### Step 4: Prepare Data for Analysis
            #Change data types for data analysis
             convert = {'terrestrial_date': 'datetime64[ns]',
           'sol': 'int64',
           'ls': 'int64',
           'month': 'int64',
           'min_temp': 'float64',
           'pressure': 'float64'}
            mars_weather_df = mars_weather_df.astype(convert).astype(convert)
### Step 5: Analyze the Data
            # 1. How many months are there on Mars?
            months = mars_weather_df['month'].value_counts().sort_index()

           # On average, the third month has the coldest mounth in Mars, and the eighth month is the warmest. 
            #Atmospheric pressure is, on average, lowest in the sixth month and highest in the ninth.
            ##The distance from peak to peak is roughly 1425-750, or 675 days. A year on Mars appears to be about 675 days from the plot. 

