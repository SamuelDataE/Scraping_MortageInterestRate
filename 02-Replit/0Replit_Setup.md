# Setup

<br><br>

This document demonstrates how to set up Replit and Cronjob.de. In the subsequent documents, it is explained how the code needs to be extended to add the financial institutions from where we fetch the interest rates data. It is shown how to download the interest rates from the following websites:

<br><br>

- [Luzerner Kantonalbank](1Replit_LuzernerKantonalbank.md)
- [Credit Suisse](1Replit_CreditSuisse.md)
- [Generali Insurance](1Replit_Generali.md)

<br><br>
Follow this guide to get started.

<br><br><br><br>

### 1. Setup Replit
<br><br>
Open an account with Replit - you can do this under the following [link](https://replit.com/login). Enter your details - the login process should be self-explanatory. 
<br><br>
![Alt Image Text](./Images/RP_Setup1.png "Setup1")

<br><br><br><br>

After you have registered, you will see this screen. To start the project you have to create your first Repl (short for "Read-Eval-Print Loop"). Click on **Create Repl**.
<br><br>
![Alt Image Text](./Images/RP_Setup2.png "Setup2")


<br><br><br><br>

A new window opens. 
1. Select Python as a template
2. Name your Repl ```WebScraping_MortgageInterestRates```
3. Decide if you want to have a private or public Repl<br>
   Difference:<br>
   For a public Repl, other users can see your code, but they cannot directly modify it. However, they can create their own copy (Fork) of the Repl and make changes to that copy without affecting your original code.
   With a private Repl, no one except you (or those you explicitly grant access to) can see or modify the code. For a private Repl, you must have a paid user subscription.
4. **Create Repl**
<br><br>
![Alt Image Text](./Images/RP_Setup3.png "Setup3")

<br><br><br><br>

Once you have created your Repl, the following screen appears in which you manage your Repl. There are four different sections:
 - Files
 - Tools
 - Script (main.py)
 - Console
<br><br>
![Alt Image Text](./Images/RP_Setup4.png "Setup4")

<br><br><br><br>

Within Python, we use two predefined programs, which we can incorporate into our code. To install these, go to **Tools** and click on **Packages**.

Install the following packages:

- beautfulsoup4
- Flask
- requests
- pandas
- replit 
<br><br>
In order to install the packages, you must first search for them in the search field - then you can install them.
<br><br>
![Alt Image Text](./Images/RP_Setup999.png "Setup5")

<br><br><br><br>

In our Python script **main.py** we will now enter various codes to do the setup. We start with the following code:

```
import requests
from bs4 import BeautifulSoup

url = 'https://www.lukb.ch/de/private/finanzieren/hypotheken/festhypothek'
response = requests.get(url)

soup = BeautifulSoup(response.content, 'html.parser')

# Extracting the terms
terms = [th.text.strip() for th in soup.find_all('th')]

# Extracting the interest rates
interest_rates = [td.find('p').text.strip() if td.find('p') else td.text.strip() for td in soup.find_all('td')]

# Combining both lists into a dictionary
data = dict(zip(terms, interest_rates))

# Displaying the data
for term, interest_rate in data.items():
    print(f"Term: {term}, Interest Rate: {interest_rate}")
```
<br><br>
If there is a **#** at the beginning of a line, then it is a comment. A comment is never executed and serves only for your information what the code stands for.
<br><br>
Enter this in the script. We want to test whether we can download the data from the Luzerner Kantonalbank. 
1. Copy the text into the script
2. Execute the script
3. You should now see the data in the console
4. *Now delete the code in **main.py** again - we have done this step for testing purposes
<br><br>
![Alt Image Text](./Images/RP_Setup5.png "SetupXXX")
<br><br>
If this does not work, check again if you have installed all relevant packages. If it still doesn't work, something has probably changed on the Luzerner Kantonalbank homepage. In this case, continue with the next steps nevertheless.

<br><br><br><br>

In order to be able to download the interest rates of several financial institutions, we write the specifications of the website in a separate list. The code in **main.py** therefore always remains the same - regardless of the number of websites from which we extract the data. This makes the setup easier.

On the left side next to **Files** there is a **+** sign. Click on this sign and create a new file with the name ```financialinstitutions.json```. It is important that you use exactly this name, because our code will look for this file afterwards.

Now enter the following code in this file:

```
[
    {
        "name": "LUKB",
        "url": "https://www.lukb.ch/de/private/finanzieren/hypotheken/festhypothek",
        "selectors": {
            "2 Jahre": "th:-soup-contains('2 Jahre') + td p",
            "3 Jahre": "th:-soup-contains('3 Jahre') + td p",
            "4 Jahre": "th:-soup-contains('4 Jahre') + td p",
            "5 Jahre": "th:-soup-contains('5 Jahre') + td p",
            "6 Jahre": "th:-soup-contains('6 Jahre') + td p",
            "7 Jahre": "th:-soup-contains('7 Jahre') + td p",
            "8 Jahre": "th:-soup-contains('8 Jahre') + td p",
            "9 Jahre": "th:-soup-contains('9 Jahre') + td p",
            "10 Jahre": "th:-soup-contains('10 Jahre') + td p"
        }
    },
    {
        "name": "MigrosBank",
        "url": "https://www.migrosbank.ch/de/privatpersonen/hypotheken/festhypothek",
        "selectors": {
            "2 Jahre": "td:-soup-contains('2 Jahre') + td + td",
            "3 Jahre": "td:-soup-contains('3 Jahre') + td + td",
            "4 Jahre": "td:-soup-contains('4 Jahre') + td + td",
            "5 Jahre": "td:-soup-contains('5 Jahre') + td + td",
            "6 Jahre": "td:-soup-contains('6 Jahre') + td + td",
            "7 Jahre": "td:-soup-contains('7 Jahre') + td + td",
            "8 Jahre": "td:-soup-contains('8 Jahre') + td + td",
            "9 Jahre": "td:-soup-contains('9 Jahre') + td + td",
            "10 Jahre": "td:-soup-contains('10 Jahre') + td + td"
        }
    }
  ]
```
<br><br>
![Alt Image Text](./Images/RP_Setup6.png "SetupXXX")
<br><br>
We again use the Luzerner Kantonalbank and MigrosBank as examples. 

***How you can set up these banks or extend the code to other banks is shown in the other documents in this repository.*** 

<br><br><br><br>

We now enter a code in **main.py** to extract the data. Now copy the following code and paste it into Replit.

```
# Testing - Extracting the data manually 

import requests
from bs4 import BeautifulSoup
import json

# Read the configuration file
with open('financialinstitutions.json', 'r') as f:
    banks = json.load(f)

all_data = {}

for bank in banks:
    response = requests.get(bank['url'])
    soup = BeautifulSoup(response.text, 'html.parser')

    bank_data = {}
    for duration, selector in bank['selectors'].items():
        rate_element = soup.select_one(selector)
        if rate_element:
            bank_data[duration] = rate_element.text.strip()

    all_data[bank['name']] = bank_data

# Display or save data
print(all_data)
```
<br><br>
When you have inserted the code, execute it with **Run**.
<br><br>
![Alt Image Text](./Images/RP_Setup7.png "SetupXXX")
<br><br>
You should now see a data record for LUKB and MigrosBank in the console. 

<br><br><br><br>

The manual download of the data is the first part of the code, which we have in our script. However, we will now add other tasks to the script. In order to execute only one task at a time, however, we need to inactivate the rest of the code. This can be done by excluding the code with the characters ```'''```. As soon as the characters appear orange, these lines are no longer executed. Set the code inactive by placing ```'''``` before and after the code. 
<br><br>
![Alt Image Text](./Images/RP_Setup8.png "SetupXXX")

<br><br><br><br>

We have now downloaded the data with the previous code - but now we have done it manually. However, in order to be able to download the data automatically on a daily basis, we need to extend the code. 
<br><br>
Now copy this code and add it to the main.py file at the top (do not delete the inactive code):
<br><br>
```
import requests
from bs4 import BeautifulSoup
import json
from datetime import datetime
from replit import db
from flask import Flask

app = Flask(__name__)

# Read the configuration file
with open('financialinstitutions.json', 'r') as f:
    banks = json.load(f)

@app.route('/')
def home():
    return "Welcome to the Mortgage Interest Rates Scraper! Use /trigger_scrape to initiate the scraping process."

@app.route('/trigger_scrape')
def trigger_scrape():
    all_data = []
    current_date = datetime.now().strftime('%d.%m.%Y')

    for bank in banks:
        response = requests.get(bank['url'])
        soup = BeautifulSoup(response.text, 'html.parser')

        for duration, selector in bank['selectors'].items():
            rate_element = soup.select_one(selector)
            if rate_element:
                rate = rate_element.text.strip()

                # Restructure data into the desired format for the database
                record = {
                    "Name": bank['name'],
                    "Duration": duration,
                    "InterestRate": rate,
                    "time-of-scraping": current_date
                }
                all_data.append(record)

    # Store data in the Replit database
    for record in all_data:
        # Use a combination of Name, Duration, and time-of-scraping as the key
        key = f"{record['Name']}_{record['Duration']}_{record['time-of-scraping']}"
        db[key] = record

    return "Data has been saved in the Replit database!"

@app.route('/cronjob_78641.html')
def cronjob_verification():
    return "cronjob.de"

if __name__ == "__main__":
    app.run(host='0.0.0.0', port=3000)
```
<br><br>
This code includes the following items:

1. Import all functions and packages which are required. With the *Flask* package we will be able to trigger the code via web.
2. Downloads the data from the websited we have defined in the **financialinstitutions.json** file.
3. Restructure data into the desired format for the database - including the date of the extraction.
4. Safes the data in the database.

When you have entered the code in **main.py** execute the script and click **Run** (before you execute the code make sure that only this code is activated).
<br><br>
![Alt Image Text](./Images/RP_Setup9.png "SetupXXX")
<br><br>
A webview will now open on the right-hand side. You will now see a link with your project und user name. Copy this link and write it into your code in the script (line 3 in the image below). Add ```Https://``` to the front of the code and add ```/trigger_scrape``` to the back. In this example the code is *https://WebScrapingMortgageInterestRates.samuelhaller.repl.co/trigger_scrape*.
<br><br>
This is the code with which you execute the script. Whenever you enter this code in a webbrowser, your python code gets triggered. We will execute this in a later step.

<br><br><br><br>

In order for this code to be called via external web, the script must always be running. In other words, the cloud server must be online so that the script can download the data from Alpha Vantage at all time. To ensure that the script is always running and does not automatically go offline after some time, we must activate **Always On**. To do this, click on the blue Python symbol at the top right. In order to activate this, you must either buy "My Cicles" or make a paid subscription. It is recommended to make a **Hacker** subscription. With this subscription you also get more storage space in your database and the *Always On* functionality is included in this package. You can find the prices [here](https://replit.com/pricing).
<br><br>
If you have bought the "My Cicles" or made the subscription, activate the **Always On** function.
<br><br>
![Alt Image Text](./Images/RP_Setup50.png "Setup50")

<br><br><br><br>

Execute now your code again and click on **Run**. The code will now be activated till you *stop* it.
<br><br>
![Alt Image Text](./Images/RP_Setup10.png "SetupXXX")

<br><br><br><br>

Now open a new tab of the web browser and enter the link we defined in the previous steps. In this example the link is called: *https://WebScrapingMortgageInterestRates.samuelhaller.repl.co/trigger_scrape*
<br><br>
![Alt Image Text](./Images/RP_Setup11.png "SetupXXX")
<br><br>
When the link is loaded, the web page should display the following: *Data has been saved in the Replit database!*

<br><br><br><br>

In summary, the following can be said:
<br><br>
Code: **https://WebScrapingMortgageInterestRates.samuelhaller.repl.co/**    (acc. Replit webview)
  * Checks if the script runs.
  * *Can be triggered when script is executed in Replit (**Run**) or the link is entered on the web.*
  * Gives as response *Welcome to the Mortgage Interest Rates Scraper! Use /trigger_scrape to initiate the scraping process.*
<br><br>  
Code: **https://WebScrapingMortgageInterestRates.samuelhaller.repl.co/trigger_scrape**
  * Is executing the script and downloads the stock data.
  * *Can only be executed via web.*
  * Gives as response *Data has been saved in the Replit database!*

<br><br><br><br>

Since we have now executed the code and entered *https://WebScrapingMortgageInterestRates.samuelhaller.repl.co/trigger_scrape* on the web, the data has been downloaded. Go back to your repl - we are now checking if anything has been saved in the database.
<br><br>
1. Click on **Database** under **Tools** at the bottom left.
2. A tab **Database** opens on the right-hand side next to Console - there you will see that there are **keys** in the database. This is the number of data records contained in the database.
<br><br>  
![Alt Image Text](./Images/RP_Setup12.png "SetupXXX")
<br><br>
In this case we see that 18 data records have been saved.

<br><br><br><br>

Now stop the code and make the code inactive by placing the characters ```'''``` around the code. We do this to be able to complete the code further. 
<br><br>  
![Alt Image Text](./Images/RP_Setup13.png "SetupXXX")

<br><br><br><br>

To retrieve the data from the database, you can add the following code to our **main.py** file. Enter the code at the end. 
<br><br>
```
# Retrieve the database

from replit import db
from datetime import datetime

# Retrieve all values from the database
all_data = [db[key] for key in db.keys()]

# Sort the data
sorted_data = sorted(all_data, key=lambda x: (x['Name'], datetime.strptime(x['time-of-scraping'], '%d.%m.%Y'), x['Duration']))

# Display the sorted data in the desired format
print("Name, Duration, InterestRate, time-of-scraping")

# Set to track already displayed records
displayed_records = set()

for record in sorted_data:
    # Extract only numeric characters from "Duration"
    duration = ''.join(filter(str.isdigit, record['Duration']))
    
    # Convert "InterestRate" to the desired format
    try:
        # Replace comma with dot and convert to a floating-point number
        interest_rate = float(record['InterestRate'].replace(',', '.').replace('%', ''))
        # Format to the desired format
        interest_rate_str = f"{interest_rate:.3f}"
    except ValueError:
        interest_rate_str = record['InterestRate']

    # Create a unique identifier for each record
    unique_id = f"{record['Name']}{duration}{interest_rate_str}{record['time-of-scraping']}"

    # Check if the record has already been displayed
    if unique_id not in displayed_records:
        print(f"{record['Name']}, {duration}, {interest_rate_str}, {record['time-of-scraping']}")
        displayed_records.add(unique_id)
```
<br><br>  
This code retrieves the data from the database and structures it into a table format with the following columns:
- Name
- Duraiton (term)
- InterestRate
- time of scraping
<br><br>  
In addition, all duplicates are deleted in advance.
<br><br>  
![Alt Image Text](./Images/RP_Setup14.png "SetupXXX")
<br><br> 
In this example we now see the 18 data sets. 
<br><br> 
Now set this code to inactive as well by using the ```'''``` characters.

<br><br><br><br>

The next code is for loading the data from the database into a csv file. This can then simply be downloaded. Copy the following code.
<br><br> 
```
# Create csv

import requests
from bs4 import BeautifulSoup
import json
from datetime import datetime
from replit import db
import csv

# Retrieve all values from the database
all_data = [db[key] for key in db.keys()]

# Sort the data
sorted_data = sorted(all_data, key=lambda x: (x['Name'], datetime.strptime(x['time-of-scraping'], '%d.%m.%Y'), x['Duration']))

# Open CSV file for writing
with open('output.csv', 'w', newline='', encoding='utf-8') as csvfile:
    csvwriter = csv.writer(csvfile)
    
    # Write the header row
    csvwriter.writerow(["Name", "Duration", "InterestRate", "time-of-scraping"])

    # Set to track already written records
    written_records = set()

    for record in sorted_data:
        # Extract only numeric characters from "Duration"
        duration = ''.join(filter(str.isdigit, record['Duration']))
        
        # Convert "InterestRate" to the desired format
        try:
            # Replace comma with dot and convert to a floating-point number
            interest_rate = float(record['InterestRate'].replace(',', '.').replace('%', ''))
            # Format to the desired format
            interest_rate_str = f"{interest_rate:.3f}"
        except ValueError:
            interest_rate_str = record['InterestRate']

        # Create a unique identifier for each record
        unique_id = f"{record['Name']}{duration}{interest_rate_str}{record['time-of-scraping']}"

        # Check if the record has already been written
        if unique_id not in written_records:
            csvwriter.writerow([record['Name'], duration, interest_rate_str, record['time-of-scraping']])
            written_records.add(unique_id)

print("Data has been written to the output.csv file!")
```
Enter the code at the end of your existing script **main.py** and press **Run**.
<br><br>
![Alt Image Text](./Images/RP_Setup15.png "SetupXXX")
<br><br>
Now make the code inactive again by placing the characters ``'''``'' around the code.

<br><br><br><br>

On the left side under **Files** the file **output.csv** has now been created. If you click on it, you will see the data contained in this csv. You can now download this csv for your further use.
<br><br>
![Alt Image Text](./Images/RP_Setup16.png "SetupXXX")
<br><br>
When the data is loaded into a csv, the current data in the database is always downloaded. When the database expands, the csv file is not automatically expanded. In this case you have to delete it manually (*right click on the file and **delete***) - then you can generate a new csv file with the new data by executing the respecitve code.

<br><br><br><br>

On the left side under **Files** the file **output.csv** has now been created. If you click on it, you will see the data contained in this csv. You can now download this csv for your further use.
<br><br>
![Alt Image Text](./Images/RP_Setup16.png "SetupXXX")








