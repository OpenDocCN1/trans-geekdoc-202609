After downloading the dataset we can unzip the file using python’s zipfile library:

```
from zipfile import ZipFile
with ZipFile('cat-dataset.zip', 'r') as zip_file:

zip_file.extractall()
```

> *Note: After extracting the dataset you will have duplicate folders. There is one folder cats containing subfolders called CAT_00 to CAT_06. These CAT-folders will also exist within the main directory. You can safely delete those in the main-folder.*

I have moved all the cat image files from the 6 CAT_0x-subfolders into a new parent-folder called cat-dataset:

```
from pathlib import Path
for i in range(7):
paths = Path(f'cat-dataset/CAT_0{i}').iterdir()
for path in paths:
p = Path(path).absolute()
par = p.parents[1]
p.rename(par/p.name)
```

We can use pathlib library to walk the directory.

```
from pathlib import Path
cat_folder = Path(f'cat-dataset')
files = [file for file in cat_folder.iterdir()]
files[:10]
```

[Path('cat-dataset/00000975_025.jpg'),
Path('catdataset/00001208_017.jpg.cat'), Path('cat-dataset/00001144_020.jpg.cat'), Path('cat-dataset/00000388_019.jpg.cat'),
Path('catdataset/00001149_001.jpg.cat'), Path('cat-dataset/00000102_004.jpg'), Path('cat-dataset/00000346_029.jpg.cat'),
Path('catdataset/00000638_006.jpg.cat'), Path('cat-dataset/00001468_016.jpg'), Path('cat-dataset/00000891_025.jpg')]