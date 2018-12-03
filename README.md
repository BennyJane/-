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

# find error //12.02 1.2.3 可靠的网络链接
# html = urlopen("http://www.pythonscraping.com/pages/page1.html")
#可能出现的两种错误及处理方式


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
#2.4 正则表达式与BeautifulSoup
#网页上几个商品图片，源代码形式 <img src="../img/gifts/img3.jpg">
from urllib.request import urlopen
from bs4 import BeautifulSoup
import re # regular string

html = urlopen("http://WWW.pythonscraping.com/pages/pages3.heml")
bsObj = Beautiful(html)
images = bsObj.findAll("img",{"src":re.compile("\.\.\/img\/gifts\/img.*\.jpg")})
#??
for image in images:
    print(image["src"])
>>> 结果
../img/gifts/img1.jpg
../img/gifts/img2.jpg

#example 
import re
pattern = re.compile('[a-zA-Z]')
result = pattern.findall('as3SiOPdj#@23awe')
print result
>>> ['a', 's', 'S', 'i', 'O', 'P', 'd', 'j', 'a', 'w', 'e']

#2.5 获取属性
#获取一个标签对象的所有属性，返回一个字典对象
myTag.attrs
#获取图片资源位置src
myTag.attrs["src"]

#2.6 Lambda表达式
#获取两个属性的标签
soup.findAll(lambda tag: len(tag.attrs) == 2)

>>>
<div class="body" id="content"></div>
<span style="color:red" class="title"></span>

#2.7 HTML解析库： 
#lxml（可以解析HTML XML文档，大部分源代码是用C语言写的，处理大多数HTML文档速度都非常快）
#HTML parser python自带的解析库
    
    
    
    
    
    


-----end-----
    
