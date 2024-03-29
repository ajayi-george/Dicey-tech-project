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

Function: load_data_to_bigquery(df, tbl)

This function loads data from a Pandas DataFrame into a specified table in Google BigQuery.

Parameters:

df (DataFrame): The DataFrame containing the data to be loaded.

tbl (str): The name of the table in BigQuery where the data will be loaded.
Steps:

Set the Google Cloud credentials path using os.environ['GOOGLE_APPLICATION_CREDENTIALS'].
Define the project ID, dataset ID, and table ID based on your Google Cloud configuration.
Create a BigQuery client using bigquery.Client().
Set up a try-except block to handle table creation and data loading.
Inside the try block:
Define the table reference using client.dataset(dataset_id).table(table_id).
Create a bigquery.Table object and use client.create_table() to create the table in BigQuery. If the table already exists, an exception is raised and caught.
Load the DataFrame into the table using client.load_table_from_dataframe(), specifying the DataFrame, table reference, and location.
If an exception occurs, log the error message, delete the table using client.delete_table(), and return from the function.
Wait for the data loading job to complete using job.result().
Print the number of rows loaded into the table.
Ensure that you have the necessary dependencies installed and provide the correct project ID, dataset ID, table name, and DataFrame (data) when calling the load_data_to_bigquery() function.

![Screenshot (660)](https://github.com/ajayi-george/Dicey-tech-project/assets/128624260/bca55fb3-e845-432a-8710-4b274595f86c)

Please note that this code assumes you have the required permissions and access to create tables and load data into Google BigQuery.

## Architecture diagram

![Screenshot (659)](https://github.com/ajayi-george/Dicey-tech-project/assets/128624260/95ae76fe-48b8-4dad-ae38-c1956210182c)

