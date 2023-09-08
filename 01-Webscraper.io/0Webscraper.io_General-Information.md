# General information about Webscraper.io
<br><br>
[WebScraper.io](https://webscraper.io/) is a browser-based tool designed for extracting data from websites with ease. It offers a user-friendly interface that allows for data collection without the need for coding. The platform can navigate and scrape multiple pages, making it useful for collecting large datasets from websites. After downloading, the data is merged and structured using [Google Sheets](https://www.google.com/sheets/about/). Google Sheets is a cloud-based spreadsheet application that is part of Google's suite of office tools. It allows users to create, edit, and collaborate on spreadsheets in real-time from any device with internet access. To clean the data and automate the process in Google Sheets we need to use some codes. 

The figure below outlines the process for daily data download via webscraping:

1. Data is sourced from various Swiss financial institutions. For this use case, we extract data from two banks and one insurance company. The process can be easily scaled to include other financial entities.
2. Data is harvested from the websites using Webscraper.io.
3. Initially, the data is saved in Webscraper.io's cloud where preliminary data cleansing occurs.
4. The data is then exported to Google Sheets. A default export channel between Webscraper.io and Google Sheets is pre-established.
5. Within Google Sheets, the data undergoes further structuring, and tables from different financial institutions are consolidated into a single table.
<br>
Compared to extraction via an API, webscraping provides less structured data due to varying homepage layouts and content across sites. Data cleansing and structuring become more critical and constitute a significant portion of the task with webscraping.
<br>

![Alt Image Text](./Images/WS_Dataflow.png "Dataflow")
  
<br><br><br><br>

## Result
<br>
The final result is a list of interest rates over various terms from different financial institutions. These are updated daily.
<br><br>

![Alt Image Text](./Images/WS_Result.png "Result")

<br><br><br><br>

## Running costs
<br>

| Application  | Free Version  | Note          |
|-----------    |---------------|---------------|
| Webscraper.io | (yes)         | A free version is available, but it doesn't offer all the services (cloud, parser, etc.) necessary for this setup. The "Project" subscription is sufficient for accessing around 170 websites per month. The costs are USD 50. |
| Google Sheets | yes         | As long as no more than 15 GB of storage space is required, the free version suffices. |

<br><br>

Here the detailed costs of Webscraper.io: [Pricing](https://webscraper.io/pricing). 
<br>
![Alt Image Text](./Images/WS_Pricing.png "Premium")
<br>
A page/cloud credit corresponds to a single page load in the Web Scraper Cloud. If the scraper navigates through 100 pages, it will consume 100 page credits. Extracting 100 records from just one page will only deduct one page credit.
<br><br>
Here the detailed costs of Google Sheets: [Pricing](https://www.google.com/sheets/about/#pricing).  
<br>
![Alt Image Text](./Images/WS_Pricing_Google.png "Setup9")
