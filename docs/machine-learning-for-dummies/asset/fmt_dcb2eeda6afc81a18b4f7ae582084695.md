
![Warning](images/warning.png)The installation works best if you first remove previous versions of Anaconda from your system. Otherwise, one version of the product can interfere with other versions of the product. Anaconda provides a separate uninstall program in the Anaconda executable folder on your system, the location of which can vary. For example, to uninstall a previous version of Anaconda 3 on a Windows system, look in the `C:\Users\<UserName>\Anaconda3` folder on your system for `Uninstall-Anaconda3.exe`. Execute this file to uninstall the product. In addition, this book doesn't support the use of the Miniconda installer described at [`https://docs.conda.io/en/latest/miniconda.html`](https://docs.conda.io/en/latest/miniconda.html).

The default download version installs Python 3.8, which is the version used in this book. Both Windows and Mac OS X provide graphical installers. When using Linux, you rely on the `bash` utility.

### Defining why Anaconda is used in this book

Anaconda isn't an Integrated Development Environment (IDE) like many other products out there. Rather, it’s a centralized method of accessing a number of packages. This book uses Jupyter Notebook as an IDE because it supports literate programming techniques. However, you could just as easily use Spyder for development, and you might be happier with it because it provides a more traditional interface. You can see a comparison at [`https://www.slant.co/versus/1246/15716/~spyder_vs_jupyter`](https://www.slant.co/versus/1246/15716/~spyder_vs_jupyter). The point is that Anaconda helps you manage both IDEs, along with a wealth of other packages. In addition, you can create environments for using the IDEs in specific ways. For example, you could have an environment for using Jupyter Notebook for Python and an entirely different environment for using Jupyter Notebook for R.

So, it’s important to know why this section emphasizes Jupyter Notebook when Anaconda provides access to a number of IDEs. Most IDEs look like fancy text editors, and that’s precisely what they are. Yes, you get all sorts of intelligent features, hints, tips, code coloring, and so on, but at the end of the day, they’re all text editors. Nothing is wrong with text editors, and this chapter isn’t telling you anything of the sort. However, given that Python developers often focus on scientific applications that require something better than pure text presentation, using notebooks instead can be helpful.

![Remember](images/remember.png)A `notebook` differs from a text editor in that it focuses on a technique called `literate programming`, advanced by Stanford computer scientist Donald Knuth. You use literate programming to create a kind of presentation of code, notes, math equations, and graphics. In short, you wind up with a scientist’s notebook full of everything needed to understand the code completely. You commonly see literate programming techniques used in high-priced packages such as Mathematica and MATLAB. Notebook development excels at

*   Demonstration

*   Collaboration

*   Research

*   Teaching objectives

*   Presentation

This book uses the Anaconda tool collection because it provides you with a great Python coding experience but also helps you discover the enormous potential of literate programming techniques. If you spend a lot of time performing scientific tasks, Anaconda and products like it are essential. In addition, Anaconda is free, so you get the benefits of the literate programming style without the cost of other packages.

![Tip](images/tip.png)For more information about Anaconda and changes from previous editions, make sure to view the Release Notes at [`https://docs.anaconda.com/anaconda/reference/release-notes/`](https://docs.anaconda.com/anaconda/reference/release-notes/). Most of the changes you find deal with bug fixes and updates.

## Installing Anaconda on Linux

You use the command line to install Anaconda on Linux — there is no graphical installation option. The following procedure should work fine on any Linux system, whether you use the Intel or PowerPC version of Anaconda:

1.  **Open a copy of Terminal.**

    The Terminal window appears.

2.  **Change directories to the downloaded copy of Anaconda on your system.**

    The name of this file varies, but normally it appears as `Anaconda3-2020.07-Linux-x86_64.sh` for Intel systems and `Anaconda3-2020.07-Linux-ppc64le.sh` for PowerPC systems. The version number is embedded as part of the filename. In this case, the filename refers to version 3.2020.07, which is the version used for this book. If you use some other version, you may experience problems with the source code and need to make adjustments when working with it.

3.  **Type** `bash Anaconda3-2020.07-Linux-x86_64.sh` **(for the Intel version) or** `bash Anaconda3-2020.07-Linux-ppc64le.sh` **(for the PowerPC version) and press Enter.**

    An installation wizard starts that asks you to accept the licensing terms for using Anaconda.

4.  **Read the licensing agreement and accept the terms using the method required for your version of Linux.**

    The wizard asks you to provide an installation location for Anaconda. The book assumes that you use the default location for your platform. If you choose some other location, you may have to modify some procedures later in the book to work with your setup.

5.  **Provide an installation location (if necessary) and press Enter (or click Next).**

    The application extraction process begins. The installer asks whether you want to initialize Anaconda3 using the `conda init` command.

6.  **Type** `yes` **and press Enter or click Yes.**

    After the extraction is complete, you see a completion message.

7.  **Add the installation path to your** `PATH` **statement using the method required for your version of Linux.**

    You're ready to begin using Anaconda.

## Installing Anaconda on Mac OS X

The Mac OS X installation comes in only one form: 64-bit. The following steps help you install Anaconda 64-bit on a Mac system using the GUI method:

1.  **Locate the downloaded copy of Anaconda on your system.**

    The name of this file varies, but normally it appears as `Anaconda3-2020.07-MacOSX-x86_64.pkg`. The version number is embedded as part of the filename. In this case, the filename refers to version 3.2020.07, which is the version used for this book. If you use some other version, you may experience problems with the source code and need to make adjustments when working with it.

2.  **Double-click the installation file.**

    An introduction dialog box appears.

3.  **Click Continue.**

    The wizard asks whether you want to review the Read Me materials. You can read these materials later. For now, you can safely skip the information.

4.  **Click Continue.**

    The wizard displays a licensing agreement. Be sure to read through the licensing agreement so that you know the terms of usage.

5.  **Click I Agree if you agree to the licensing agreement.**

    The wizard asks you to provide a destination for the installation. The destination controls whether the installation is for an individual user or a group.

6.  **Click Continue.**

    This book assumes that you keep the default settings.

7.  **Click Install.**

    The installation begins. A progress bar tells you how the installation process is progressing. When the installation is complete, you see a completion dialog box.

8.  **Click Continue.**

    You’re ready to begin using Anaconda.

## Installing Anaconda on Windows

Anaconda comes with a graphical installation application for Windows, so getting a good install means using a wizard, as you would for any other installation. The following procedure should work fine on any Windows system, whether you use the 32-bit or the 64-bit version of Anaconda:

1.  **Locate the downloaded copy of Anaconda on your system.**
