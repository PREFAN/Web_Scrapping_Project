# Web_Scrapping_Project
#World Bank API Scraper Project Documentation
#URL of Chosen target Website
The target website for this project is URL: https://api.worldbank.org. This URL is a suitable target for showing API handling because it is a structured public and real-time data that is easily accessible without user login or authentication. The API returns clean JSON data, which simplifies parsing and eliminates the need for complex HTML scraping. The JSON data is easily converted to CSV file making it more cleaner and human readability friendly. Parameters like MRV=1 helps to fetch the most recent data reducing payload size and improves efficiency. The API support pagination and rate-limiting which enables users to practice large dataset and implementing retry logic. Using this API URL also helps users to acquit themselves with how to merge multiple datasets based on country codes deploying Pandas and Python. It also avoids the need to handle JavaScript rendered content or dynamic page loading. Ultimately, the API produces a clean, fast, and robust example of RESTful API interaction.
#Step-by-Step Instruction  
The project directory was created using the following command: 
cd ~ 
mkdir worldbank_api_project 
cd worldbank_api_project, and activated using the command source venv/bin/activate. The command pip3 install requests pandas was run to install Pandas for data manipulation and requests for HTTP requests. The python script named worldbank_api_scraper.py that contain the code that automatically fetches the latest country level data from World Bank API, process it, and save it to a CSV file inside the project folder. The Python script was ran using the command python worldbank_api_scraper.py in the terminal. It generates a CSV file named worldbank_country_stats.csv in the same folder. Finally, the CSV was opened using excel to review that scraper was able to fetch 262 rows with missing values which was later cleaned to 255 rows to worldbank_country_stats.csv folder.

#Description of Data points collected and their significance
The scraper fetches five important data points from the World Bank API which include country name, which is the primary identifier for grouping and organizing the data. The other data include population, growth rate, area, and density. These metrics together allow users to analyze and compare demographic and spatial characteristics of countries. The data collected is valuable because it helps users who are within business landscape to assess market size and customer base. Also, it helps make policies tailored to foster economic growth, social development and help check signal challenges such as aging populations or overpopulation. Lastly, the data fetched is critical for land use, planning, environment conservation, and zoning, which are cardinal parameters for disaster preparedness and resources allocation. In the nutshell, the data is valuable for research in economics, urban planning, public policy, global development, and support forecasting trend analysis and cross-country comparison.

#Challenges encountered and Resolution   
1.	The API return status code 429(“Too Many Request”) when I exceeded my request limit. To resolve this issue, I added the command time.sleep(5) which was initially absent to the code to pause the execution of the code for 5seconds. This helped to avoid too many requests too quickly, giving the server time to reset the rate limit and reducing the chances of repeated errors.

2.	The API was producing duplicate records due to variations in reporting or indicator updates. The command drop_duplicates(subset=["iso3"]) was added to remove any duplicate rows in the DataFrame and ensures that each country appears only once in the data, preventing multiple entries for the same country.

3.	Some countries did not have recent data for one or more indicators, resulting in missing values. The command combined = combined.dropna() was added to the code to further clean the missing values. This reduced the 262 datasets initially retrieved to 255 rows after dropping missing values.

4.	The World Bank website continue to change endpoint URL, data formats or indicators because website is constantly updated. I regularly checked the World Bank API documentation and INDICATOR dictionary and API_TEMPLATE for update.

#Advantages of scraping via an API vs. Traditional HTML
1.	Web scraping deals with raw, unstructured HTML that requires extensive processing. Your scraper needs to parse the HTML, clean the data, and transform it into a usable format. In contrast, APIs deliver data in clean, structured formats like JSON or XML that are immediately ready for use in your applications.
2.	Web scrapers are vulnerable to website changes and updates. Any modification to the HTML structure can break your scraping code, requiring frequent maintenance. APIs provide a more stable environment with versioning support and documented changes, though they may occasionally deprecate features or endpoints.
3.	Web scraping operations tend to be slower, especially when dealing with large-scale data collection or JavaScript-heavy websites. APIs provide optimized data delivery with minimal overhead, making them significantly faster for most use cases.
4.	Building and maintaining web scrapers demands significant technical knowledge. You'll need to understand HTML structure, handle anti-bot measures, and manage complex parsing logic. APIs typically offer clear documentation and simple integration patterns, making them more accessible for developers of all skill levels.
5.	Web scraping exists in a complex legal landscape. While scraping public data is generally acceptable, you must carefully consider website terms of service and adhere to best practices of web scraping. APIs provide a clear legal framework through their terms and conditions, making them a safer choice from a compliance perspective.


