7. To persist the setting of Homebrew Python for all Terminal windows, type and run the following command in the Terminal window depending on which shell you have on your Mac:

```
echo alias python=/usr/local/bin/python3 >> ~/.bashshrc
```

Or, type and run the following command:

```
echo alias python=/usr/local/bin/python3 >> ~/.zshrc
```

# Installing Jupyter Notebook on macOS

Now, we are ready to install the Jupyter Notebook on your machine:

+   1. Inside the Terminal window, run the following command:

```
brew install jupyter
```

+   2. Start the Jupyter Notebook by running the following command in your Terminal window:

```
jupyter notebook
```

# Installing Python3 on a Windows machine

Download the Windows installer for Python 3.9.1 using the following URL:

https://www.python.org/ftp/python/3.9.1/python-3.9.1-amd64.exe

Run the installer and follow the instructions to complete the installation.

# Installing PIP3

Follow the given steps to complete the installation:

+   1. Download https://bootstrap.pypa.io/get-pip.py and save it to a local folder on the PC.

+   2. Open a Command Prompt window and navigate to the folder where the file is saved.

+   3. Run the following command to install pip:

```
py get-pip.py
```