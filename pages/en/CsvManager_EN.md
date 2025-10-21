### Working with CsvManager

This class is designed to write and extract information from csv files

The CsvManager class takes three arguments: the newline character newline (default is an empty string), the encoding of the opened files encoding (default is UTF-8), and the delimiter used in the CSV file delimiter (default is ";").

```py

from ipars import CsvManager

c = CsvManager()
```

### Brief Overview of CsvManager Methods

1. The **writerow** method writes a row to the CSV file. The method takes the path to the CSV file, the write mode, and a list of data that will be written to the file's row.

2. The **writerows** method takes the same arguments as writerow, but the row must be a double list with data for writing. The difference between these methods is that writerow writes one row, while writerows writes as many as there are in the double list.

3. The **getRows** method is used to retrieve a list of rows in the CSV file. The method takes the path to the file from which the rows will be obtained.

4. The **pprint** method is the same as that of Pars.

### Example of Using CsvManager

```py
from ipars import CsvManager
c = CsvManager()

# writing headers
writer = c.writerow('./data.csv', 'w', ['Quantity', 'Price', 'Total'])

# writing data
writer = c.writerows('./data.csv', 'a', [
["5", "5", "25"],
["6", "6", "36"],
["7", "7", "49"],
])

# retrieving rows from the table
rows = c.getRows('./data.csv')

# printing table rows
c.pprint(rows)
```
