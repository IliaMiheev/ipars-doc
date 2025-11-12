### Working with CsvManager

This class is intended for writing and retrieving information from CSV files.

The CsvManager class accepts three arguments:

- newline — the newline character (default is an empty string).

- encoding — the encoding of the files being opened (UTF-8).

- delimiter — the delimiter used in the CSV file (;).

```py
from ipars import CsvManager

c = CsvManager(newline="", encoding="UTF-8", delimiter=";")
```

### Brief Overview of CsvManager Methods

- The **writerow** method writes a row to a CSV file. This method accepts the file path, the write mode, and a list of data to be written in the row.

- The **writerows** method accepts the same arguments as writerow, except row must be a double list with data for writing. The difference between these methods is that writerow writes one row, while writerows writes as many rows as there are in the double list.

- The **getRows** method is used to obtain a list of rows from the CSV file. This method accepts the file path from which the rows will be retrieved.

- The **pprint** method is the same as that of Pars.

### Example Usage of CsvManager

```py
from ipars import CsvManager
c = CsvManager()
nameFile = 'data.csv'

# Writing headers
c.writerow(nameFile, 'w', ['Quantity', 'Price', 'Total'])

# Writing data
c.writerows(nameFile, 'a', [
["5", "5", "25"],
["6", "6", "36"],
["7", "7", "49"],
])

# Retrieving rows from the table
rows = c.getRows(nameFile)

# Displaying the rows of the table
c.pprint(rows)
```
