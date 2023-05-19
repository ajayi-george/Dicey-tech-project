# Dicey-tech-project
## About this project

This project involves web scraping property listings from multiple websites for the Greater London area. The goal is to create a master dataset that combines property information from multiple sources and provides valuable insights into the London real estate market.

The code utilizes the following libraries:

1. undetected_chromedriver: This library is used to create a new instance of the Chrome browser and perform web scraping. It helps in bypassing detection mechanisms that websites may have in place to prevent scraping.

2. time: This library provides functions to introduce pauses or delays in the code execution. It is used to add a delay between successive requests to avoid overwhelming the website.

3. BeautifulSoup: This library is used for parsing HTML content and extracting data from it. It provides convenient methods and syntax for navigating and manipulating the HTML structure.

4. pandas: This library is widely used for data manipulation and analysis. It provides a DataFrame data structure that allows for easy handling of structured data. The code uses pandas to convert the scraped data into a DataFrame and perform various data transformations.

5. re: This library provides regular expression matching operations. It is used in the code to extract specific patterns or information from text strings. In this case, it is used to extract the property type from the title.

6. random: This library is used to introduce randomness in the code. It is used to generate random pause durations between successive requests to avoid predictable scraping patterns.

These libraries collectively provide the necessary functionality for web scraping, data extraction, data manipulation, and data processing in the given code.
