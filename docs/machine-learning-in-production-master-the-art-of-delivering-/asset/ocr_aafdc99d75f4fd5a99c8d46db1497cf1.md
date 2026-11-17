The class declaration is done here.

Use the Tk class to create the main window and call the mainloop() to keep the window displayed.

Also, the application window does not appear on the screen till mainloop() is not called, as it takes all the objects and widgets and renders them on screen.

```
1. window=Tk()
2.
3. mywin=MyWindow(window)
4.
5. # Create a title
6. window.title('ML App')
7.
8. # Define the size of the window
9. window.geometry("400x400+10+10")
10.
11. window.mainloop() #Keep the window displaying
```

Create a ml_app.py file for the Tkinter app and run it. It should make predictions based on the given input.

# # Convert Python app into Windows EXE file

Now, you can convert this Tkinter - ML app to Windows executable application using Pyinstaller, with the following steps. Pyinstaller packages a Python application and its dependencies into a single package that can be run independently without installing a Python interpreter.

Let’s create a virtual environment and install all the required dependencies.

Here, a virtual environment is created with Python version 3.7 using conda, as follows:

```
conda create -n envv_tkinter python=3.7 -y
```

Once it is created, activate it using:

```
source activate envv_tkinter
```

> Note: To remove the conda environment, you can execute the following command conda env remove -n envv_tkinter: