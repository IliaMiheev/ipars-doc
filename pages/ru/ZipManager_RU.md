### Работа с ZipManager

Класс ZipManager нужен для архивации папоки файлов. Он принимает принимает только один аргумент — уровень сжатия файлов.

'none' => Без сжатия

'normal' => Обычное сжатие

'hard' => Увеличенное сжатие

'maximum' => Максимальное сжатие

```py
from ipars import ZipManager

z = ZipManager()
```

### Коротко о методах ZipManager

1. Метод **zip_file** используется для архивирования одного файла. Принимает путь до исходного файла и путь выходного файла

2. Метод **zip_folder** используется для архивирования каталога. Принимает путь до исходного каталога и путь выходного файла

### Пример использования ZipManager

```py
from ipars import ZipManager
z = ZipManager(compression='maximum')

z.zip_file('./your_file.txt', 'file_archive_maximum.zip')
z.zip_folder('./your_folder/', 'folder_archive_maximum.zip')
```
