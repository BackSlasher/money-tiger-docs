# Collecting Transactions

Without transactions, the site is uselss.  
Collecting transactions is the main funcionality of the site.  
Due to the complex beaurocracy of acquiring transactions directly from the banks / CC companies, I instead rely on scraping externally.

## TL;DR

1. Get an import token (https://www.money-tiger.tech/accounts/settings/import-keys)
2. Follow the instructions in [money-tiger-scraper](https://github.com/BackSlasher/money-tiger-scraper).

## Explained
Scraping is done with [israeli-bank-scrapers](https://github.com/eshaham/israeli-bank-scrapers/), which is a NodeJS code.  
I wrap it in a Docker image, which is then executed either in GitHub action or whenever you want to run it.

The Docker itself is described in [money-tiger-scraper-docker](https://github.com/BackSlasher/money-tiger-scraper-docker).
The process is:

1. Take a JSON file that describes the different accounts
2. Iterate over each account and fetch all possible transactions
3. Submit the results to the Money Tiger API

You can view all of the submitted collection runs via [import runs](https://www.money-tiger.tech/txns/runs)
