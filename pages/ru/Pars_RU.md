### Работа с Pars

Данный класс предназначен для работы с запросами и полученной html-страницей.

Класс Pars не принимает никаких данных для конструкторов.

```python
from ipars import Pars

p = Pars()
```

### Коротко о методах Pars:

- Метод **getStaticPage** принимает url страницы, путь по которому сохранится страница, метод записи и заголовки запроса. Метод записи «wb» используется для сохранения картинок, по умолчанию writeMethod установлен как «w», что используется для html-страниц. Если заголовки запросов не указаны, то будут использоваться заголовки со случайным user-agent. Метод возвращает статус ответа сайта, его можно использовать для проверкок.

```python
for index, url in enumerate(urlList):
    if p.getStaticPage(url, f'./page{index}') == 404:
        print('Не удалось получить страницу: ', url)
```

- Метод **getDynamicPage** с помощью библиотеки Selenium получает динамически обновляемую страницу. Это помогает, когда контент на странице подгружается динамически. Принимает url страницы, путь сохранения, closeWindow и timeSleep. По умолчанию браузер Selenium открывается в фоновом режиме, и работу браузера не видно, но если closeWindow указать как False, то будет виден процесс выполнения кода. С помощью timeSleep можно увеличить время загрузки страницы если контент на ней долго подгружается

- Метод **gpsa** (get page semi-automatically) похож на метод getDynamicPage, но работает в полуавтоматическом режиме. Он открывает страницу сайта и ждёт пока не будет нажат Enter в терминале. В этот момент можно зарегистрироваться на сайте и/или перейти на нужную вкладку сайта, после чего нажать Enter и метод спарсит страницу. Подходит для лент соцсетей, где неавторизованным пользователям контент ограничен. Принисает такие же аргументы для таких же целей, что и getDynamicPage, за исключением closeWindow

- Метод **returnBs4Object** возвращает объект beautifulsoup4. Принимает путь до html-страницы, содержимое которой преобразует в объект beautifulsoup, кодировку открытия файла (по умолчанию UTF-8) и тип парсера (по умолчанию lxml).

- Метод **getAttributes** нужена чтобы получить список атрибутов из списка объектов bs4. Принимает список объектов bs4 и название атрибута который будет извлекаться из элементов списка

- Метод **getTexts** нужена чтобы получить список текста из списка объектов bs4. Принимает список объектов bs4 и параметр needFix. Если этот параметр установлен как True, то из текста будут удалены \n, \t и пробелы с концов

- Метод **pprint** используется для вывода значений переменных у которых большая вложеность. Например, если у Вас есть массив объектов, где в качестве значения ключа используется другой массив объектов

- Метод **mkdir** используется для создания папки с именем _nameDir_ если она ещё не существует

- Метод **listdir** используется для получения списка файлов в указанной папке 

- Метод **exists** используется для проверки наличия файла или папки


### Пример использования класса Pars:

```py
# О классе ProgressBarManager читай ниже
from ipars import Pars, ProgressBarManager
p = Pars()
nameFile = 'index.html'
nameFolder = 'img'

def main():
    # Получаем html страницу
    p.getDynamicPage(nameFile, 'https://duckduckgo.com/?q=теплица+социальных+технологий+youtube&iar=videos&atb=v454-1', closeWindow=False, timeSleep=5)

    # Получаем объект BautifullSoup
    soup = p.returnBs4Object(nameFile)

    # Находим все карточки ответов
    # Первые результаты выдачи те что хотелось получить, а остальные нет. Поэтому нам желательно получить первые 84 элемента
    locator = 'b_NgmZrVnRtV8MZMEjLs'
    allCards = soup.find_all(class_=locator)[:84]
    if len(allCards) == 0:
        print(f'''Что-то пошло не так. Вот список возможных проблем:
        1) DuckDuckGo изменил назввание класса для карточек с видео. Сейчас используется локатор: "{locator}"
        2) Сайт не прогрузился. Попробуй увиличить значени параметра timeSleep или выполни запрос позже.''')
        return

    # Получаем все изображения
    allImg = [card.find('img') for card in allCards]

    # Получаем все ссылки
    allSrc = p.getAttributes(allImg, 'src')

    # Создаём папку img если её ещё нет
    p.mkdir(nameFolder)

    # Создаём объект ProgressBarManager
    bar = ProgressBarManager(len(allSrc))

    # Скачиваем картинки
    for index, url in enumerate(allSrc):
        url = 'https:' + url
        p.getStaticPage(f'./{nameFolder}/img{index}.png', url, writeMethod='wb')
        bar.next()
    bar.finish()

    # Смотрим что появилось в папке img
    p.pprint(p.listdir(nameFolder))

if __name__=='__main__':
    main()
```

### Пример использования методов _getAttributes_ и _getTexts_

```py
from ipars import Pars
p = Pars()
nameFile = 'index.html'

p.getStaticPage(nameFile, 'https://google.com')
soup = p.returnBs4Object(nameFile)

allTegA = soup.find_all('a')
textsFromA = p.getTexts(allTegA, needFix=1)
p.pprint(a1)

attributesFromA = p.getAttributes(allTegA, 'href')
p.pprint(a2)
```
