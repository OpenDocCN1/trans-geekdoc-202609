
# 目录

*   [3. Define the generator and discriminator and its optimizer](#ch009_split_001.xhtml#id_3-define-the-generator-and-discriminator-and-its-optimizer)
*   [4. Training model](#ch009_split_001.xhtml#id_4-training-model)
*   [8.5.4 GAN training techniques](#ch009_split_001.xhtml#id_854-gan-training-techniques)
*   [8.6 GAN loss function and its probability explanation](#ch009_split_001.xhtml#id_86-gan-loss-function-and-its-probability-explanation)
    *   [8.6.1 The global optimal solution of the loss function of GAN](#ch009_split_001.xhtml#id_861-the-global-optimal-solution-of-the-loss-function-of-gan)
    *   8.6.2 Kullback–Leibler divergence and Jensen–Shannon divergence
    *   [8.6.3 Maximum Likelihood Interpretation of GAN](#ch009_split_001.xhtml#id_863-maximum-likelihood-interpretation-of-gan)
*   [8.7 Improved loss function: Wasserstein GAN (WGAN)](#ch009_split_001.xhtml#id_87-improved-loss-function-wasserstein-gan-wgan)
    *   [8.7.1 Principle of Wasserstein GAN](#ch009_split_001.xhtml#id_871-principle-of-wasserstein-gan)
    *   [8.7.2 WGAN code implementation](#ch009_split_001.xhtml#id_872-wgan-code-implementation)
*   [8.8 Deep convolutional confrontation network DCGAN](#ch009_split_001.xhtml#id_88-deep-convolutional-confrontation-network-dcgan)
    *   [8.8.1 Transposed convolution of 1D vectors](#ch009_split_001.xhtml#id_881-transposed-convolution-of-1d-vectors)
    *   [8.8.2 2D transposed convolution](#ch009_split_001.xhtml#id_882-2d-transposed-convolution)
    *   [8.8.3 Implementation of convolutional confrontation network DCGAN](#ch009_split_001.xhtml#id_883-implementation-of-convolutional-confrontation-network-dcgan)

# 1.1 Python quick start

Python is an easy-to-learn interpreted scripting language, originally designed to write automated scripts, and later used in web development and scientific computing. In recent years, with the development of data science and artificial intelligence, Python has become the fastest growing and most popular programming language, establishing its dominance in the field of artificial intelligence represented by data processing and machine learning.

## 1.1.1 Python installation

As an interpreted language, each statement of the Python program is interpreted and executed by the `python` interpreter; that is, the Python interpreter interprets and executes the statements of the Python program sentence by sentence.

### Python interpreter installation

On an Ubuntu system, you can enter the following command in a terminal window:

```
sudo apt-get update   
sudo apt-get install python3.8
```

On Mac systems, you can install Python through the package management tool Homebrew:

```
brew install python3
```

Windows platform can download and run the Python3 installer from the official website [`https://www.python.org/downloads`](https://www.python.org/downloads). Check "Add Python3.8 to Path" during the installation process, and the installer will automatically add the path of the Python interpreter to the system path.

Enter the Python interpreter command `python` in the terminal window to open the Python interpreter, and the Python version information will be displayed. If the following information is displayed, the installation is successful.

```
C:\Users\hwdon>python
Python 3.8.2 (tags/v3.8.2:7b3ab59, Feb 25 2020, 23:03:10) [MSC v.1916 64 bit (AMD64)] on win32
Type "help", "copyright", "credits" or "license" for more information.
>>>
```

The reason why Python is popular is a large number of program libraries (packages), such as `numpy` is a multidimensional array (tensor) library, `matplotlib` is a drawing library, and these packages can be installed through the `pip` installation command. For example:

```
python -m pip install -U pip
pip install numpy
python -m pip install -U matplotlib
```

### jupyter notebook programming environment

Now many people use the `jupyter notebook` Python development environment. `jupyter notebook` can use the browser as a programming environment for Python programs. A `jupyter notebook` document is composed of some cells (units), which have different types, mainly Code cell and Markdown Cell. The former is used to write Python code, and the latter is used to write Markdown format (similar to Word) documents in which you can write text, formulas, etc. `Jupyter Notebook` organically combines code and notes in one document. It has become the most used tool for Python programmers to write code and record ideas.

You can enter the following command to install the `jupyter` environment:

```
pip install --upgrade pip
pip install jupyter
```

Then enter `jupyter notebook` on the command line to open a browser window for python programming.

### Anaconda installation tool

Integrated installation tools such as `Anaconda` can automatically install `python` interpreters and common development packages such as `numpy`, `matplotlib`, and `jupyter notebook`. Download and install `Anaconda` on the official website [`https://www.anaconda.com`](https://www.anaconda.com).

> **Note**: If you use `Anaconda` to install Python and its packages, you don't need to install the Python interpreter separately.

The `Anaconda` installer also comes with `spyder`, a Python integrated development environment with a graphical user interface. Of course, readers can also use other Python development environments such as `Pycharm`, etc.

## 1.1.2 Object, `print()` function, type conversion, comment, variable, `input()` function

### 1. Objects

All values in Python (such as the integer `2`) exist in the form of objects, and an object contains information such as value (that is, the content of the object), data type, and `id` (equivalent to an address). Python is a dynamically typed high-level language. The so-called "dynamic type" means that Python can automatically infer the type of an object from its value. The type of a value can be queried with the Python built-in function `type()`. For example:

```
type("http://hwdong-net.github.io")
```

```
str
```

```
type(2)
```

```
int
```

```
type(3.14)
```

```
float
```

```
type(False)
```

```
bool
```

```
id(3)
```

```
140705546753760
```

```
id(3.14)
```

```
1857260776048
```

> **Note**: The Boolean type `bool` has only 2 values `True` and `False`, which are used to represent the truth or falsehood of logical propositions.

### 2. Print function `print()`

You can output a series of objects separated by commas `,`, such as:

```
print(2, 3.14)
print("youtube channel：hwdong", True)
```

```
2 3.14
youtube channel: hwdong True
```

The `print()` function has a keyword parameter `end`, which indicates the default end character after outputting information. Its default value is `\n`, which means a newline after the output. The following code passes a space string `" "` to the `end` parameter; then the space will be output instead of a newline after the print output. For example:

```
print(1, 2, 3, end=" ")  # After outputting 3 objects, output a space instead of a newline
print(4, 5, 6)
```

```
1 2 3 4 5 6
```

### 3. Type conversion

For primitive types, the type name can be used to convert an object of another type to an object of that type. For example:

```
print(int(3.14))                 # convert 3.14 from float type to int integer type
print(type(int(3.14)))           # output the type of int(3.14)
print(type("3.14"))
print(float("3.14"))
print(type(float("3.14")))       # convert "3.14" from str string type to float floating point type
```

```
3
<class 'int'>
<class 'str'>
3.14
<class 'float'>
```

### 4. Comment

The line of text at the beginning of `#` is called a **comment**, and the comment is not a program statement, but a description of the program code.

### 5. Variables

You can use the operator `=` to give an object a name, which is called the **variable name** of the object. Or that the variable refers to an object.

```
pi = 3.14
print(pi)
print(2 * pi)
```
