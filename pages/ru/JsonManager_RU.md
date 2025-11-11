### Работа с JsonManager

Данный класс предназначен для записи и извлечения информации из json-файлов.

JsonManager принимает принимает только encoding — кодировку в которой будут читаться файлы (по умолчанию UTF-8)

```py
from ipars import JsonManager

j = JsonManager(encoding="UTF-8")
```

### Коротко о методах JsonManager

- Метод **load** используется для получения данных из json-файла по указанному пути

- Метод **dump** используется для записи данных в json-файл. Принимает путь до файла и данные для записи

- Метод **pprint** такой же как и у Pars

### Пример использования JsonManager

```py
from ipars import JsonManager
j = JsonManager()
nameFile = 'data.json'

# Записываем данные
j.dump(nameFile, [1, 2, 3, 4, 5, 6, 7])

# Получаем данные
data = j.load(nameFile)
j.pprint(data) # [1, 2, 3, 4, 5, 6, 7]
```
