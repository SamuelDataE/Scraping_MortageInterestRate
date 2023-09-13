## Generali Insurance
<br><br>
This guide details how to access the interest rates on the Gernerali website. In case you you don't have Webscraper.io installed yet - click [here](0Webscraper.io_Setup.md). 
<br><br>
If you have Websracper.io installed: Go to this [website](https://www.generali.ch/privatkunden/wohnen-bauen/hypotheken). 

1. Scroll down where the section is with *Useful information about mortgages at a glance*.
2. Click on the symbol to oben the interest rates.
3. Left click and select **Inspect**.
<br><br>
![Alt Image Text](./Images/WS_Setup406.png "Setup6")

<br><br><br><br>

1. Select the section **Web Scraper**
2. **Create new sitemap**
3. **Create Sitemap**
<br><br>
![Alt Image Text](./Images/WS_Setup407.png "Setup7")

<br><br><br><br>

1. Name the Sitemap - in this example its called ```0Generali```.
2. Enter the website ```https://www.generali.ch/en/privatkunden/wohnen-bauen/hypotheken```.
3. **Create Sitemap**.
<br><br>
![Alt Image Text](./Images/WS_Setup408.png "Setup8")

<br><br><br><br>

1. **Add new selector**
2. When the Generali page is accessed, the interest rates are not yet directly visible. The table must first be opened. Open the table **Interest rates** on the page.
3. Name the selector - in this exampled ```Link```.
4. Select **Element click** as a *Type* .
5. Click in the line *Selector* on **Select**.
6. Now mark the whole selection which opened when you clicked on **Interest rates** in step 2#. 
7. **Done selecting**.
<br><br>
![Alt Image Text](./Images/WS_Setup409.png "Setup9")

<br><br><br><br>

1. Now you have to select the *Click selector*. Click on **Select**
2. Select on the page **Interest rates**
3. **Done selecting**
4. Select as *Click type*: **Click once (pagination, tabs)**
5. Select as *Click element uniqueness*: **Unique Text**
6. Untick the box **Multiple**
7. Select *Discard*: **Never Discard**
8. **Save selector**
<br><br>
![Alt Image Text](./Images/WS_Setup410.png "Setup10")
<br><br>
In the *Selector* we have now indicated from which area we want to download the data. With the *Click Selector* we indicate what has to be clicked first by Webscraper.io to see the area above.

<br><br><br><br>

You have now created the first *Selector*. Click now on your sector **Link**.
<br><br>
![Alt Image Text](./Images/WS_Setup412.png "Setup12")

<br><br><br><br>

1. **Add new selector**
2. In the selector before, we entered what Webscraper.io has to click on the website. In this selector, we now specify which data should be scraped.
3. Name the selector - in this exampled ```InterestRates```.
4. Select **Table** as a *Type* .
5. Click in the line *Selector* on **Select**.
6. Now mark within the section you marked in the selector before only the table with the interest rates. It is important that all interest rates for a fixed mortgages are marked. 
7. **Done selecting**.
<br><br>
![Alt Image Text](./Images/WS_Setup4121.png "Setup9")

<br><br><br><br>

1. Click in the line *Header row selector* on **Select**.
2. Now mark the respective header. 
7. **Done selecting**.
<br><br>
![Alt Image Text](./Images/WS_Setup4122.png "Setup9")

<br><br><br><br>

1. Click in the line *Data rows selector* on **Select**.
2. Now mark all the interset rates. Since it is not possible to exclude the variable interest rates, you must also select them. 
7. **Done selecting**.
<br><br>
![Alt Image Text](./Images/WS_Setup4123.png "Setup9")

<br><br><br><br>

1. Now we do the rest of the settings. Tick the box **Multiple**.
2. Name the columns ```Duration``` and ```InterestRate```.
3. Tick the boxes **Include into result** only for *Duration* and *InterestRate*. We don't want to know the interest rates for 2nd mortgages.
4. Go to **Preview Data**
<br><br>
![Alt Image Text](./Images/WS_Setup4124.png "Setup9")

<br><br><br><br>

The preview should now include the years and interest rates as in the figure below. If this is not the case, please reselect the table, header and data again till it all data is included correctly. 
<br><br>
If everything looks okay, you can close the *Data Preview* and finish the setup with **Save selector**.
<br><br>
![Alt Image Text](./Images/WS_Setup4125.png "Setup13")

<br><br><br><br>

Now we execute the webscraping.
1. Click on **Sitemap** ***0Generali***
2. Select **Scrape**
<br><br>
![Alt Image Text](./Images/WS_Setup415.png "Setup15")

<br><br><br><br>

You are now asked about the request interval and page load delay. 

- Request interval: Determines the amount of time the scraper waits between sending requests to web pages.
- Page load delay: Specifies the duration the scraper waits for a page to fully load before extracting the data.
<br>
It's done to mimic human browsing behavior, avoid overloading the server, and reduce the chances of getting banned or blocked due to rapid or frequent requests. For the time being, we leave the default settings at 2000 miliseconds.
<br>
Therefore, just click **Start scraping**. If we then see that scraping is not working, we could always increase the time here.
<br><br>

![Alt Image Text](./Images/WS_Setup416.png "Setup16")

<br><br><br><br>

A window now opens and closes itself again after a few seconds. After that click on **refresh**. You will now see the data that has been downloaded. Make sure that they are complete and that each column contains data. Be aware that only the first few lines of the dataset are displayed.
<br><br>
![Alt Image Text](./Images/WS_Setup417.png "Setup17")

<br><br><br><br>

Now go back to **Sitemaps** where you will see the created function for downloading the data from the Generali webpage.
<br><br>
![Alt Image Text](./Images/WS_Setup419.png "Setupxx")

<br><br><br><br>


### Webscraper.io - Cloud
<br><br>
We have now made the setup in the local webscraper.io application. In order for this to run automatically on a daily basis, we need to do the installation in webscraper.io cloud. How to get an cloud account you see [here](0Webscraper.io_Setup.md).
<br><br>
We now copy the settings from the sitemap we made. To do this, click on the sitemap **0Generali** in your Chrome browser.
<br><br>
![Alt Image Text](./Images/WS_Setup419.png "Setupxx")

<br><br><br><br>

Choose now the tab **Sitemap 0Generali** and select **Export Sitemap**.
<br><br>
![Alt Image Text](./Images/WS_Setup421.png "Setupxx")

<br><br><br><br>

Copy now the displayed code.
<br><br>
![Alt Image Text](./Images/WS_Setup422.png "Setupxx")

<br><br><br><br>

Now open your [Cloud account](https://cloud.webscraper.io) and go to **Import Sitemap**.
1. Paste the code you copied in the previous step
2. Name the Sitemap again - in this case ```0Generali```
3. **Import**
<br><br>
![Alt Image Text](./Images/WS_Setup423.png "Setupxx")

<br><br><br><br>

You have now created the sitemap in your cloud environment.
1. Click now on **Scrape** to see if it works correctly.
2. Wait a few seconds for the file to be created - reload the page after a few seconds.
3. Click on **Preview**.
<br><br>
![Alt Image Text](./Images/WS_Setup424.png "Setupxx")

<br><br><br><br>

Now check whether all content has been loaded here. If something is missing - for example, the column with the interest rates - you have to run the setup again locally in your Chrome browser. You can then export the adjusted code again and insert it in your sitemap under **Edit**. 
<br><br>
![Alt Image Text](./Images/WS_Setup425.png "Setupxx")
<br><br>
Please be aware that only the first 10 lines are shown in the *Data Preview*.

<br><br><br><br>

Every time a scrape is executed, this file is created. In order to be able to merge the data from all financial institutions into one file, we need to add the following columns so that we can distinguish the data:

- Name of the financial institution
- Date of download

In addition, we have to edit the data so that they look the same in all sitemaps (e.g. dot everywhere instead of comma for the separation of decimal places, etc.). We do this under **Parser**.
1. Go to **My Sitemaps**
2. Select **0Generali** Sitemap
3. Go to **Parser**. Here you see the existing columns
4. **Add column**
<br><br>
![Alt Image Text](./Images/WS_Setup426.png "Setupxx")

<br><br><br><br>

We now add the a colum with the name of the financial institution. 
1. Name the column ```Financial_Institution```
2. Select as source column **web-scraper-start-url**
3. **Save**
<br><br>
![Alt Image Text](./Images/WS_Setup427.png "Setupxx")

<br><br><br><br>

A new column has now been created. 
1. Go to **Add parser**
2. **Regex match**
<br><br>
![Alt Image Text](./Images/WS_Setup428.png "Setupxx")

<br><br><br><br>

Currently, the input is the URL where we download the data. We would like to get the name of the financial institution from this URL. For this we use a code in Regex. This shortens the URL accordingly.
<br>
1. Use the code ```www\.(.*?)\.ch```
2. Select **Group 1**
3. As *Output* you should now get the name **generali**
4. **Save** 
<br><br>
![Alt Image Text](./Images/WS_Setup429.png "Setupxx")

<br><br><br><br>

Now we add a second column. Click on **Add time scraped**. You see now the added column *time-scraped*. Click now on the field **Convert UNIX timestamp**.
<br><br>
![Alt Image Text](./Images/WS_Setup430.png "Setupxx")

<br><br><br><br>

1. Select your preferred time **Format**.
2. Check the *Output*.
3. **Save**.
<br><br>
![Alt Image Text](./Images/WS_Setup431.png "Setupxx")

<br><br><br><br>

In the list below you will now see the updated list with the two added columns. We will now edit the column **Duration** so that we finally have the same data format for all files. Since **InterestRate** has already the correct format we dont have to change this one.
<br>
1. Now go to the **Duration** column.
2. Click on **Add parser**.
3. Select **Regex match**.
<br><br>
![Alt Image Text](./Images/WS_Setup432.png "Setupxx")

<br><br><br><br>

We now use a code so that only the figure remains - words are excluded.
1. Enter the following code at *Regex* ```(\d+)```
2. Check *Output*
3. **Save**
<br><br>
![Alt Image Text](./Images/WS_Setup433.png "Setupxx")

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

![Alt Image Text](./Images/WS_Setup435.png "Setupxx")

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
![Alt Image Text](./Images/WS_Setup436.png "Setupxx")

<br><br>

We have now made the settings so that the Generali interest rates are automatically extracted on a daily basis. 

<br><br><br><br>

### Google Sheets
<br><br>
Before proceeding further within Google Sheets, please ensure that you have completed the initial setup steps, including creating a Google Sheets account and configuring the Webscraper.io interface to work seamlessly with Google Sheets. To do this, go back to [Webscraper.io_Setup](0Webscraper.io_Setup.md).


