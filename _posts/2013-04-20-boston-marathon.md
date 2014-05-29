---
layout: post
title: High-volume search of 2013 Boston Marathon<br /> runners to rapidly identify community members
---

![](/static/boston-marathon/marathon.png)

> For the full list of Boston Marathon runners produced by the first script, [click here](/static/boston-marathon/runners.txt).

### Background

In the hours following the 2013 Boston Marathon tragedy, a friend from my school paper--the Daily Princetonian-- asked if I could compile a list of any Princeton students who might have run in the race. I admired the paper's effort to confirm the safety of community members: as of Tuesday morning, [all known university affiliates are confirmed safe](http://www.dailyprincetonian.com/2013/04/16/33108/).

The news of the Boston Marathon tragedy shocked me as much as other members of the Princeton University community, and my thoughts go out to the city of Boston and anyone affected by the events. Here, I've documented how to rapidly search for a large number of names in the participants list with hopes that it might help other communities confirm the safety of their members.

### Scraping Marathon Runners

The first task was to compile a complete list of marathon runners from the [Boston Marathon database](http://www.baa.org/individual.html). It seemed that one could list 1000 runners at a time, so scraper.py fetches data across 27 results pages and stores it in a file, runners.txt, including the runner details URL in the final field for looking up age in the final step below

{% highlight python %}
import urllib, sys, codecs
from bs4 import BeautifulSoup
 
START = 1
END = 27
 
for n in range(START,END):
 
    output = ""
    
    sys.stderr.write("Getting URL #" + str(n) + "\n")
    
    url = "http://boston-iframe.r.mikatiming.de/2013/?page="+str(n)+"&event=R&num_results=1000&pid=search&search[club]=%25&search[age_class]=%25&search[sex]=%25&search[nation]=%25&search[state]=%25&search_sort=name"
    
    f = urllib.urlopen(url)
    html = f.read()
    html = html.decode('utf8')
 
    soup = BeautifulSoup(html)
 
    tr_list = soup.find_all("tr")
 
    length = len(tr_list)
 
    for n in range(1, length):
        
        tr = tr_list[n]
        line = list()
        
        for td in tr.find_all('td'):
            line.append(td.get_text().strip())
 
        output += "\t".join(line) + "\t" + tr.find_all("a")[0].get('href') + "\n"
 
    f = codecs.open("runners.txt", "a", "utf-8")
    f.write(output)
{% endhighlight %}

### Matching Students

The second task was to prepare the list of Princeton University undergraduates for easy matching with the Boston Marathon name format ("Last Name, First Name"). This is performed by names.py to produce a file called names.txt.

{% highlight python %}
import os, sys, csv
 
file_path = sys.argv[1]
file  = open(file_path, "rU")
reader = csv.reader(file)
 
header = True
names = []
 
for row in reader:
    
    if header:
        header = False
        continue
 
    name = row[1] + ", " + row[0]
    names.append(name)
 
for name in names:
 
    print name
{% endhighlight %}

Finally, grep.py runs 'grep' regular expression matching to print those lines in runners.txt that contain any name in names.txt.

{% highlight python %}
import os, sys
 
namesFile = open("names.txt","r")
 
for name in namesFile.readlines():
 
    sys.stderr.write(name)
    
    n = name.replace("\n","")
    
    os.system('grep "'+n+'" runners.txt')
{% endhighlight %}

### Consolidation

Because there were several common names in the grep output, one final script called consolidate.py fetches the ages of the matched runners. This proved useful when searching for undergraduates because most students were in the 18-22 age range.

{% highlight python %}
import urllib, sys, codecs
from bs4 import BeautifulSoup
import os, sys
 
matchFile = open("matches.txt","r")
 
count = 0
for line in matchFile.readlines():
    
    print count
    count += 1
    
    lineSplit = line.replace("\n","").split("\t")
    url = "http://boston-iframe.r.mikatiming.de/2013/"+lineSplit[-1]
    
    f = urllib.urlopen(url)
    html = f.read()
    html = html.decode('utf8')
 
    soup = BeautifulSoup(html)
    
    gender = soup.find_all("td", class_="f-age_class")[0].get_text().split(" ")[0].decode('utf8')
    age = soup.find_all("td", class_="f-age")[0].get_text().decode('utf8')
    state = soup.find_all("td", class_="f-state")[0].get_text().decode('utf8')
 
    output = "\t".join(lineSplit[:-1]).decode('utf8') + gender + "\t" + age + "\t" + state + "\n"
    f = codecs.open("consolidated.txt", "a", "utf-8")
    f.write(output)
{% endhighlight %}

### GitHub

You can find the source code for this project on [GitHub](https://github.com/shbhrsaha/boston-marathon).

[ April 2013 ]