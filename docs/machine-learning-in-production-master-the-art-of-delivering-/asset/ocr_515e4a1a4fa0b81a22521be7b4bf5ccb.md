+   - Build an ML-based app using kivy and kivyMD
+   - Convert Python app into Android app using Buildozer

# # Objectives

After studying this chapter, you should be able to build and deploy ML-based native apps, such as Windows and Android apps. This chapter is divided into two sections. By the end of the first section, you should be comfortable using Tkinter for developing ML-based Windows apps. You can also convert a Python app to an independent Windows executable file. By the end of the second section, you should be able to develop ML-based kivy applications and convert them into Android apps using the Buildozer package.

# # Introduction to Tkinter

Tkinter is a free software released under a Python license.

Tkinter is the Python interface to the Tk GUI library. Tk is derived from the **Tool Command Language (TCL)**, which is a scripting language. The best part is that you do not need to install Tkinter explicitly as it comes with Python since 1994.

Tkinter enables developers to create widgets (GUI elements) easily, which are packaged in the Tk toolkit. With widgets, developers can create buttons, menus, and input fields to get user data. These widgets can be linked to Python features, methods, data, or other widgets.

For instance, a button widget can be used to perform a certain action upon click event, or it can call the function and pass the user’s data as parameters.

> > Note: Get the latest version of Tkinter by installing Python 3.7 or a later version.

You can verify the Tkinter installation using the following command:

```
python -m tkinter
```

A pop-up window will appear, as shown below, which contains TCL/Tk version and text as This should be a cedilla: ç.

![](bbox=[0.392, 0.781, 0.602, 0.921])

Figure 8.1: Tkinter