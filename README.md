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
