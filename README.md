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