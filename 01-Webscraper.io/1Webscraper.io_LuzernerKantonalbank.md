## Luzerner Kantonalbank
<br><br>
This guide details how to access the interest rates on the Luzerner Kantonalbank website. In case you you don't have Webscraper.io installed yet - click [here](0Webscraper.io_Setup.md). 
<br><br>
If you have Websracper.io installed: Go to this [website](https://www.lukb.ch/de/private/finanzieren/hypotheken/festhypothek). 

1. Scroll down where the interest rates are shown.
2. Left click and select **Inspect**.
<br><br>
![Alt Image Text](./Images/WS_Setup6.png "Setup6")

<br><br><br><br>

1. Select the section **Web Scraper**
2. **Create new sitemap**
3. **Create Sitemap**
<br><br>
![Alt Image Text](./Images/WS_Setup7.png "Setup7")

<br><br><br><br>

1. Name the Sitemap - in this example its called ```0LuzernerKantonalbank```.
2. Enter the website ```https://www.lukb.ch/de/private/finanzieren/hypotheken/festhypothek```.
3. **Create Sitemap**.
<br><br>
![Alt Image Text](./Images/WS_Setup8.png "Setup8")

<br><br><br><br>

1. **Add new selector**
2. Name the selector - in this exampled ```InterestRate```
3. Select as a *Type* **Table**
4. Click in the line *Selector* on **Select**
5. Now you can mark the whole table with the interest rates
6. **Done selecting**
<br><br>
![Alt Image Text](./Images/WS_Setup9.png "Setup9")

<br><br><br><br>

1. Now you have to select the header. Click on **Select**.
2. Since there is now header in the table - select the first line.
3. **Done selecting**
<br><br>
![Alt Image Text](./Images/WS_Setup10.png "Setup10")

<br><br><br><br>

1. With the data rows selector you now select the data. Click on **Select**.
2. Mark the whole table - incuding the first line (header line). Sometimes the shift key has to be pressed to select all lines.
3. **Done selecting**
4. To review our setup click now on **Data preview**.
<br><br>
![Alt Image Text](./Images/WS_Setup12.png "Setup12")

<br><br><br><br>

The preview should now include the years and interest rates as in the figure below. Please check if the first line of the table is entered twice - once as a header and once as a data row. If this is not the case, please reselect the table, header and data again till it all data is included correctly. 
<br><br>
If everything looks okay, you can close the *Data Preview*. 
<br><br>
![Alt Image Text](./Images/WS_Setup13.png "Setup13")

<br><br><br><br>

1. Tick the box **Multiple**
2. Name the columns ```Duration``` and ```InterestRate```
3. Tick both boxes **Include into result**
4. Go on **Data preview** again and check, if now the header has changed according your adjustments.
5. **Safe selector**
<br><br>
![Alt Image Text](./Images/WS_Setup14.png "Setup14")

<br><br><br><br>

Now we execute the webscraping.
1. Click on **Sitemap** ***0LuzernerKantonalbank***
2. Select **Scrape**
<br><br>
![Alt Image Text](./Images/WS_Setup15.png "Setup15")

<br><br><br><br>

You are now asked about the request interval and page load delay. 

- Request interval: Determines the amount of time the scraper waits between sending requests to web pages.
- Page load delay: Specifies the duration the scraper waits for a page to fully load before extracting the data.
<br>
It's done to mimic human browsing behavior, avoid overloading the server, and reduce the chances of getting banned or blocked due to rapid or frequent requests. For the time being, we leave the default settings at 2000 miliseconds.
Therefore, just click **Start scraping**. If we then see that scraping is not working, we could always increase the time here.
<br><br>

![Alt Image Text](./Images/WS_Setup16.png "Setup16")

<br><br><br><br>

A window now opens and closes itself again after a few seconds. After that click on **refresh**.
<br><br>
![Alt Image Text](./Images/WS_Setup17.png "Setup17")

<br><br><br><br>

You will now see the data that has been downloaded. Make sure that they are complete and that each column contains data. Be aware that only the first few lines of the dataset are displayed.
<br><br>
![Alt Image Text](./Images/WS_Setup18.png "Setup18")

<br><br><br><br>

Now go back to **Sitemaps** where you will see the created function for downloading the Luzerner Kantonalbank data.
<br><br>
![Alt Image Text](./Images/WS_Setup19.png "Setupxx")

<br><br><br><br>


### Webscraper.io - Cloud
<br><br>
We have now made the setup in the local webscraper.io application. In order for this to run automatically on a daily basis, we need to do the installation in webscraper.io cloud. How to get an cloud account you see [here](0Webscraper.io_Setup.md).
<br><br>
We now copy the settings from the sitemap we made. To do this, click on the sitemap **0LuzernerKantonalbank** in your Chrome browser.
<br><br>
![Alt Image Text](./Images/WS_Setup20.png "Setupxx")

<br><br><br><br>

Choose now the tab **Sitemap 0Luzerner Kantonalbank** and select **Export Sitemap**.
<br><br>
![Alt Image Text](./Images/WS_Setup21.png "Setupxx")

<br><br><br><br>

Copy now the displayed code.
<br><br>
![Alt Image Text](./Images/WS_Setup22.png "Setupxx")

<br><br><br><br>

Now open your [Cloud account](https://cloud.webscraper.io) and go to **Import Sitemap**.
1. Paste the code you copied in the previous step
2. Name the Sitemap again - in this case ```0LuzernerKantonalbank```
3. **Import**
<br><br>
![Alt Image Text](./Images/WS_Setup23.png "Setupxx")

<br><br><br><br>

You have now created the sitemap in your cloud environment.
1. Click now on **Scrape** to see if it works correctly.
2. Wait a few seconds for the file to be created - reload the page after a few seconds.
3. Click on **Preview**.
<br><br>
![Alt Image Text](./Images/WS_Setup24.png "Setupxx")

<br><br><br><br>

Now check whether all content has been loaded here. If something is missing - for example, the column with the interest rates - you have to run the setup again locally in your Chrome browser. You can then export the adjusted code again and insert it in your sitemap under **Edit**. 
<br><br>
![Alt Image Text](./Images/WS_Setup25.png "Setupxx")
<br><br>
Please be aware that only the first 10 lines are shown in the *Data Preview*.
<br><br><br><br>

Every time a scrape is executed, this file is created. In order to be able to merge the data from all financial institutions into one file, we need to add the following columns so that we can distinguish the data:

- Name of the financial institution
- Date of download

In addition, we have to edit the data so that they look the same in all sitemaps (e.g. dot everywhere instead of comma for the separation of decimal places, etc.). We do this under **Praser**.
1. Go to **My Sitemaps**
2. Select **0LuzernerKantonalbank** Sitemap
3. Go to **Parser**. Here you see the existing columns
4. **Add column**
<br><br>
![Alt Image Text](./Images/WS_Setup26.png "Setupxx")

<br><br><br><br>

We now add the a colum with the name of the financial institution. 
1. Name the column ```Financial_Institution```
2. Select as source column **web-scraper-start-url**
3. **Save**
<br><br>
![Alt Image Text](./Images/WS_Setup27.png "Setupxx")

<br><br><br><br>

A new column has now been created. 
1. Go to **Add parser**
2. **Regex match**
<br><br>
![Alt Image Text](./Images/WS_Setup28.png "Setupxx")

<br><br><br><br>

Currently, the input is the URL where we download the data. We would like to get the name of the financial institution from this URL. For this we use a code in Regex. This shortens the URL accordingly.
<br>
1. Use the code ```www\.(.*?)\.ch```
2. Select **Group 1**
3. As *Output* you should now get the name **lukb**
4. **Save** 
<br><br>
![Alt Image Text](./Images/WS_Setup29.png "Setupxx")

<br><br><br><br>

Now we add a second column. Click on **Add time scraped**. You see now the added column *time-scraped*. Click now on the field **Convert UNIX timestamp**.
<br><br>
![Alt Image Text](./Images/WS_Setup30.png "Setupxx")

<br><br><br><br>

1. Select your preferred time **Format**.
2. Check the *Output*.
3. **Save**.
<br><br>
![Alt Image Text](./Images/WS_Setup31.png "Setupxx")

<br><br><br><br>

In the list below you will now see the updated list with the two added columns. We will now edit the two columns **Duration** and **InterestRate** so that we finally have the same data format for all files.
<br>
1. Now go to the **Duration** column first.
2. Click on **Add parser**.
3. Select **Regex match**.
<br><br>
![Alt Image Text](./Images/WS_Setup32.png "Setupxx")

<br><br><br><br>

We now use a code so that only the figure remains - words are excluded.
1. Enter the following code at *Regex* ```(\d+)```
2. Check *Output*
3. **Save**
<br><br>
![Alt Image Text](./Images/WS_Setup33.png "Setupxx")

<br><br><br><br>

Now we adjust the column **InterestRate**.
1. As before, select the **InterestRate** column - click on **Add parser**.
2. Select **Regex match**.
3. Enter the following code at *Regex* ```(\d+).(\d+)``` - This code includes decimal places in a number.
4. Check *Output*.
5. **Save**.
<br><br>
![Alt Image Text](./Images/WS_Setup34.png "Setupxx")

<br><br><br><br>

Your list should now look like the image below. The following columns should be included.
<br>
- Web-scraper-order
- Web-scraper-start-url
- Duration *(only number may be included)*
- InterestRate *(only a number is allowed)*
- Financial Instituition
- time-scraped *(always the same format must be used)*
<br>
Regardless of the financial institution, all lists should be set up and formatted in exactly the same way. Otherwise there will be a mess when the data is merged. 
<br><br>
Unless you can't get the list in Webscraper.io into this format. The data must be further formatted in Google Sheet. See the example of [Credit Suisse](1Webscraper.io_CreditSuisse.md).
<br><br>

![Alt Image Text](./Images/WS_Setup35.png "Setupxx")

<br><br><br><br>

Now that we have structured and formatted the data, we need to set up a job to automatically download the data on a daily basis. To do this, go to **Schedule** in the corresponding sitemap.
<br>
1. **Enable scheduler**.
2. Set the *Scheduler Type* to **Daily**.
3. Under *Run a job on*, select the days on which the interest rate is to be updated. In this example, all weekdays are selected.
4. Specify the time when the job is to be run.
5. The remaining settings can be left as they are.
6. **Save**.
<br><br>
![Alt Image Text](./Images/WS_Setup36.png "Setupxx")

<br><br>

We have now made the settings so that the Luzerner Kantonalbank interest rates are automatically extracted on a daily basis. 

<br><br><br><br>




### Google Sheets
<br><br>
Before we proceed with Google Sheets, ensure that you've completed the general setup for Google Sheets (account creation) and established the interface between Webscraper.io and Google Sheets. If you need to set this up, please refer to [Webscraper.io_Setup](0Webscraper.io_Setup.md).
<br><br>
When the file in [Google Sheets](https://docs.google.com/spreadsheets/) is in place select the file **0LuzernerKantonalbank**. Your Google spreadsheet's name matches your sitemap.
<br><br>
![Alt Image Text](./Images/WS_Setup601.png "Setupxx")

<br><br><br><br>

In the table, you will now see all the data that was loaded from the sitemap **0LuzernerKantonalbank**. If there are rows where the data is incorrect, delete the content of that data. In Webscraper.io, you can then manually execute the **Scrape** again. After a few seconds the file will be updated.

If data is missing - for instance, the interest rate - also trigger the run **Scrape** in Webscraper.io. If there's no interest rate present in the *Preview Data* there either, you'll need to adjust the sitemap code. To do this, go to your local Webscraping.io and redefine the selectors. Enter the new code in Webscraper.io Cloud under **Edit** of the respective sitemap.
<br><br>
In our case, the data appears as we would expect it to. However, we want to modify the sheet such that the following cleaning steps are applied:

- The header should appear only once.
- If there's no number in column E, the row should be deleted.
- Duplicate rows should be removed. 
<br><br>
![Alt Image Text](./Images/WS_Setup602.png "Setupxx")

<br><br><br><br>

To implement this, we need to write a code. For this, navigate to **Extension**. Select **Apps Script**
<br><br>
![Alt Image Text](./Images/WS_Setup603.png "Setupxx")

<br><br><br><br>

Delete the existing code and enter the following one in the console. 
```
function checkAndDeleteRows() {
  var sheet = SpreadsheetApp.getActiveSpreadsheet().getActiveSheet();
  var lastRow = sheet.getLastRow();
  var lastCol = sheet.getLastColumn();
  var range = sheet.getRange(1, 1, lastRow, lastCol);
  var values = range.getValues();
  var rowsToDelete = [];
  var uniqueCombinations = {};

  for (var i = values.length - 1; i > 0; i--) {  // Loop starts from the last row and ignores the first row
    var columnD = values[i][3]; // 0-based, so 3 is for Column D
    var columnF = values[i][5]; // 0-based, so 5 is for Column F

    var combinationKey = columnD + "_" + columnF; // Create a unique key for the combination
    
    // Check if the combination already exists or if Column E doesn't contain a number
    if (uniqueCombinations[combinationKey] || !isNumeric(values[i][4])) {
      rowsToDelete.push(i);
    } else {
      uniqueCombinations[combinationKey] = true;
    }
  }

  // Delete rows in reverse order to avoid shifting of rows
  for (var j = 0; j < rowsToDelete.length; j++) {
    sheet.deleteRow(rowsToDelete[j] + 1);
  }
}

function isNumeric(value) {
  return !isNaN(parseFloat(value)) && isFinite(value);
}
```
<br><br>
After pasting the code:
1. **Save**
2. **Run**
<br><br>
![Alt Image Text](./Images/WS_Setup604.png "Setupxx")

<br><br><br><br>

If this is the first code you're implementing in App Scripts for this spreadsheet, you'll need to grant the application the necessary permissions before executing the code. Click on **Review permissions**.
<br><br>
![Alt Image Text](./Images/WS_Setup90.png "Setupxx")

<br><br><br><br>

Select your Google account.
<br><br>
![Alt Image Text](./Images/WS_Setup92.png "Setupxx")

<br><br><br><br>

1. Click on **Advanced**
2. Click on **Go to Untitled project (unsafe)**. If you have named your code in *App Script*, it can be named differently.
<br><br>
![Alt Image Text](./Images/WS_Setup93.png "Setupxx")

<br><br><br><br>

**Allow**
<br><br>
![Alt Image Text](./Images/WS_Setup94.png "Setupxx")

<br><br><br><br>

The code is now executed. 
<br><br>
![Alt Image Text](./Images/WS_Setup951.png "Setupxx")

<br><br><br><br>

Go now back to the **0LuzernerKantonalbank** spreadsheet and review the data. The script seems to work, the line that had no percentage was deleted. 
<br><br>
![Alt Image Text](./Images/WS_Setup605.png "Setupxx")

<br><br><br><br>

Now we want this code to be executed whenever data is loaded into the spreadsheet. Now go back to the *Apps script* application.
1. Go to **Extensions**
2. Select **Apps Script**
3. In the Apps Script application, click on the clock icon (*Triggers*) on the left side
4. **Add Trigger**
<br><br>
![Alt Image Text](./Images/WS_Setup961.png "Setupxx")

<br><br><br><br>

Now we specify the trigger.
1. Select event source: **From Spreadsheet**
2. Select event type: **On change**
3. Rest stays the same
4. **Save**
<br><br>
![Alt Image Text](./Images/WS_Setup971.png "Setupxx")

<br><br><br><br>

We have now finished setting up the **0LuzernerKantonalbank** spreadsheet. Whenever the data is reloaded, the content is automatically processed and checked. A history of daily interest rates of the Luzerner Kantonalbank is now automatically created in the table - this is expanded daily. 

To check whether everything is correct, you can trigger the scraping again manually in Webscraper.io. If there are no duplicate values, no lines without percentages and the header still only appears once after the reload of the spreadsheet, then everything has worked.

<br><br><br><br>

Here you can see how to consolidate the data of all financial institutions into a single file - [0Webscraper.io_Setup](0Webscraper.io_Setup.md).

<br><br><br><br>


