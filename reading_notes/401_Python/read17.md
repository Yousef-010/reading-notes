# Reading 17 webs scraping 
> what is web scraping or web data extraction
- data scraping used for extracting data from websites.
- The web scraping software may directly access the World Wide Web using the Hypertext Transfer Protocol or a web browser
- While web scraping can be done manually by a software user
- the term typically refers to automated processes implemented using a bot or web crawler.
- It is a form of copying in which specific data is gathered and copied from the web
- typically into a central local database or spreadsheet, for later retrieval or analysis.

> Important notes about web scraping:
- Read through the website’s Terms and Conditions to understand how you can legally use the data
  - Most sites prohibit you from using the data for commercial purposes.
- Make sure you are not downloading data at too rapid a rate because this may break the website. You may potentially be blocked from the site as well.


> Inspecting the Website
- The first thing that we need to do is to figure out where we can locate the links to the files we want to download inside the multiple levels of HTML tags 
- Simply put, there is a lot of code on a website page and we want to find the relevant pieces of code that contains our data. 
- **On the website, right click and click on “Inspect”. This allows you to see the raw code behind the site.**

> python code example : 
- We start by importing the following libraries.
```
import requests
import urllib.request
import time
from bs4 import BeautifulSoup

url = 'http://web.mta.info/developers/turnstile.html'
response = requests.get(url)
```
- you will see this response code 
![image](https://miro.medium.com/max/414/1*fyqRGzG8IbhhjxF2Q5MU_Q.png)

- Next we parse the html with BeautifulSoup so that we can work with a nicer, nested BeautifulSoup data structure using this code 
```
soup = BeautifulSoup(response.text, “html.parser”)
```
- example find all a tags 
```
soup.findAll('a')
```
- you will see like this 
![image](https://miro.medium.com/max/582/1*G6YulYb5rczkVvmn7nbQ6g.png)

- extract the actual link that we want like this code 
```
one_a_tag = soup.findAll(‘a’)[38]
link = one_a_tag[‘href’]
```
- you will see this output ‘http://web.mta.info/developers/data/nyct/turnstile/turnstile_180922.txt’
- We can use our urllib.request library to download this file path to our computer.
  - using urllib library
```
download_url = 'http://web.mta.info/developers/'+ link
urllib.request.urlretrieve(download_url,'./'+link[link.find('/turnstile_')+1:])
```

-we can pause our code for a second so that we are not spamming the website with requests. This helps us avoid getting flagged as a spammer.
```
time.sleep(1)
```

- complete example :
```
# Import libraries
import requests
import urllib.request
import time
from bs4 import BeautifulSoup

# Set the URL you want to webscrape from
url = 'http://web.mta.info/developers/turnstile.html'

# Connect to the URL
response = requests.get(url)

# Parse HTML and save to BeautifulSoup object¶
soup = BeautifulSoup(response.text, "html.parser")

# To download the whole data set, let's do a for loop through all a tags
line_count = 1 #variable to track what line you are on
for one_a_tag in soup.findAll('a'):  #'a' tags are for links
    if line_count >= 36: #code for text files starts at line 36
        link = one_a_tag['href']
        download_url = 'http://web.mta.info/developers/'+ link
        urllib.request.urlretrieve(download_url,'./'+link[link.find('/turnstile_')+1:]) 
        time.sleep(1) #pause the code for a sec
    #add 1 for next line
    line_count +=1
```

> Beautiful Soup library 
- Python library designed for quick turnaround projects like screen-scraping. Three features make it powerful:
  - Beautiful Soup provides a few simple methods and Pythonic idioms for navigating, searching,
    - and modifying a parse tree: a toolkit for dissecting a document and extracting what you need. It doesn't take much code to write an application
  - Beautiful Soup automatically converts incoming documents to Unicode and outgoing documents to UTF-8
    - You don't have to think about encodings, unless the document doesn't specify an encoding and Beautiful Soup can't detect one
    - Then you just have to specify the original encoding
  - Beautiful Soup sits on top of popular Python parsers like lxml and html5lib, 
    - allowing you to try out different parsing strategies or trade speed for flexibility.
- Beautiful Soup parses anything you give it  you can 
  - You can tell it "Find all the links", or "Find all the links of class externalLink",
  - or "Find all the links whose urls match "foo.com",
  - or "Find the table heading that's got bold text, then give me that text."


> Resources
- https://towardsdatascience.com/how-to-web-scrape-with-python-in-4-minutes-bc49186a8460
- https://en.wikipedia.org/wiki/Web_scraping
- https://www.scrapehero.com/how-to-prevent-getting-blacklisted-while-scraping/
- https://www.youtube.com/watch?v=Bg9r_yLk7VY&ab_channel=DevEd
- https://www.crummy.com/software/BeautifulSoup/
