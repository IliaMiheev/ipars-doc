### Работа с ProgressBarManager

Класс создаёт прогресс-бар для для отображения процесса выполнения кода. Принимает пять аргументов:

- **max**: обязательный параметр, который указывает максимальное значение итераций в прогресс-баре

- **message**: сообщение перед прогресс-баром

- **color**: цвет прогресс-бара

- **fill**: заполнитель для выполненой части

- **width**: размер прогресс-бара в символах

```py
from ipars import ProgressBarManager

bar = ProgressBarManager(100) # Здесь max установлен как 100
```

### Коротко о методах ProgressBarManager

- Метод **next** запускает следущую итерацию прогресс-бара

- Метод **finish** завершает работу прогресс-бара

### Пример использования ProgressBarManager

```py
# Импортируем библиотеки
from ipars import ProgressBarManager
from time import sleep

maxValue = 300
# Создаём прогресс-бар по умолчанию
bar = ProgressBarManager(maxValue)

# Имитируем работу
for _ in range(maxValue//2):
    sleep(0.1)
    bar.next()

# Выключаем прогресс-бар
bar.finish()



# Создаём более кастомизированный прогресс-бар
bar = ProgressBarManager(
    maxValue,
    message='Процесс скачивания',
    color='red',
    fill='*',
    width=50
)

# Имитируем работу
for _ in range(maxValue):
    sleep(0.1)
    bar.next()

# Выключаем прогресс-бар
bar.finish()
```
