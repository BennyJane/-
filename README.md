# - BeautifulSoup

from urllib.request import urlopen
from bs4 import BeautifulSoup
html = urlopen("http://www.pythonscraping.com/pages/page1.html")
bsObj = BeautifulSoup(html.read())
print(bsObj.h1)

>>> <h1>An Interesting Title</h1>
html --- <html><head>...</head><body>...</body></html>
  head----<head><title>A Useful Page</title></head>
      title---<title>A Useful Page</title>
  body---<body><h1>An Int...</h1><div>Lorem ip..</div></body>
       h1---<h1>An Interesting Title</h1>
       div---<div>Lorenm Lpsum dolor...</div>
  
  bsObj.h1
  bsObj.html.body.h1
  bsObj.body.h1
  bsObj.html.h1

# find error //12.02
from urllib.request import urlopen
from urllib.error import HTTPError, URLError
from bs4 import BeautifulSoup
def getTitle(url):
    try:
        html = urlopen(url)
    except (HTTPError, URLError) as e:
        return None
    try:
        bsObj = BeautifulSoup(html.read())
        title = bsObj.body.h1
    except AttributeError as e:
        return None
    return title

title = getTitle("http://www.pythonscraping.com/pages/page1.html1")
if title == None:
    print("Title could not be fouund")
else:
    print(title)

# Gordian Kont 

    
    
    
    
    
    
    


-----end-----
    
