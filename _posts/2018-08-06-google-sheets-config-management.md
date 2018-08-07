---
layout: post
title: Quick config management with Google Sheets
categories:
    - Software
published: true
---

I recently discovered the convenience of managing configuration of hobby-grade software projects with Google Sheets.

My project was an hourly cron job requiring a frequently-edited blacklist of English words. Some options were to:

1. Write the blacklist in-line with the code and push every change
2. Store the blacklist in the cloud provider's environment variables (e.g. [Heroku config vars](https://devcenter.heroku.com/articles/config-vars))

(1) was pretty simple and (2) was the no-brainer for sensitive config variables like API keys. But because the blacklist would be edited frequently and was not sensitive, I turned to a third option: manage the blacklist in a Google Sheet and use the CSV publishing feature to propagate changes to the application.

It was easy to publish a Google Sheet to CSV: File > Publish to the web > Comma-separated values > Publish. Then, the Python application read the CSV with a few lines of code:

```python

import csv
import urllib2

# URL for published Google Sheet
csv_url = "https://docs.google.com/spreadsheets/..."

csv_contents = urllib2.urlopen(csv_url).read()
reader = csv.reader(csv_contents.splitlines(), delimiter=',')
blacklist = [row[0] for row in reader]

```

Because the project was an hourly cron job, refetching config on every code run was acceptable. If the project needed the config for a user HTTP request, it wouldn't have been much work to add a thin caching layer that refetched periodically.

This is all pretty hacky, so I don't recommend doing this for mission-critical applications. But for hobby-grade software projects needing frequent config updates, Google Sheets does the trick.
