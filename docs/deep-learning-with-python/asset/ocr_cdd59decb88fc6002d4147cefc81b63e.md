I recommend using Jupyter notebooks to get started with Keras, although that isn’t a requirement: you can also run standalone Python scripts or run code from within an IDE such as PyCharm. All the code examples in this book are available as open source notebooks; you can download them from GitHub at github.com/fchollet/deep-learning-with-python-notebooks.

# 3.4.2 Using Colaboratory

Collaboratory (or Colab for short) is a free Jupyter notebook service that requires no installation and runs entirely in the cloud. Effectively, it’s a web page that lets you write and execute Keras scripts right away. It gives you access to a free (but limited) GPU runtime and even a TPU runtime, so you don’t have to buy your own GPU. Colaboratory is what we recommend for running the code examples in this book.

# FIRST STEPS WITH COLABORATORY

To get started with Colab, go to https://colab.research.google.com and click the New Notebook button. You’ll see the standard Notebook interface shown in figure 3.2.

![](bbox=[0.19, 0.4, 0.87, 0.62])

Figure 3.2 A Colab notebook

You’ll notice two buttons in the toolbar: + Code and + Text. They’re for creating executable Python code cells and annotation text cells, respectively. After entering code in a code cell, Pressing Shift-Enter will execute it (see figure 3.3).

In a text cell, you can use Markdown syntax (see figure 3.4). Pressing Shift-Enter on a text cell will render it.

Text cells are useful for giving a readable structure to your notebooks: use them to annotate your code with section titles and long explanation paragraphs or to embed figures. Notebooks are meant to be a multimedia experience!