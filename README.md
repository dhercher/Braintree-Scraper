# Braintree-Scraper

## This is used to scrape data from Braintree's website
  - You can scrape settlement and disbursement data
  - Because of lag time while loading there is a download queue that still needs to be fully built out
  - I still need to add dispute data load
  - check braintree website for other possible features
  - check to make sure all types (ie. credit cards, options) are chosen


```python
# Dates For Searching
date_max = datetime.now()
date_min = datetime.now() - timedelta(7)

## Create Object and Login
# bt = Braintree(USERNAME, PASSWORD)

# Create Object then Login -- Same as above
bt = Braintree()
bt.login(USERNAME, PASSWORD)

# Load Disbursement Data -- this can take awhile to load on braintree
bt.load_disbursement_report(date_min, date_max, wait_time=100)
bt.disbursement_data # Might have the data you want or its in the download_queue

# Load Settlement Data For Yesterday
bt.load_settlement_batch_report(date_min, wait_time=30)
bt.settlement_data # Might have the data you want or its in the download_queue
```
