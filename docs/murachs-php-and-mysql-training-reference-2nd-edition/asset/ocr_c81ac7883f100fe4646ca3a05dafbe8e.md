# # How to use NetBeans
to develop a PHP application

Although a text editor is adequate for developing simple PHP applications like the ones for this book, most professional PHP developers use an *Integrated Development Environment (IDE)* that’s designed for developing PHP applications. However, an IDE can also be useful as you’re learning how to develop PHP applications.

If you’re interested, we recommend the NetBeans IDE for PHP. This free IDE runs on all major operating systems, and it provides many features that make it easier to edit and test PHP applications. To learn how to install this IDE, please refer to the appendixes. To learn how to get started with this IDE, please read the three topics that follow.

# ## How to work with PHP projects and files

When you use NetBeans, all of the directories and files for an application are grouped within a *project*. You can also have more than one project open at the same time. In figure 1-16, the Projects tab of NetBeans shows that two projects are open: `ch01_product_discount` and `ch02_future_value`.

When you work with NetBeans, you can start commands by using the menus, clicking on the toolbar buttons, or right-clicking on an object and using the resulting shortcut menu, just as you would with any application. In this figure, for example, you can see how to open a project, start a new project, or close a project by using the toolbar buttons, but you can get the same results by using the commands in the File menu.

To work with the files in a project, you can use the Projects tab to view the files for the project. Then, you can open any file by double-clicking on the filename in the Projects tab. In this figure, for example, three of the files for the `ch01_product_discount` project are open in the text editor, and the file named `display_discount.php` is displayed. To start a new file, you can select the project in the Projects tab and click the New File button in the toolbar.

Incidentally, when you create a NetBeans project, NetBeans adds a subdirectory named `nbproject` to the application root directory. It uses this subdirectory and its files to manage the project. However, this has no effect on the operation of the project, and you can still edit the files using a standard text editor.

In addition, the applications you download from our website are NetBeans projects that contain an `nbprojects` subdirectory, so you should be able to open them by using the Open Project button and then navigating to the `\xampp\htdocs\` folder.