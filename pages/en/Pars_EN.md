### Working with Pars

This class is designed for handling requests and the obtained HTML page.

The Pars class does not accept any data for its constructor.

```py
from ipars import Pars

p = Pars()
```

### Brief Overview of Pars Methods:

- The **getStaticPage** method takes a URL of the page, the path where the page will be saved, the write method, and request headers. The write method "wb" is used for saving images; by default, the write method is set to "w", which is used for HTML pages. If the request headers are not specified, random user-agent headers will be used. The method returns the response status of the website, which can be used for checks.

```py
for index, url in enumerate(urlList):
    if p.getStaticPage(url, f'./page{index}') == 404:
        print('Failed to obtain the page: ', url)
```

- The **getDynamicPage** method uses the Selenium library to obtain dynamically updating pages. This helps when the content on the page loads dynamically. It takes the URL of the page, the saving path, closeWindow, and timeSleep. By default, the Selenium browser opens in the background, and the browser activity is not visible, but if closeWindow is set to False, the code execution process will be visible. The timeSleep parameter can be used to increase the loading time if the content takes a while to load.

- The **gpsa** (get page semi-automatically) method is similar to the getDynamicPage method but operates in a semi-automatic mode. It opens the site page and waits for the Enter key to be pressed in the terminal. During this time, you can register on the site and/or switch to the desired tab, after which pressing Enter will allow the method to parse the page. It accepts the same arguments for the same purposes as getDynamicPage, except for closeWindow.

- The **returnBs4Object** method returns a BeautifulSoup4 object. It takes the path to the HTML page, converts its content into a BeautifulSoup object, the file encoding (default is UTF-8), and the parser type (default is lxml).

- The **getAttributes** method is used to obtain a list of attributes from a list of bs4 objects. It takes a list of bs4 objects and the name of the attribute to be extracted from the list elements.

- The **getTexts** method is used to obtain a list of text from a list of bs4 objects. It takes a list of bs4 objects and the needFix parameter. If this parameter is set to True, \n, \t, and spaces from the ends will be removed from the text.

- The **pprint** method is used to output the values of variables with significant nesting. For example, if you have an array of objects where the value of the key is another array of objects.

- The **mkdir** method is used to create a folder with the name _nameDir_ if it does not already exist.

### Example Parser Using ipars:

```py
# About the ProgressBarManager class, read below
from ipars import Pars, ProgressBarManager
p = Pars()
nameFile = 'index.html'

# Getting the HTML page
p.getDynamicPage(nameFile, 'https://duckduckgo.com/?q=теплица+социальных+технологий+youtube&iar=videos&atb=v454-1', closeWindow=0)

# Getting the BeautifulSoup Object
soup = p.returnBs4Object(nameFile)

# Finding all answer cards
# The first results are what we wanted, and the rest are not. Therefore, we prefer to get the first 84 elements
allCards = soup.find*all(class*='b_NgmZrVnRtV8MZMEjLs')[:84]

# Getting all images
allImg = [card.find('img') for card in allCards]

# Getting all links
allSrc = p.getAttributes(allImg, 'src')

# Creating a folder img if it does not already exist
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

### Example Usage of _getAttributes_ and _getTexts_ Methods

```py
from ipars import Pars
p = Pars()
nameFile = 'index.html'

# download the page and get the object bs4 based on it
p.getStaticPage(nameFile, 'https://google.com')
soup = p.returnBs4Object(nameFile)

# Getting the text
allTegA = soup.find_all('a')
textsFromA = p.getTexts(allTegA, needFix=1)
p.pprint(a1)

# Getting the attribute href
attributesFromA = p.getAttributes(allTegA, 'href')
p.pprint(a2)
```
