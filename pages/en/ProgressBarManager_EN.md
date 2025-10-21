### Working with ProgressBarManager

The class creates a progress bar for better visibility of code execution. It takes five arguments:

1. **max**: a required parameter that indicates the maximum number of iterations in the progress bar.

2. **message**: a message displayed before the progress bar.

3. **color**: the color of the progress bar.

4. **fill**: a character used to fill the completed portion.

5. **width**: the size of the progress bar in characters.

```py

from ipars import ProgressBarManager

bar = ProgressBarManager(100) # Here max is set to 100
```

### Brief Overview of ProgressBarManager Methods

1. The **next** method starts the next iteration of the progress bar.

2. The **finish** method completes the progress bar.

### Example of Using ProgressBarManager

```py
# Importing libraries
from ipars import ProgressBarManager
from time import sleep

maxValue = 300

# Creating a default progress bar
bar = ProgressBarManager(maxValue)

# Simulating work
for _ in range(maxValue // 2):
sleep(0.1)
bar.next()

# Turning off the progress bar
bar.finish()

# Creating a more customized progress bar
bar = ProgressBarManager(
maxValue,
message='Downloading process',
color='red',
fill='\*',
width=50
)

# Simulating work

for _ in range(maxValue):
sleep(0.1)
bar.next()

# Turning off the progress bar

bar.finish()
```
