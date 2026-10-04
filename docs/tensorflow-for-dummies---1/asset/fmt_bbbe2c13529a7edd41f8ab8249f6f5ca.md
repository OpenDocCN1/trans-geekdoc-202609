
Keras’s simplicity stems from its small API and intuitive set of functions. These functions focus on accomplishing standard tasks in machine learning, which makes Keras ideal for newcomers to the field but of limited value for those who want to customize their operations.

François Chollet released Keras under the MIT License, and Google has incorporated his interface into TensorFlow. For this reason, many TensorFlow developers prefer to code their neural networks using Keras.

### TensorFlow

As the title implies, this book centers on TensorFlow, Google’s gift to the world of machine learning. The Google Brain team released TensorFlow 1.0 in 2015, and as of the time of this writing, the current version is 1.4. It’s provided under the Apache 2.0 open source license, which means you’re free to use it, modify it, and distribute your modifications.

TensorFlow’s primary interface is Python, but like Caffe, its core functionality is written in C++ for improved performance. Like Theano, TensorFlow stores operations in a graph that can be deployed to a GPU, a remote system, or a network of remote systems. In addition, TensorFlow provides a utility called TensorBoard, which makes visualizing graphs and their operations possible.

Like other frameworks, TensorFlow supports execution on CPUs and GPUs. In addition, TensorFlow applications can be executed on the Google Cloud Platform (`GCP`). The `GCP` provides world-class processing power at relatively low cost, and in my opinion, `GCP` processing is TensorFlow’s most important advantage. [Chapter 13](#19_9788126592555-ch13.xhtml) discusses this important topic in detail.

# Getting Your Feet Wet

IN THIS CHAPTER

![check](images/check.png)**Obtaining and installing TensorFlow**

![check](images/check.png)**Exploring the TensorFlow package**

![check](images/check.png)**Running a simple application**

![check](images/check.png)**Understanding style conventions**

Many chapters of this book present complex technical subjects and lengthy mathematical formulas. But not this one. This chapter is dead simple, and its goal is to walk you through the process of installing TensorFlow and running your first TensorFlow application.

A complete TensorFlow installation contains a vast number of files and directories. This chapter explores the installation and explains what the many files and folders are intended to accomplish. The discussion touches on many of TensorFlow’s packages and the modules they contribute.

Once you’ve installed the TensorFlow toolset, it’s easy to start coding and running applications. The end of the chapter presents a basic application that provides a cheery welcome to TensorFlow development.

## Installing TensorFlow

Google provides two methods for installing TensorFlow, and the simpler option involves installing precompiled packages. This discussion presents a three-step process for installing these packages:

1.  **Install Python on your development system.**
2.  **Install the pip package manager.**
3.  **Use pip to install TensorFlow.**

The second installation method involves compiling TensorFlow from its source code. This option takes time and effort, but you can obtain better performance because your TensorFlow package will take the fullest advantage of your processor’s capabilities. [Chapter 12](#18_9788126592555-ch12.xhtml) explains how to obtain and compile TensorFlow’s source code.

### Python and pip/pip3

TensorFlow supports development with Java and C++, but this book focuses on Python. I use Python 3 in the example code, but you’re welcome to use Python 2. As I explain in the upcoming section “[Setting the Style](#06_9788126592555-ch02.xhtml#c02-sec-0012),” TensorFlow applications should be accessible to both versions.

Python’s official package manager is *pip,* which is a recursive acronym that stands for “pip installs Python.” To install packages like TensorFlow, you can use `pip` on Python 2 systems or `pip3` on Python 3 systems. Package management commands have the following format:

`pip <command-name> <command-options>`

`pip` and `pip3` accept similar commands and perform similar operations. For example, executing `pip list` or `pip3 list` prints all the Python packages installed on your system. [Table 2-1](#06_9788126592555-ch02.xhtml#c02-tbl-0001) lists this and five other commands.

[TABLE 2-1](#06_9788126592555-ch02.xhtml#rc02-tbl-0001) Package Management Commands

| **Command Name** || **Description** |

| --- | --- |

| `install` || Installs a specified package |

| --- | --- |

| `uninstall` || Uninstalls a specified package |

| `download` || Downloads a package, but doesn't install it |

| `list` || Lists installed packages |

| `show` || Prints information about a specified package |

| `search` || Searches for a package whose name or summary contains the given text |

For this discussion, the most important command to know is `pip install` and `pip3 install`. But keep in mind that `pip`/`pip3` can perform many other operations.

![tip](images/tip.png)If you execute a TensorFlow application using a precompiled package, you may receive messages like “The TensorFlow library wasn't compiled to use *XYZ* instructions, but these are available on your machine and could speed up CPU computations.” To turn off these messages, create an environment variable named `TF_CPP_MIN_LOG_LEVEL` and set its value to 3.

### Installing on Mac OS

Many versions of Mac OS have Python already installed, but I recommend obtaining and installing a new Python package. If you visit [`www.python.org/downloads`](http://www.python.org/downloads), you see one button for Python 2 and another for Python 3. If you click one of these buttons, your browser downloads a PKG file that serves as the Python installer.

When you launch the installer, the Python installation dialog box appears. To install the package, follow these five steps:

1.  **In the Introduction page, click the button labeled Continue.**
2.  **In the Read Me page, click the button labeled Continue.**
3.  **In the License page, click the button labeled Continue and then click Agree to accept the software license agreement.**
4.  **In the Installation Type page, click Install to begin the installation process, entering your password, if necessary.**
5.  **When the installation is complete, click Close to close the dialog box.**

If the installation completes successfully, you can run `pip` or `pip3` on a command line. You can install TensorFlow with the following command:

`pip install tensorflow`

This command tells the package manager to download TensorFlow, TensorBoard, and a series of dependencies. One dependency is `six`, which supports compatibility between Python 2 and 3. If the installation fails due to a preinstalled `six` package, you can fix the issue by executing the following command:

`pip install --ignore-installed six`

This command tells `pip` to install `six` on top of the existing installation. After this installation completes, you should be able to run `pip install tensorflow` without error. On my system, the installer stores the TensorFlow files in the `/Library/Frameworks/Python.framework/Versions/<ver>/lib/python<ver>/site-packages/tensorflow` directory.

### Installing on Linux

Many popular distributions of Linux are based on Debian, including Ubuntu and Linux Mint. These distributions rely on the Advanced Package Tool (`APT`) to manage packages, which you can access on the command line by entering `apt-get`. This discussion explains how to install TensorFlow on these and similar operating systems.

Most Linux distributions already have Python installed, but it's a good idea to install the full development version and `pip`/`pip3`. The following command installs both for Python 2:

`sudo apt-get install python-pip python-dev`

Alternatively, the following command performs the installation for Python 3:

`sudo apt-get install python3-pip python3-dev`
