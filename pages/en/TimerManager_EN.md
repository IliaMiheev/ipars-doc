### Working with TimerManager

The TimerManager class is designed to track the execution time of code. It allows you to obtain the total runtime in various formats.

```py
from ipars import TimerManager

t = TimerManager()
```

### Brief Overview of TimerManager Methods

1. The **start** method marks the starting point of the time measurement.

2. The **end** method marks the endpoint of the time measurement.

3. The **getWorkTime** method returns the total execution time in the specified format. Supported formats are seconds, minutes, and hours. The ndigits parameter specifies the number of decimal places for rounding; by default, the number is not rounded.

### Example of Using TimerManager

```py
from time import sleep
from ipars import TimerManager
t = TimerManager()

# Starting the timer
t.start()
sleep(2) # simulating two seconds of work
t.end()

# Displaying results in different formats
print(f"Execution time in seconds: {t.getWorkTime()}") # 2.0008320808410645
print(f"Execution time in minutes: {t.getWorkTime(ndigits=2, format='minutes')}") # 0.03
print(f"Execution time in hours: {t.getWorkTime(ndigits=4, format='hours')}") # 0.0006
```
