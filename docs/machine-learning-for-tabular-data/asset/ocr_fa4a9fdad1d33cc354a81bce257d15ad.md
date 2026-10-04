# PyTorch with Lightning Flash

To work in Colab, the Lightning Flash solution requires a set of installs in a particular order, as shown in 8.14. The source for this list is https://mng.bz/QDP6.

# 8.14 Installs required to get Lightning to work in Colab

```
:pip install torch==1.8.1+cu102 -f https://download.pytorch.org/whl/torch_stable.html
:pip install vision==0.9.0
:pip install effetter
:pip install lightning-flash [image]
:pip install git+https://github.com/PyTorchLightning/lightning-flash.git
:pip uninstall fastai -y
curl https://raw.githubusercontent.com/airc/icevision/44b47c569423ba3f8c6ae5f605fb11leb/icevision/core/7record_components.py --output - /usr/local/lib/python3/dist/packages/icevision/core/record_components.py
```

Series of pip installs to get the required levels of PyTorch Lightning

To eliminate potential conflicts between fastai and Lightning Flash, fastai needs to be uninstalled.

Manually applies a fix for a bug in the current release of icevision

8.14 includes all list installs (and one uninstall) to get Lightning Flash to work in Colab. From experience, we know that this very specific list of installs is required or there will be conflicts between the levels of libraries that Lightning Flash requires and the default library levels for Colab.
Next, the libraries required by Lightning Flash need to be imported.

# 8.15 Library imports required by Lightning Flash

```
import torch
import flash
from flash.tabular import TabularClassificationData,
from flash.tabular import TabularClassifier
```

Imports the torch tensor library

Imports the flash library

Imports the objects needed for a tabular classification model

Note that the torch import statement in listing 8.15 is the same as that you saw to import torch in 8.11 for TabNet.
Next, we define the parameters for the dataset that we will use to train the model.

# 8.16 Setting dataset parameters

```
dep_var = 'target'
cat=['neighbourhood_group','neighbourhood','room_type']
cont=['min_minutes','number_of_reviews',
'reviews_per_month','calculated_host_listings_count']
```

Sets the target field as value that the trained model will predict

Defines the list of categorical features

Defines the list of continuous features