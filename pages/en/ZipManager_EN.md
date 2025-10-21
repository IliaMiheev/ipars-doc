### Working with ZipManager

The ZipManager class is used for archiving a folder of files. It takes only one argument — the compression level for the files.

'none' => No compression

'normal' => Normal compression

'hard' => Increased compression

'maximum' => Maximum compression

```py
from ipars import ZipManager

z = ZipManager()
```

### Brief Overview of ZipManager Methods

1. The **zip_file** method is used to archive a single file. It takes the path to the source file and the path to the output file.
2. The **zip_folder** method is used to archive a directory. It takes the path to the source directory and the path to the output file.

### Example of Using ZipManager

```py

from ipars import ZipManager
z = ZipManager(compression='maximum')

z.zip_file('./your_file.txt', 'file_archive_maximum.zip')
z.zip_folder('./your_folder/', 'folder_archive_maximum.zip')
```
