# General information about Webscraper.io
<br><br>
WebScraper.io is a browser-based tool designed for extracting data from websites with ease. It offers a user-friendly interface that allows for data collection without the need for coding. The platform can navigate and scrape multiple pages, making it useful for collecting large datasets from websites. After downloading, the data is merged and structured using Google Sheets. Google Sheets is a cloud-based spreadsheet application that is part of Google's suite of office tools. It allows users to create, edit, and collaborate on spreadsheets in real-time from any device with internet access. To clean the data and automate the process in Google Sheets we need to use some codes. 

The following figure shows how the process looks for the daily download of data via webscraping.

1. The data is provided by the market data provider [Alpha Vantage](../00-Alpha_Vantage).
2. Using the Airtable add-on application Data Fetcher, the data is extracted from Alpha Vantage and stored in Airtable. This is done automatically on a daily basis.  
3. The first table in Airtable always contains the most recent daily stock data. Whenever there is a change due to a new reload of data, the new data set is loaded into the second table in Airtable via the external tool Zapier.
4. In this way, the data is collected and cumulated to provide a history of the respective shares. 

![Alt Image Text](./Images/Airtable_dataflow1.png "Dataflow")
  
<br><br><br><br>

## Result
<br>
The end result is a database with daily records on the requested shares. 
<br><br>

![Alt Image Text](./Images/Airtable_Setup36.png "Setup36")

<br><br><br><br>

## Running costs
<br>

| Application  | Free Version  | Note          |
|-----------   |---------------|---------------|
| Airtable     | (yes)         | Free version available - but probably not enough capacity for automation runs. A Team subscripton of USD 24 per month is required. |
| Data Fetcher | (yes)         | Free version available - but probably not enough capacity for runs. Subscription for USD 24 per month is sufficient for collecting data of about 50 shares.        |
| Zapier       | yes           |           |

<br><br>

Here the detailed costs of Airtable: [Pricing](https://airtable.com/pricing). 
<br>
![Alt Image Text](./Images/Airtable_Premium.png "Premium")
<br><br>
Here the detailed costs of Data Fetcher: [Pricing](https://datafetcher.com/).  
<br>
![Alt Image Text](./Images/Airtable_Setup9.png "Setup9")
