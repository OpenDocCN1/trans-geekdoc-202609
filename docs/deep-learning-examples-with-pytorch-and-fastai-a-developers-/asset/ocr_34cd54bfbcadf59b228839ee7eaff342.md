```
path=Path('style_transfer_predictions')
```

Now we can look into the results-folder where all the transferred cat images are stored.
We can even use notebook-dev again to export these prediction functions to use with our deployment server:

```
#hide
from nbdev.imports import *
from nbdev.export import reset_nbdev_module, notebook2script
```

```
create_config('myLib',
user='we-make-ai',
path='.',
cfg_name='settings.ini')
```

```
cfg = Config(cfg_name='settings.ini') #hide
reset_nbdev_module()
#hide
from nbdev.export import notebook2script
notebook2script('10-Deploy-A-Model-to-a-Server.ipynb')
Converted 10-Deploy-A-Model-to-a-Server.ipynb.
```

# Chapter 13
Building your own Learner from any Model architecture

This chapter shows you how you can use nearly any model architecture and build your own learner on it.

from fastai.vision.all import *
As always we create our dataloaders like this:

```
path = untar_data(URLs.PETS)/"images"
fnames = get_image_files(path)
```