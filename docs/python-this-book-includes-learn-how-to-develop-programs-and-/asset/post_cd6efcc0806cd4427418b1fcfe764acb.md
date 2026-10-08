
Let’s start with the manage.py file:

## 1. Manage.py

This is the file that holds details of the command line for the project and you will use this file to run, debug, and test the project.
The files store code for running the server, migrating the server and controlling the project using the command-line.
The above file provides all the functions just like Django-admin and it also delivers certain project functionalities.
While building your project, you will make use of the following commands often:

- **Runserver:** You will use this command to run the test server in the Django framework. This is also one of the advantages of Django over other frameworks.
- **Makemigrations:** This command is useful for combining the project files you have added in it. This command will basically review for any new additions within your project and add that to the same.
- **Migrate:** The last command is to include these migrations you have engineered in the last command with the entire project. The difference between this command and the previous one is that the initial command is used to save the changes within the file, and the later one applies that change to the entire project.

## 2. My_project

This is a Python package for the project. It contains the files for configuring the project settings.\init__.py
This particular file is empty, and it’s available in the project for the main reason of learning the Python interpreter understand that the above directory is a package. That’s one of the standard guidelines for Python packages.

### settings.py
The settings.py is the primary file where you will be adding all applications and middleware applications. As the name goes, is the main settings file of the Django project. This file has installed applications and middleware information which are installed on this Django project.
Any time you install a new application, you will be adding in this file. Notice that there are certain pre-installed applications. By default, these applications provide all the basic functionality you will ever want for your website such as the Django admin app.

### Url.py
This file features the project URL details. The URL is the general resource locator and it presents you with the address of the resource plus other components for your website.
The major function of this file is to link the web-apps with the project. This urls.py file will execute anything that you'll be typing inside the URL bar.
Then, it will relate your request to the particular app you connected to.

```python
from django.contrib import admin
from django.urls import path

urlpatterns = [
    path('admin/', admin.site.urls),
]
```

In this example, by default, the file adds one URL to the admin app.
The path () accepts two arguments.
First, the url to be looked inside the URL bar on the local server, and secondly, the file you want to run when URL request is matched. The admin is the pre-made application and the file is URL's file of that app. This file acts as a map of your Django project.

### Wgi.py

Remember that Django is developed using Python, which relies on the WSGI server for web development. This file handles that you won't be using this file a.
Wsgi is still significant though if you want to run the applications on Apache servers, or a different server because Django is backend, it will require your support with various servers. However, you should not worry, for each server, you will get a Django middleware which will solve all the connectivity and integration challenges. You only need to have an important relevant middleware for your server. It's that simple.
This last section has explored more about the Django project layout and the way all files in the Django architecture align, and what's their purpose.
These files are fundamental and will be available in any Django application you build individually. Their primary function is to make available all the backend support and resolve connectivity problems. It takes place while you handle the database creation. It also handles frontend and the uniqueness of your website or web-application.

# Chapter 14: Create, Install, Deploy First Django App

In this chapter, you will learn how to create, install, and run your first Django app. Furthermore, you'll learn how to add the app in urls.py file and build views.py for the Django project.
Let's dive in.

# 1. Creating a Django App

The main reason web applications are used is make use of the Django code's reusability property. This will allow you to not only migrate the built apps within the project but also personalize web applications.
All the commands are available in the root directory or within the directory where there is the manage.py file.
Additionally, before you build Django application, run this command on your system within the project directory.

```
python manage.py makemigrations
```

Once this command is finished executing, run the following command:

```bash
python manage.py migrate
```

Building a Django project is simple because you only need to write some commands that will be implemented on your system.
In the case below, both terminal and PowerShell users share the same commands:

```bash
django-admin startapp application-name
```

Now, running these commands will create the application. If you look at the root directory, you will see files that the new application will require, and you will be editing them to accomplish set goals.
Here are some tips that might help you:

- Name your applications based on different tasks that they’re going to execute.
- Build applications if the task can be accomplished using a separate application.

If you adhere to the above tips, you will create modularity within your project. This habit will not only help you in general practice, but anytime you be building future projects you can be specific as to what kind of apps to include in your current project. Hence, boosting your development speed and reducing the workload without losing any quality in your work. Below are files that will come pre-installed when your application is developed and the formats for every application file doesn’t change.

# 2. Install Django App

Once you have defined your application, the next step is to install the application.
So, you need to open the settings.py file and change it.
Keep in mind that you will be changing the main settings.py file of your Django project, not the one within the app directory.
You will only need to type your app-name in the INSTALLED_APPS list once you add the application in the list of Installed Apps.
Once you complete that, congratulations, you have installed custom Django application.
Now, you will need to include the app to your urls.py file that anyone who searches the URL of the app within the browser will open the above app.

# 3. Adding App in urls.py

To include the app in the urls.py, you will need to write some code. First, you need to define a new Python file in the demo directory and paste the following code in that file.

```python
from django.urls import path
from . import views
urlpatterns = [
    path('', views.index, name='index'),
]
```

In the above code, you are passing a message to the Django project that you've to trigger this function in the views.py file.
Don't be scared; you'll be changing that file too.
In the above code, you've imported the django.urls package and path function from there.
The path () function is new functionality in Django 2.0. If you have any previous versions, it's better to upgrade.
This code passes two arguments, first there is the URL which was searched and relayed to the URL bar from the browser. The other argument is to run the file or function, which is an index function.
Now, you'll be changing the urls.py file in the main Django project.
There is only a single item on the list and you'll need to add the new data.

```python
from django.contrib import admin
from django.urls import include, path

urlpatterns = [
    path('admin/', admin.site.urls),
]
```

After including the apps urls.
