# Machine Learning

# Chapter 4: Getting Started with Python & Turi

```
sh Anaconda3-2019.07-MacOs-x86_64.sh
```

You'll have to accept the license agreement, and then the installer a directory to install Anaconda (or accept the default location that works for you). Once the installation starts, it may take a while.

While you're waiting for the installation to finish, scroll down to the Get Started links and take a closer look at Anaconda Training:

Get Started with Anaconda Distribution

| Documentation | Anaconda Blog | Community Support | Anaconda Webinars | Anaconda Training |
| :--- | :--- | :--- | :--- | :--- |
| Installation and user guide for Anaconda Distribution S | News, software developer and best practices | Solutions and questions from the community | Industry trends and solutions from Anaconda | Learn Python for Data DataCamp |
| Read More | Read More | Read More | Read More | Start Learning |

These are are videos about using Python for machine learning. Parts for free, others require you to be a subscriber before you can watch.

If you're asked to run conda init, type you yes. Once installation is complete, restart Terminal.. Once restarted, you can run the following command to check that the installation was successful.

```
conda --version
```

If the above command fails with a command not found message, chances are you'll need to add the Anaconda path to your global path environment variable. This means, you will have to edit the .bashrc or .zshrc file in your home directory (usually /Users/<username>). If the file doesn't exist, you'll have to create based on the shell your is currently using. If you're running Catalina or later, your current shell is likely Zsh.

In either case, open or create a .zshrc or .bashrc file and either find or add a line that resembles the one below. Assuming you installed Anaconda in your home directory, the line could look:

```
export PATH="Users/<username>/anaconda3/bin":"$PATH"
```

In this line, you prepend the path to the anaconda installation to your existing path. Two important things to note include the inclusion of the bin directory to the path, and the colon separating the installation path with the existing PATH variable.

![](bbox=[0.166, 0.923, 0.333, 0.953])