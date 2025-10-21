### Работа с TimerManager

Класс TimerManager предназначен для отслеживания времени выполнения кода. Он позволяет получить общее время работы в различных форматах.

```py
from ipars import TimerManager

t = TimerManager()
```

### Коротко о методах TimerManager

1. Метод **start** — точка начала отсчёта времени

2. Метод **end** — конечная точка отсчёта времени

3. Метод **getWorkTime** возвращает общее время работы в указанном формате. Поддерживаемые форматы: _seconds_, _minutes_, _hours_. Параметр _ndigits_ указывает количество знаков после запятой для округления, по умолчанию число не округляется.

### Пример использования TimerManager

```py
from time import sleep
from ipars import TimerManager
t = TimerManager()

# Засекаем время
t.start()
sleep(2) # имитация двухсекундной работы
t.end()

# Выводим результат в разных форматах
print(f"Время работы в секундах: {t.getWorkTime()}")                           # 2.0008320808410645
print(f"Время работы в минутах: {t.getWorkTime(ndigits=2, format='minutes')}") # 0.03
print(f"Время работы в часах: {t.getWorkTime(ndigits=4, format='hours')}")     # 0.0006
```
