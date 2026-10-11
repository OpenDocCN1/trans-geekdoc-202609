
![Figure 1.5. The digital valley (color) of the loss function and the trace (black) of the loss function during model training.](images/bk978-0-7503-6244-3ch1f5_online.jpg)

**Figure 1.5.** The digital valley (color) of the loss function and the trace (black) of the loss function during model training.

### 1.4 Dataset, dataloader, GPU and models saving

Data for model training in computer vision projects should be packed into datasets. Usually, sizes of datasets are huge. Many datasets are already packed into datasets by many selfless dataset creators. After downloading a dataset, we need to slice each dataset into a dataloader with many batches, because our computer memory is not big enough to handle all data of a dataset in a single batch. Just like eating a big cake, we have to cut it with a knife into small pieces so that each piece can fit into our mouths. We will learn how to pack the data in the temperature csv file into a dataset and slice it into a dataloader in project [1.4.1](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1ueqn22). They are all extra jobs for the simple project, but are essential steps for big datasets in computer vision projects.

![](images/bk978-0-7503-6244-3ch1uf16_pr.gif)

More Python and PyTorch libraries are imported in Cell 01 as tools for us to pack our data into a dataset and slice the dataset into a dataloader. How is data packed inside a dataset? Or what is the dataset structure? Codes in Cell 02 of project [1.4.1](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1ueqn22) are used as an example to show you how to pack data into a dataset. With a subclass `Dataset` imported from `torch.utils.data` in PyTorch, a class named `C2F` is defined. The `__init__` function in the `C2F` class uses the `np.loadtxt` function to input date from the csv file with a string as its file name. The option `np.float32` is important because we need it to convert the data into float32 tensors. Then each of the two columns and the length of each column are recorded. The second function in the `C2F` class named `__getitem__` can be used to pick out a single pair of data in the dataset at a specific index. With the last function `__len__` in the class `C2F`, we can find how many data pairs are in the dataset. In Cell 03, the csv file with a name string `d:/C2F.csv` is used for an instance of the `C2F` class. You can see the class `C2F` does its jobs just as we want. In `my_dataset[0]` of Cell 03, if you change the `0` to `:`, you will print out all nine elements in the array x and all nine elements of the array y.

![](images/bk978-0-7503-6244-3ch1uf17_pr.gif)

It is easy to use a subclass `DataLoader` from `torch.utils.data` in PyTorch to slice a dataset into many small batches. With an option `shuffle = False` in Cell 04, the data sequence would not be changed. To an image dataloader for model training in the future, we need this option to be True to reduce overfitting. A for-loop in Cell 04 prints out the first batch of the dataloader. Of course, if you remove the `break`, you will print out all three batches.

![](images/bk978-0-7503-6244-3ch1uf18_pr.gif)

In sections [1.2](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1s1-2) and [1.3](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1s1-3), we defined a linear regression model as `X`@`w`, or `nn.Linear(1,1)`. In Cell 05 of this project, we write extra codes to define the simple model. Usually, computer vision projects use many neural layers in their neural network models. The `nn.Sequential()` in Cell 05 can contain many kinds of mathematical operations to process and extract information from data. This is the way to define all computer vision models in big projects of this book. The function `forward` in the class accepts input data and returns output data. In the last line of Cell 05, a model was defined as an instance of the `LinearRegression` class, and the model was moved to the memory of a graphics processing unit (GPU) by `cuda()`. CUDA's ability of parallel computing can significantly reduce model training time. In Cell 06, a loss function (criterion), model optimizer and learning rate scheduler are defined. A learning rate scheduler `OneCycleLR` is used here. This scheduler changes learning rate along all iterations of all epochs. Since there are three batches in each epoch, the 20 000 epochs have 60 000 iterations for the model training.

![](images/bk978-0-7503-6244-3ch1uf19_pr.gif)

In Cell 07, each batch of data x and y coming from the dataloader is sent to GPU by `cuda()`, because the model is in GPU. Model parameters k and b are printed out by codes on the last two lines in Cell 07. With the codes in Cell 08, the model training results are shown in three graphs (figure [1.6](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1fig6)). For the y\_hat calculations on line 06 of Cell 08, Data X in the dataset must be sent to GPU. Using matplotlib to plot y\_hat in figure [1.6](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1fig6)(A), we have to send y\_hat back to CPU. It is no surprise that the running time for this project with GPU is much longer than the running time of project [1.2.1](#Chapter_1.xhtml#bk978-0-7503-6244-3ch1ueqn10). Many extra codes added to the project take extra time. For huge datasets, it is guaranteed that GPU saves model training time significantly.

![](images/bk978-0-7503-6244-3ch1uf20_pr.gif)

![Figure 1.6. Model training output graphs. (A): original data Y and predicted data y\_hat. (B): loss curve, (C): learning rate curve with OneCycleLR learning rate scheduler.](images/bk978-0-7503-6244-3ch1f6_online.jpg)

**Figure 1.6.** Model training output graphs. (A): original data Y and predicted data y\_hat. (B): loss curve, (C): learning rate curve with OneCycleLR learning rate scheduler.

Training models with a huge amount of data takes hours, days or even weeks. After your computer is turned off, all those good parameters of your trained models disappear. It is painful to take a long time to train the model again. We need to save parameters of trained models so that we can use them for later applications. To save a trained model, you need a file name, for example: `File_name = 'd:/model4LR.pth'`, and then use the code `torch.save(model, File_name)`. The trained linear regression model defined in Cell 05 would be saved by codes in Cell 09.

![](images/bk978-0-7503-6244-3ch1uf21_pr.gif)

To avoid confusion, I use `saved_model` as the name of the model loaded from the saved file in Cell 10. Before using the loaded model, we have to set the saved model for evaluation by the code `saved_model.eval()` after the model is loaded. With the last line in Cell 10, the trained model's parameters are printed out. You can see that the two parameters are right, and the saved model is in GPU. Using codes in Cell 11, you will find that the loaded model works. There are more methods to save trained models. The second method is only saving the model parameters to a file. Just by reloading those parameters in the file to the model, we can reuse the trained model. You can try the second method by running Cell 12–14.

![](images/bk978-0-7503-6244-3ch1uf22_pr.gif)

The third method is to save a check-point of a trained model during training. Big computer vision projects need many days for model training. We have to restart model training from a check-point saved on a previous day. In Cell 15, you can see that the model's parameters, the optimizer's parameters, the loss function, and learning rate scheduler are all saved in a file. You can reload those parameters by running codes in Cell 16.

![](images/bk978-0-7503-6244-3ch1uf23_pr.gif)

### 1.5 Activation functions for nonlinear regressions
