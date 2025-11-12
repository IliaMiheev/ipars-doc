### Working with ZipManager

The ZipManager class is used for archiving folders of files. It accepts only one argument — one of the possible compression levels:

- none — no compression.

- normal — standard compression.

- hard — increased compression.

- maximum — maximum compression.

```py
from ipars import ZipManager

z = ZipManager()
```

### Brief Overview of ZipManager Methods

- The **zip_file** method is used for archiving a single file. It accepts the path to the source file and the path to the output file.

- The **zip_folder** method is used for archiving a directory. It accepts the path to the source directory and the path to the output file.

### Example Usage of ZipManager

```py
from ipars import ZipManager
z = ZipManager(compression='maximum')

z.zip_file('./your_file.txt', 'file_archive_maximum.zip')
z.zip_folder('./your_folder/', 'folder_archive_maximum.zip')
```
