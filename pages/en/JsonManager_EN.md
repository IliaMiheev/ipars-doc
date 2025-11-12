### Working with JsonManager

This class is intended for writing and retrieving information from JSON files.

JsonManager accepts only one parameter: encoding — the encoding in which the files will be read (default is UTF-8).

```py
from ipars import JsonManager

j = JsonManager(encoding="UTF-8")
```

### Brief Overview of JsonManager Methods

- The **load** method is used to obtain data from a JSON file at the specified path.

- The **dump** method is used to write data to a JSON file. It accepts the file path and the data to write.

- The **pprint** method is the same as that of Pars.

### Example Usage of JsonManager

```py
from ipars import JsonManager
j = JsonManager()
nameFile = 'data.json'

# Writing data
j.dump(nameFile, [1, 2, 3, 4, 5, 6, 7])

# Retrieving data
data = j.load(nameFile)
j.pprint(data) # [1, 2, 3, 4, 5, 6, 7]
```
