# Creating a Master Property List for London

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

## Property Scraper Documentation

This code scrapes property data from three popular real estate websites,On the market(OTM) Rightmove and Zoopla. It extracts property details such as prices, titles, addresses, descriptions, agents, and other relevant information. The data is then processed and stored in DataFrames.

Usage:
- Ensure you have the necessary dependencies installed (requests, BeautifulSoup, pandas, undetected_chromedriver).
- Execute the code and it will automatically scrape property data from Rightmove and Zoopla.
- The scraped data is stored in separate DataFrames, 'otm_data','rightmove_data' and 'zoopla_data', respectively.

Code Structure:
- The code is divided into three parts, one for Rightmove scraping and other two for OTM and Zoopla scraping.
- Each part consists of a class that handles the scraping and data processing.

Rightmove Scraper:
- Class Name: RightmoveScraper
- Methods:
  - fetch(url): Sends an HTTP GET request to a URL and returns the response.
  - parse(html): Extracts property details from the HTML content using BeautifulSoup.
  - to_dataframe(): Converts the scraped data into a DataFrame.
  - transform_run(url): Performs the web scraping process for Rightmove.

Zoopla Scraper:
- Class Name: ZooplaScraper
- Methods:
  - parse(html): Extracts property details from the HTML content using BeautifulSoup.
  - to_dataframe(): Converts the scraped data into a DataFrame.
  - transform_run(url): Performs the web scraping process for Zoopla.
  
OTM Scraper:
- Class Name: OTM
- Methods:
  - parse(html): Extracts property details from the HTML content using BeautifulSoup.
  - to_dataframe(): Converts the scraped data into a DataFrame.
  - transform_run(url): Performs the web scraping process for the OTM website.


Rightmove Scraper:
- The RightmoveScraper class handles the scraping and data processing for Rightmove website.
- It contains the following methods:

  - fetch(url):
    - Parameters:
      - url: The URL to fetch the HTML content from.
    - Returns:
      - The response content as a string.
    - Description:
      - Sends an HTTP GET request to the specified URL and returns the response content.

  - parse(html):
    - Parameters:
      - html: The HTML content to parse.
    - Description:
      - Extracts property details such as prices, titles, addresses, descriptions, and agents from the HTML content using BeautifulSoup.
      - The extracted data is stored in the 'results' list.

  - to_dataframe():
    - Returns:
      - A pandas DataFrame containing the scraped property data.
    - Description:
      - Converts the scraped property data stored in the 'results' list into a pandas DataFrame.

  - transform_run(url):
    - Parameters:
      - url: The URL to scrape property data from.
    - Returns:
      - A pandas DataFrame containing the scraped property data.
    - Description:
      - Performs the web scraping process for Rightmove.
      - It navigates to the specified URL, fetches the HTML content, calls the 'parse' method to extract property details, converts the results to a DataFrame using the 'to_dataframe' method, and performs additional data manipulation and feature extraction.
      - Finally, it returns the processed DataFrame.

Zoopla Scraper:
- The ZooplaScraper class handles the scraping and data processing for Zoopla website.
- It contains the following methods:

  - parse(html):
    - Parameters:
      - html: The HTML content to parse.
    - Description:
      - Extracts property details such as prices, titles, addresses, descriptions, and agents from the HTML content using BeautifulSoup.
      - The extracted data is stored in the 'results' list.

  - to_dataframe():
    - Returns:
      - A pandas DataFrame containing the scraped property data.
    - Description:
      - Converts the scraped property data stored in the 'results' list into a pandas DataFrame.

  - transform_run(url):
    - Parameters:
      - url: The URL to scrape property data from.
    - Returns:
      - A pandas DataFrame containing the scraped property data.
    - Description:
      - Performs the web scraping process for Zoopla.
      - It creates a new instance of Chrome (undetected_chromedriver), navigates to the specified URL, fetches the HTML content, calls the 'parse' method to extract property details, converts the results to a DataFrame using the 'to_dataframe' method, and performs additional data manipulation and feature extraction.
      - Finally, it returns the processed DataFrame.

"""






Main Execution:
- The main execution part of the code creates instances of the RightmoveScraper, OTM scraper and ZooplaScraper classes.
- It then iterates over the sales and rentals URLs for OTM, Rightmove and Zoopla, scraping property data from each URL and storing the results in separate DataFrames.
- Random time delays between requests are included to avoid overwhelming the websites.
- Finally, it concatenates the sales and rentals data into a single DataFrame named 'otm_data','rightmove_data' and 'zoopla_data', respectively.

Dependencies:
- requests: Used for making HTTP requests to fetch HTML content.
- BeautifulSoup: Used for parsing HTML content and extracting data using CSS selectors.
- pandas: Used for data manipulation and storing scraped data in DataFrames.
- undetected_chromedriver: Used for automating browser actions (specifically for Zoopla scraping).

## Architecture diagram

![first](https://github.com/ajayi-george/Dicey-tech-project/assets/128624260/de5f347a-33da-4e8b-97b3-1198d5d6cd89)
