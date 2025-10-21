### Working with JsonManager

This class is designed to write and extract information from json files.

JsonManager takes only one argument — the encoding in which the files will be read. The default is UTF-8.

```py
from ipars import JsonManager

j = JsonManager()
```

### Brief Overview of JsonManager Methods

1. The **load** method is used to retrieve data from a JSON file at the specified path.

2. The **dump** method is used to write data to a JSON file. It takes the path to the file and the data to be written.

3. The **pprint** method is the same as that of Pars.

### Example of Using JsonManager

```py

from ipars import JsonManager
j = JsonManager()

# Writing data
j.dump('./data.json', [1, 2, 3, 4, 5, 6, 7])

# Retrieving data
data = j.load('./data.json')
j.pprint(data) # [1, 2, 3, 4, 5, 6, 7]
```
