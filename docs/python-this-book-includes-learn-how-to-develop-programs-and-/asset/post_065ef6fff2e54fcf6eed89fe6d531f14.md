
This will present us with the following directory structure:

```
myproject/
|-- myproject/
|   |-- boards/                <-- our new django app!
|   |   |-- migrations/
|   |   |       +--- __init__.py
|   |   |-- __init__.py
| ||-- admin.py
|   ||-- apps.py
|   ||-- models.py
|   ||-- tests.py
|   |+-- views.py
|-- myproject/
|   |-- __init__.py
|   |-- settings.py
|   |-- urls.py
|   |-- wsgi.py
+-- manage.py
```

Now, that you have created the first app, let's configure the project to use it.
To accomplish that, open the settings.py and try to search for INSTALLED_APPS variable:

# Settings.py

Django already has 6 built-in apps installed. These apps provide common functionalities that many Web applications require, such as sessions, css, static files management, etc.
You will learn more about these apps in the later chapters. But for now, let them be and only add your boards app to the list of INSTALLED_APPS:

Hello, World!

Let's create the first view. You will learn more about it in the next chapter. For now, let's check out how it feels building a new page using Django.
First, open the views.py file within the boards app, and include the following code:

```
from django.http import HttpResponse

def home(request):
    return HttpResponse('Hello, World!')
```

Views are Python functions that accept an HttpRequest object and displays an HttpResponse object. Accept a request as a parameter and return a response as a result. That's the flow you need to remember.
So, here is a simple view definition known as home which returns a message Hello, World.
Next, you have to instruct Django when to serve this view. It happens within the urls.py file:

# Urls.py

```
from django.conf.urls import url
from django.contrib import admin

from boards import views

urlpatterns = [
    url(r'^$', views.home, name='home'),
    url(r'^admin/', admin.site.urls),
]
```

# Chapter 13: MVC Pattern

The previous section dealt with the installation of everything you need. Hopeful, you're all set up with Python and Django. We already created the project you're going to use.

# The MVC Pattern

This section will review the MVC pattern. You will understand more about the MVC pattern. Django MVC architecture solves many problems that were available in the traditional approach for web development. For every website on the internet, it has three main components: Input Logic, UI logic, and Business Logic.

These sections of code perform different roles, the input logic within the dataset, and how the data organizes in the database.

It merely accepts inputs and directs it to the database in the right format. Business logic is the primary controller that takes care of the output from the server within the HTML. The UI logic as the names, refers to the HTML, CSS, and JavaScript pages.

When the traditional technique was used for running all this code was implemented in a single file. This was not a huge problem back in the time, the web pages were highly static, and websites didn't feature multimedia and extensive coding. Additionally, this architecture presents challenges for developers during testing and project maintenance.

Now, the times are different, and the websites are getting larger and larger every day while supporting applications as online artificial intelligence, cloud computing, and online development environment, these projects are all built within the MVC architecture.

Well, what is MVC? This is a short for Model View Controller. Don't be scared, and you'll learn every feature of the MVC pattern and associate it to Django.

The MVC pattern is one of the Product Development Architecture. It computes the traditional approach' challenges of code in a single file. There are three major parts of the MVC. That includes the Model, View, and Controller.

The difference between these parts allows the developer to concentrate on one major feature of the web-app and thus, robust code for one function significant testing, scalability and debugging.

Let’s look at the components:

# 1. Model

The Model represents the section of web-app, which works as a mediator between the website interface and the database. In technical terms, the object executes the logic for the application’s data domain. There are moments when the application may only consume data in a given dataset, and directly send it to the view without requiring any database then the dataset seen as a model.

While nowadays, if you want any website you need to have some type of database because its extra user input even if you’re building a simple blog site.

The Model refers to the component which carries the Business Logic within the Django architecture.

For example:
Once you sign up on any website, you’ll be sending information to the controller, which later transfers it to the models which have business logic and stores in the database.

# 2. View

The View section contains the UI of the Django framework. The View is made up of HTML, CSS and other technologies. Overall, the UI develops from the Model components.

# 3. Controller

The controller is the engine part. In other words, the controller takes care of the user interaction and clicks a view based on the model.
The main function of the controller is to choose a view component depending on the user interaction and apply the model component.
This architecture has numerous benefits, and that’s why Django is built on this architecture. It takes the same model to a complex level.

For example:
When you combine the previous standards, you can clearly understand that the component which is choosing different views and transferring the data to the model’s parts is the controller.

# MTV Pattern

MTV stands for the Model-Template-View framework. It carries the Templates terminology for Views and Views for Controller.

Templates are connected to the View within the MVC pattern because it describes the presentation layer that handles the presentation logic in the framework and controls the content to display and how to present it for the user.

# Advantages of Using the Django Architecture

The Django framework is developed on the above architecture, and it communicates between all these three parts without the need to create complex code. That's the reason why Django is becoming popular. There are various advantages that Django architecture comes with:

- 1. Rapid Development
This Django architecture divides into different components that simplifies it for numerous developers to work on separate features of the application simultaneously. That is one of the properties of Django.

- 2. Loosely Coupled
The Django architecture has different parts that depend on each other at varying stages of the application at every point that enhances the security of the general website.

- 3. Easy to Make Changes
This is a great feature of development because there are different sections in the Django architecture. If there is a change in section parts, you don't need to change it in other parts.

This is one of the key features of Django because it provides more adaptability to the website than other frameworks.
