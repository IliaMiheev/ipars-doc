### Работа с ProgressBarManager

Класс создаёт прогресс-бар для лучшей видимости выполнения кода. Принимает пять аргументов:

1. **max**: обязательный параметр, который указывает максимальное значение итераций в прогресс-баре

2. **message**: сообщение перед прогресс-баром

3. **color**: цвет прогресс-бара

4. **fill**: заполнитель для сделанной части

5. **width**: размер прогресс-бара в символах

```py
from ipars import ProgressBarManager

bar = ProgressBarManager(100) # Здесь max установлен как 100
```

### Коротко о методах ProgressBarManager

1. Метод **next** запускает следущую итерацию прогресс-бара

2. Метод **finish** завершает работу прогресс-бара

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
