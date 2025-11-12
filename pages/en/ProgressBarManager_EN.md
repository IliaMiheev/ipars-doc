### Working with ProgressBarManager

The class creates a progress bar to display the execution process of code. It accepts five arguments:

- **max**: a mandatory parameter that indicates the maximum number of iterations in the progress bar.

- **message**: a message displayed before the progress bar.

- **color**: the color of the progress bar.

- **fill**: a character used to fill the completed part.

- **width**: the width of the progress bar in characters.

```py
from ipars import ProgressBarManager

bar = ProgressBarManager(100) # Here max is set to 100
```

### Brief Overview of ProgressBarManager Methods

- The **next** method starts the next iteration of the progress bar.

- The **finish** method completes the progress bar.

### Example Usage of ProgressBarManager

```py
# Importing libraries
from ipars import ProgressBarManager
from time import sleep

maxValue = 300
# Creating a default progress bar
bar = ProgressBarManager(maxValue)

# Simulating work
for _ in range(maxValue//2):
    sleep(0.1)
    bar.next()

# Turning off the progress bar
bar.finish()

# Creating a more customized progress bar
bar = ProgressBarManager(
    maxValue,
    message='Downloading process',
    color='red',
    fill='*',
    width=50
)

# Simulating work
for _ in range(maxValue):
    sleep(0.1)
    bar.next()

# Turning off the progress bar
bar.finish()
```
