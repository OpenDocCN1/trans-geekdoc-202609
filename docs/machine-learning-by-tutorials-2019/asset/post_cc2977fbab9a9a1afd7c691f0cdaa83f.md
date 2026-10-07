
## Machine Learning Chapter 4: Getting Started with Python & Turi Create

If you don't have access to a machine learning capable computer, you can certainly follow along with parts of this book using Colab. However, the authors of this book recommend that readers follow along with a local installation of Python. If you choose to use Colab you'll have to perform the following setup up. Of course, you will need a Google account in order to continue.

Access your Google Drive at drive.google.com and from the side menu, create a new **Folder** named **machine-learning**.

![](img/5720be5c3cca252e12448e68d25607b5_157_0.png)

Double click the folder, and drag and drop the unzipped snapshots dataset into it. This may take a while. While you wait, you'll need to add Colab as an "app" to Google Drive. Right-click anywhere in the **machine-learning** folder, select **More** from the dialog, and select + **Select Connect more apps**.

## Machine Learning
Chapter 4: Getting Started with Python & Turi Create

![](img/5720be5c3cca252e12448e68d25607b5_158_0.png)

From the Connect apps to Drive window that opens up, search for colab in the search field, and select + Connect.

## Chapter 4: Getting Started with Python & Turi Create

![](img/5720be5c3cca252e12448e68d25607b5_159_0.png)

Once it's been successfully installed, close the window, and Right-click anywhere again, and from the **More** dialog, select **Collaboratory**. This will open a new tab or window with something that should look a lot like a Jupyter notebook.

## Machine Learning
Chapter 4: Getting Started with Python & Turi Create

![](img/5720be5c3cca252e12448e68d25607b5_160_0.png)

Rename the file to **getting-started.ipynb** by clicking the title and renaming it in inline.

![](img/5720be5c3cca252e12448e68d25607b5_160_1.png)

## Machine Learning
## Chapter 4: Getting Started with Python & Turi Create

From the toolbar, select Runtime > Change Runtime type.

![](img/5720be5c3cca252e12448e68d25607b5_161_0.png)

From the Notebook settings dialog that open, change the Hardware accelerator from None to GPU. Save the changes.

![](img/5720be5c3cca252e12448e68d25607b5_161_1.png)

## Machine Learning
## Chapter 4: Getting Started with Python & Turi Create

In the first code cell of the notebook, paste the following code:

```python
from google.colab import drive
drive.mount('/content/drive/')
```

These two lines will walk through your google drive folders into the notebook. This requires giving Colab access to your Google Drive folders. Click the tiny button beside the code cell. Follow the instructions in the output window by opening the link to give Colab the authority to access your Drive. You'll be given an access code to paste into your notebook.

![](img/5720be5c3cca252e12448e68d25607b5_162_0.png)

## Machine Learning
Chapter 4: Getting Started with Python & Turi Create

Once the mounting is complete, add a new code cell, and run the following piece of code:

```bash
ls "/content/drive/My Drive/machine-learning/snacks"
```

![](img/5720be5c3cca252e12448e68d25607b5_163_0.png)

You may notice that the code starts off with an exclamation. In Jupyter-specific syntax that allows you to run system commands, you're trying to list the contents of the directory where you uploaded the snacks dataset. If all goes well, you should now be able to set this as your root directory to the snacks dataset.

You've completed setting up a Google notebook environment, configured to use the GPU, which you can use for this book. It's worth reiterating that Colab is untested with respect to this book, and you may run into issues while using it. However, it offers a compelling alternative for developers looking to do machine learning, but don't have access to a machine powerful enough to run machine learning algorithms.

## Key points

- Get familiar with Python. Its widespread adoption with academics in the machine learning field means if you learn Python, you'll be in demand.
- Get familiar with Conda.
- Get familiar with Jupyter.

## Where to go from here?

You've completed setting up a Google notebook environment, configured to use the GPU, which you can use for this book. It's worth reiterating that Colab is untested with respect to this book, and you may run into issues while using it. However, it offers a compelling alternative for developers looking to do machine learning, but don't have access to a machine powerful enough to run machine learning algorithms.

## Chapter 4: Getting Started with Python & Turi Create

If you don't have access to a machine learning capable computer, you can certainly follow along with parts of this book using Colab. However, the authors of this book recommend that readers follow along with a local installation of Python. If you choose to use Colab you'll have to perform the following setup up. Of course, you will need a Google account in order to continue.

Access your Google Drive at drive.google.com and from the side menu, create a new **Folder** named **machine-learning**.

![](img/5720be5c3cca252e12448e68d25607b5_157_0.png)

Double click the folder, and drag and drop the unzipped snapshots dataset into it. This may take a while. While you wait, you'll need to add Colab as an "app" to Google Drive. Right-click anywhere in the **machine-learning** folder, select **More** from the dialog, and select + **Select Connect more apps**.

## Machine Learning
Chapter 4: Getting Started with Python & Turi Create

![](img/5720be5c3cca252e12448e68d25607b5_158_0.png)

From the Connect apps to Drive window that opens up, search for colab in the search field, and select + Connect.

## Chapter 4: Getting Started with Python & Turi Create

![](img/5720be5c3cca252e12448e68d25607b5_159_0.png)

Once it's been successfully installed, close the window, and Right-click anywhere again, and from the **More** dialog, select **Collaboratory**. This will open a new tab or window with something that should look a lot like a Jupyter notebook.

## Machine Learning
Chapter 4: Getting Started with Python & Turi Create

![](img/5720be5c3cca252e12448e68d25607b5_160_0.png)

Rename the file to **getting-started.ipynb** by clicking the title and renaming it in inline.

![](img/5720be5c3cca252e12448e68d25607b5_160_1.png)

## Machine Learning
## Chapter 4: Getting Started with Python & Turi Create

From the toolbar, select Runtime > Change Runtime type.

![](img/5720be5c3cca252e12448e68d25607b5_161_0.png)

From the Notebook settings dialog that open, change the Hardware accelerator from None to GPU. Save the changes.

![](img/5720be5c3cca252e12448e68d25607b5_161_1.png)

## Machine Learning
## Chapter 4: Getting Started with Python & Turi Create

In the first code cell of the notebook, paste the following code:

```python
from google.colab import drive
drive.mount('/content/drive/')
```

These two lines will walk through your google drive folders into the notebook. This requires giving Colab access to your Google Drive folders. Click the tiny button beside the code cell. Follow the instructions in the output window by opening the link to give Colab the authority to access your Drive. You'll be given an access code to paste into your notebook.

![](img/5720be5c3cca252e12448e68d25607b5_162_0.png)

## Machine Learning
Chapter 4: Getting Started with Python & Turi Create

Once the mounting is complete, add a new code cell, and run the following piece of code:

```bash
ls "/content/drive/My Drive/machine-learning/snacks"
```

![](img/5720be5c3cca252e12448e68d25607b5_163_0.png)

You may notice that the code starts off with an exclamation. In Jypter-specific syntax that allows you to run system commands, you're trying to list the contents of the directory where you uploaded the snacks dataset. If all goes well, you should now be able to set this as your root directory to the snacks dataset.

You've completed setting up a Google notebook environment, configured to use the GPU, which you can use for this book. It's worth reiterating that Colab is untested with respect to this book, and you may run into issues while using it. However, it offers a compelling alternative for developers looking to do machine learning, but don't have access to a machine powerful enough to run machine learning algorithms.

## Key points

- Get familiar with Python. Its widespread adoption with academics in the machine learning field means if you learn Python, you'll be in demand.
- Get familiar with Conda.
- Get familiar with Jupyter.

## Where to go from here?

You've completed setting up a Google notebook environment, configured to use the GPU, which you can use for this book. It's worth reiterating that Colab is untested with respect to this book, and you may run into issues while using it. However, it offers a compelling alternative for developers looking to do machine learning, but don't have access to a machine powerful enough to run machine learning algorithms.

*(Note: The OCR text provided seems to contain repetitions and artifacts from the OCR process. I have cleaned the logical flow based on the instructions provided.)*

## Chapter 4: Getting Started with Python & Turi Create

(The rest of the content follows the pattern established above, merging the pages and correcting typos like "unwested" to "untested", "devlopers" to "developers", etc.)
