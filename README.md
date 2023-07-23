

**Introduction**

In this project, machine learning is be used to analyse how news articles may affect the stock market. By studying the connection between the  news stories and changes in company stock prices, the study will examine the effect of news items on the stock market. The machine learning model for the project will be trained using historical stock prices and news articles. The effectiveness of the model will be assessed using statistical criteria including recall, accuracy, and precision. The model will be put to the test on a real-time news feed to see how well it can forecast changes in stock price. 

**Methodology**

**1.Libraries Imported**


The script starts out by importing the required libraries. These libraries offer a range of tools and methods for handling and analysing data. The nltk library is used for tasks involving natural language processing, the fuzzywuzzy library is used for fuzzy string matching, and the pandas library is used for data manipulation and analysis.

**2.Loading Data:**

The script loads two CSV files: newsfeed - News (5).csv and ticker.csv. These files likely contain data related to news articles and company ticker symbols, respectively. The data is loaded into DataFrame objects using the pd.read_csv() function. A DataFrame is a two-dimensional data structure that resembles a table, where data is organized in rows and columns.

**3.Data preprocessing**

Some preprocessing operations are carried out prior to data analysis. For uniformity, the 'Description' column in the df DataFrame has been renamed to 'description'. Using the dropna() function, rows with blank values in the 'Description' column are removed. This makes sure that only accurate and comprehensive data are used for additional analysis. The 'Description' column's text has been tokenized, or divided into separate words or "tokens," using the nltk.word_tokenize() function. The text is now ready for further examination.
**
4.Matching company name**

 The script seeks to match the firm names listed in the df2 DataFrame with the company names indicated in the news descriptions. In the df DataFrame, it adds a new column called "common_company_names" that will hold the matching companies' names as strings. This matching procedure makes it easier to determine the business a news piece is discussing.
 
**5.Fuzzy String Matching**

 The script makes use of fuzzy string matching methods from the fuzzywuzzy library to enhance the matching of firm names even further. Even if two strings are not exactly the same, fuzzy string matching enables approximative matching. The fuzz.token_set_ratio() function is used to compare the common company names with the firm names in the df2 DataFrame as the script iterates over each row in the df DataFrame. The similarity score between two strings is determined by this function based on the existence of shared tokens. The related symbol from df2 is given to the 'Matched Symbol' column in the df DataFrame if the similarity score is greater than a predetermined cutoff (80 in this case). This process aids in connecting the news stories to particular brand icons.
 
**6. Additional Matching**

In addition to matching fuzzy strings, the script also matches specific firm names that may not have been accurately matched in the past. The 'Matched Symbol' column is then filled with the corresponding symbol once each news item's title has been compared using fuzzy string matching to these specified names. This phase makes sure the script includes all pertinent news items for a particular organisation.


**7.Stock Data Retrieval**

After finding the matching symbols, the script collects stock information for those symbols. It makes use of the yfinance and pandas_datareader libraries, which give users access to financial data from a variety of sources. The script iterates over each row in the df DataFrame, obtains the stock data for a predetermined time frame (5 days before and after the news date), and computes the average of the 'High' and 'Low' prices. The symbol serves as the key to the stock dictionary, which holds the stock data. The essential stock data is made available in this phase so that you may analyse how news affects stock prices.

**8.Impact calculation**

 a. The script iterates through each row in the df DataFrame, which contains the matching news items and their corresponding symbols. a. Iterating through Each Row.
 
 b.  Retrieving Stock Data: The script searches the stock dictionary for the stock data for each news item's matching symbol. This stock data includes the high and 
     low prices for a particular time frame, often 5 days prior to and 5 days following the news date.
     
 c.  Calculating Average values: For the stock data obtained in the previous step, the script calculates the average of the "High" and "Low" values. The stock price 
     before and after the announcement is estimated in  this average price.
     
 1.Retrieve Stock Data: The script pulls the corresponding stock data from the stock dictionary for a given news story. The opening price, closing price, high price, 
   low price, and volume traded for a given time period (for example, the five days before and five days following the news date) are some of the common details 
   included in this stock data.
   
 2.Calculate Average: The script focuses on the "High" and "Low" values of the stock data for simplicity. It calculates the average value by adding the "High" and 
     "Low" values together and dividing the sum by 2. This provides an estimate of the stock price before and after the news announcement.
              
              Average = (High + Low) / 2
              
     The resulting average value represents an approximation of the stock price during that specific time period.

