# Chapter 12: Django Installation

The first thing you need to do is to install a few programs on your machine so you can be able to begin using Django. The basic setup involves installing Python, Virtualenv, and Django. Briefly:

+   - You first need to install Python

+   - Then you can proceed to install the virtual environment that will help isolate your Python and Django projects.

+   - Next, you should install Django within the virtual environment. This way, you can isolate your project.

# Install Python

The first thing you need to do is install the latest Python distribution. You can go to early chapters to learn how to install Python, or go to www.Python.org and scroll down until you see the download files listed. Select the correct version based on your Windows distribution. If you're not sure which one is perfect for you, the possibilities are you want to download the Windows x86-64 executable installer version.

Navigate to your Downloads directory, right-click on the installer and select Run as administrator.

After Python installation, the next thing you need to do is search for the Command Prompt program and open it. To check whether everything is working fine, enter the following command: Python --version

The output should display the Python version you've installed on your computer.

If you can see the version of Python installed on your computer, Congratulations, Python is running. Now is time to install Virtual Environments.

# Installing Virtualenv

In the next step, you'll use pip, this tool will help you control and install Python packages. In order to install virtualenv, type the following command in the Command Prompt.

```
pip install virtualenv
```