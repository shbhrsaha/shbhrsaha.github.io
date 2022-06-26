---
layout: post
title: CSVFiddle for querying CSVs with SQL
---

When working with CSV files, I often want to query them with SQL. There are a [lot](https://jupyter.org/) [of](https://shell.duckdb.org/) [tools](https://simonwillison.net/2021/Jun/19/sqlite-utils-memory/) that make it technically possible to do this, but they fall short on user experience in a couple ways.

What I want is an experience resembling the [BigQuery SQL Editor](https://www.google.com/search?q=bigquery+sql+editor&tbm=isch), but optimized for quick import of CSV data. I want to generate links to share my queries with anyone on the Internet.

So, I built a quick hack called [CSVFiddle](http://csvfiddle.io/):

![](/static/csvfiddle/demo.gif)

The name is inspired by JSFiddle, a popular tool to write HTML/CSS/Javascript snippets in a sandbox environment. CSVFiddle is like JSFiddle for CSV/SQL.

You can import data, write SQL, then instantly share it with anyone. Everything runs 100% in-browser, so the data you import and the queries you write are never sent to a web server.

Building CSVFiddle was a good opportunity to use technologies like NextJS and DuckDB, both of which have been a phenomenal experience to work with. In its current state, I wouldn't describe CSVFiddle as a "robust" tool; reliably parsing CSVs alone would require more configuration options.

Still, I'm putting this out there in case it's useful to someone. If you're using CSVFiddle for anything, I'd [love to hear from you](https://twitter.com/shubroski).