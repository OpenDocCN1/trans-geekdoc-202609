
# CHAPTER 8 Getting started with deep learning with tabular data

Table 8.2 Summary of the pros and cons of the Keras and TabNet solutions (continued)

| Keras | TabNet |
| --- | --- |
| Con | No built-in support for tabular data, which means the model definition needs to be hand-coded. No one-stop summary statement to see the structure of the model |
| | Training process is much slower. The Keras model training notebook took ~20 seconds to run. The Tab-Net-ing training notebook took over 4 minutes. |

In this section we reviewed the Airbnb pricing prediction solution for PyTorch TabNet. In the next section we will reveal our final approach to the Airbnb problem: PyTorch with Lightning Flash.

# 8.4 PyTorch with Lightning Flash

So far, we've considered Keras, fastai, and TabNet PyTorch solutions for the Airbnb price prediction problem. Now let's turn to our final stack: Lightning Flash. As a platform designed for fast prototyping, baslining, and fine-tuning, with a clear API and outstanding documentation, Lightning Flash potentially offers advantages over the stacks we have explored so far.

You can find the code for this solution at https://mng.bz/Vknp. Figure 8.13 shows the fastai and TabNet on PyTorch stacks

| PyTorch Ecosystem | PyTorch Ecosystem |
| --- | --- |
| Low-level framework | PyTorch |
| High-level API | fastai |
| Tabular data library | fastai | TabNet |

Figure 8.13 The fastai and TabNet on PyTorch stacks

# 8.4.1 The key aspects of the Lightning Flash solution

The code for the Lightning Flash solution has many aspects that are different from the solutions we have seen so far. In this section, we go through the model training notebook (https://mng.bz/4aDR) to highlight the most interesting points about this solution.

# PyTorch with Lightning Flash

To work in Colab, the Lightning Flash solution requires a set of installs in a particular order, as shown in 8.14. The source for this list is https://mng.bz/QDP6.

# 8.14 Installs required to get Lightning to work in Colab

```
:pip install torch==1.8.1+cu102 -f https://download.pytorch.org/whl/torch_stable.html
:pip install vision==0.9.0
:pip install effectter
:pip install lightning-flash [image]
:pip install git+https://github.com/PyTorchLightning/lightning-flash.git
:pip uninstall fastai -y
curl https://raw.githubusercontent.com/airc/icevision/44b47c569423ba3f8c6ae5f605fb11leb/icevision/core/7record_components.py --output - /usr/local/lib/python3/dist/packages/icevision/core/record_components.py
```

- Series of pip installs to get the required levels of PyTorch Lightning
- To eliminate potential conflicts between fastai and Lightning Flash, fastai needs to be uninstalled.
- Manually applies a fix for a bug in the current release of icevision
- 8.14 includes all list installs (and one uninstall) to get Lightning Flash to work in Colab. From experience, we know that this very specific list of installs is required or there will be conflicts between the levels of libraries that Lightning Flash requires and the default library levels for Colab.

Next, the libraries required by Lightning Flash need to be imported.

# 8.15 Library imports required by Lightning Flash

```
import torch
import flash
from flash.tabular import TabularClassificationData,
from flash.tabular import TabularClassifier
```

- Imports the torch tensor library
- Imports the flash library
- Imports the objects needed for a tabular classification model

Note that the torch import statement in listing 8.15 is the same as that you saw to import torch in 8.11 for TabNet.
Next, we define the parameters for the dataset that we will use to train the model.

# 8.16 Setting dataset parameters

```
dep_var = 'target'
cat=['neighbourhood_group','neighbourhood','room_type']
cont=['min_minutes','number_of_reviews',
'reviews_per_month','calculated_host_listings_count']
```

- Sets the target field as value that the trained model will predict
- Defines the list of categorical features
- Defines the list of continuous features

# CHAPTER 8 Getting started with deep learning with tabular data

The definitions in listing 8.16 remind you of a similar block of code in the fastai solution (listing 8.3), where we defined the target feature along with lists for categorical and continuous features.

Next we use the values we just defined to define a TabularClassificationData object. This object specifies the minimum characteristics of the dataset that we will use to train the model.

```
Listing 8.17 Defining a TabularClassificationData
```

```
datamodule = TabularClassificationData.from_csv(
categorical_fields=cat,
numerical_fields=cont,
target_fields='target',
train_file='../data/train.csv',
val_file='../data/val.csv',
predict_file='../data/test.csv',
batch_size=64)
```

- Defines the categorical features
- Defines the continuous features
- Defines the target feature
- Defines the training dataset
- Defines the validation dataset
- Defines the test dataset

We should explain why the definition of the TabularClassificationData object shown in listing 8.17 uses separate CSV files for train, validation, and test. For all other solutions, the dataset is loaded from a pickle file that is the output of the data cleanup notebook (https://mgn.bz/XxN9), which is then split into train, validation, and test datasets in the model training notebook. The Lightning solution is different because it has distinct CSV files for each segment of the dataset. The reason for this is that the very specific installation requirements shown in listing 8.14 were incompatible with loading the pickle file that contains the dataframe from the data cleanup notebook. As a workaround, we loaded pickle file in a separate notebook into a pandas DataFrame and saved the separate CSV files for training, validation, and test that you see in the definition of the TabularClassificationData object in listing 8.17. As an exercise, you could update the data cleanup notebook for the Lightning solution so that it saves the cleaned-up dataset as three separate CSV files rather than a single pickle file.

Now that we have specified the details about the dataset, we are ready to define and train the model, as shown in the following listing:

```
Listing 8.18 Setting dataset parameters
```

```
model = TabularClassifier.from_data(datamodule,
learning_rate=0.1)
trainer = flash.Trainer(max_epochs=3,
gpus=torch.cuda.device_count())
trainer.fit(model, datamodule=datamodule)
```

- Defines the model using the TabularClassifierData object defined in listing 8.18
- Defines a Trainer object
- Fits the model

# PyTorch with Lightning Flash

The training code in lightning 8.18 generates the output in figure 8.14.

```
INFO: pytorchlightning.accelerators.cuda:LOCAL_RANK: 0 - CUDA_VISIBLE_DEVICES: []
INFO: pytorchlightning.callbacks.model_summary:
| Name | Type | Params |
|0 train_metrics | ModuleDict | 0 |
1 val_metrics | ModuleDict | 0 |
2 test_metrics | ModuleDict | 0 |
3 adapter | PyTorchtabularAdapter | 12.7 K |

12.7 K Trainable params
0 Non-trainable params
12.7 K Total params
0.051 Total model params size (MB)
Epoch 2:100%
611/611 [00:19:00,31.67it/s,loss=0.481,v_num=3,train_loss=0.456,valid_loss=0.461,valid_accuracy=0.710,train_accuracy=0.698] reached.
```

Figure 8.14 Output of the Lightning training process

![](img/def89cc476fa39f4c54bd34e78d91674_341_0.png)

Note the output includes the validation accuracy and training accuracy for the model. Figure 8.15 shows the deep learning with tabular data stack from the example in this section.
The code for the Lightning solution incorporates some very elegant ideas, as being able to specify the training, validation, and test datasets in the same object that we define the overall characteristics of the dataset. The API for Lightning is easy to understand. Unfortunately, these benefits are undermined because Lightning Flash requires specific requirements to run in Colab. Otherwise, Lightning Flash could have been a favorite, considering the simplicity of fastai with the intuitiveness of Keras.

Figure 8.15 The PyTorch with Lightning Flash stack

# 8.4.2 Comparing the Lightning solution with the Keras solution

We have seen four deep learning solutions to the Airbnb NYC listing price problem: the Keras solution, the fastai solution, the TabNet solution, and finally, the Lightning Flash solution. In this section we'll compare the Keras solution with the Lightning Flash solution and review the pros and cons of each.
We've seen that Lightning Flash has some real advantages for rolling out a fast, simple solution. However, the lack of a beaten path to using Lightning Flash in Colab is
