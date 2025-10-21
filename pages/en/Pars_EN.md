### Working with Pars

This class is designed to work with requests and the resulting html page.

The Pars class does not take any arguments for its constructors.

```python
from ipars import Pars

p = Pars()
```

### Brief Overview of Pars Methods

1. The **getStaticPage** method takes the URL of the page, the path where the page will be saved, the write method, and request headers. The "wb" write method is used for saving images; by default, the write method is set to "w", which is used for HTML pages. If request headers are not specified, random user-agent headers will be used. The method returns the status response from the website, which should be used for conducting checks.
2. The **getDynamicPage** method uses the Selenium library to get a dynamically updated page. This is useful when content on the page loads dynamically. It takes the URL of the page, the save path, closeWindow, and timeSleep. By default, the Selenium browser opens in the background, and its operation is not visible, but if closeWindow is set to False, the code execution process will be shown. The timeSleep parameter can extend the page load time if content takes long to load.
3. The **gpsa** (get page semi-automatically) method is similar to the getDynamicPage method but works in a semi-automatic mode. It opens the webpage and waits until Enter is pressed in the terminal. During this time, you can register on the site and/or switch to the desired tab on the site, after which pressing Enter will allow the method to parse the page. This is suitable for social media feeds where unauthorized users have limited access to content. It accepts the same arguments and serves the same purposes as getDynamicPage, except for closeWindow.
4. The **returnBs4Object** method returns a BeautifulSoup object. It takes the path to the HTML page, converts its contents into a BeautifulSoup object, the file open encoding (default is UTF-8), and the parser type (default is lxml).
5. The **getAttributes** method is used to retrieve a list of attributes from a list of BeautifulSoup objects. It takes a list of BeautifulSoup objects and the name of the attribute to be extracted from the elements of the list.
6. The **getTexts** method is used to retrieve a list of text from a list of BeautifulSoup objects. It takes a list of BeautifulSoup objects and the needFix parameter. If this parameter is set to True, \n, \t, and spaces from the ends will be removed from the text.
7. The **pprint** method is used for displaying variable values that have a high level of nesting. For example, if you have an array of objects, where another array of objects is used as the value of a key.
8. The **mkdir** method is used to create a directory with the name nameDir if it does not already exist.

### Example Parser Using ipars:

```py
# Read about the ProgressBarManager class below
from ipars import Pars, ProgressBarManager
p = Pars()
nameFile = 'index.html'

# Getting the HTML page
p.getDynamicPage(nameFile, 'https://duckduckgo.com/?q=greenhouse+social+technologies+youtube&iar=videos&atb=v454-1', closeWindow=0)

# Getting the BeautifulSoup object
soup = p.returnBs4Object(nameFile)

# Finding all answer cards
# The first results are those we want, while the rest are not. Therefore, we want the first 84 elements
allCards = soup.find*all(class*='b_NgmZrVnRtV8MZMEjLs')[:84]

# Getting all images
allImg = [card.find('img') for card in allCards]

# Getting all links
allSrc = p.getAttributes(allImg, 'src')

# Creating the img folder if it doesn't already exist
nameFolder = 'img'
p.mkdir(nameFolder)

# Creating a ProgressBarManager object
bar = ProgressBarManager(len(allSrc))

# Downloading images
for index, url in enumerate(allSrc):
url = 'https:' + url
p.getStaticPage(f'./{nameFolder}/img{index}.png', url, writeMethod='wb')
bar.next()
bar.finish()
```

### Example Using getAttributes and getTexts Methods

```py
from ipars import Pars
p = Pars()

p.getStaticPage('./index.html', 'https://google.com')
soup = p.returnBs4Object('./index.html')

allTegA = soup.find_all('a')
a1 = p.getTexts(allTegA, needFix=1)
p.pprint(a1)

a2 = p.getAttributes(allTegA, 'href')
p.pprint(a2)
```
