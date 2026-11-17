
## Code Organization

Now that you know the different components of a symfony application, you’re probably wondering how they are organized. Symfony organizes code in a project structure and puts the project files into a standard tree structure.

## Project Structure: Applications, Modules, and Actions

In symfony, a project is a set of services and operations available under a given domain name, sharing the same object model.

Inside a project, the operations are grouped logically into applications. An application can normally run independently of the other applications of the same project. In most cases, a project will contain two applications: one for the front-office and one for the back-office, sharing the same database. But you can also have one project containing many mini-sites, with each site as a different application. Note that hyperlinks between applications must be in the absolute form.

Each application is a set of one or more modules. A module usually represents a page or a group of pages with a similar purpose. For example, you might have the modules home, articles, help, shoppingCart, account, and so on.

Modules hold actions, which represent the various actions that can be done in a module. For example, a shoppingCart module can have the add, show, and update actions. Generally, actions can be described by a verb. Dealing with actions is almost like dealing with pages in a classic web application, although two actions can result in the same page (for instance, adding a comment to a post in a weblog will redisplay the post with the new comment).

> If this represents too many levels for a beginning project, it is very easy to group all actions into one single module, so that the file structure can be kept simple. When the application gets more complex, it will be time to organize actions into separate modules. As mentioned in Chapter 1, rewriting code to improve its structure or readability (but preserving its behavior) is called refactoring, and you will do this a lot when applying RAD principles.

### Figure 2-3 - Example of code organization

![](img/0f886a7f4cbcc3939be96e985ca35ff4_28_0.png)

## File Tree Structure

All web projects generally share the same types of contents, such as the following:

- A database, such as MySQL or PostgreSQL
- Static files (HTML, images, JavaScript files, style sheets, and so on)
- Files uploaded by the site users and administrators
- PHP classes and libraries
- Foreign libraries (third-party scripts)
- Batch files (scripts to be launched by a command line or via a cron table)
- Log files (traces written by the application and/or the server)
- Configuration files

Symfony provides a standard file tree structure to organize all these contents in a logical way, consistent with the architecture choices (MVC pattern and project/application/module grouping). This is the tree structure that is automatically created when initializing every project, application, or module. Of course, you can customize it completely, to reorganize the files and directories at your convenience or to match your client's requirements.

## Root Tree Structure

These are the directories found at the root of a symfony project:

```
apps/
    frontend/
    backend/
    cache/
    config/
    data/
    sql/
    doc/
    lib/
    model/
    log/
    plugins/
    test/
        bootstrap/
        unit/
        functional/
    web/
        css/
        images/
        js/
        uploads/
```

### Table 2-1 - Root Directories

| Directory | Description |
| --- | --- |
| apps/ | Contains one directory for each application of the project (typically, frontend and backend for the front and back office). |
| cache/ | Contains the cached version of the configuration, and (if you activate it) the cache version of the actions and templates of the project. The cache mechanism (detailed in Chapter 12) uses these files to speed up the answer to web requests. Each application will have a subdirectory here, containing preprocessed PHP and HTML files. |
| config/ | Holds the general configuration of the project. |
| data/ | Here, you can store the data files of the project, like a database schema, a SQL file that creates tables, or even a SQLite database file. |
| doc/ | A default place to store project documentation |
| lib/ | Dedicated to foreign classes or libraries. Here, you can add the code that needs to be shared among your applications. The model/ subdirectory stores the object model of the project (described in Chapter 8). |
| log/ | Stores the applicable log files generated directly by symfony. It can also contain web server log files, database log files, or log files from any part of the project. Symfony creates one log file per application and per environment (log files are discussed in Chapter 16). |
| plugins/ | Stores the plug-ins installed in the application (plug-ins are discussed in Chapter 17). |
| test/ | Contains unit and functional tests written in PHP and compatible with the symfony testing framework (discussed in Chapter 15). During the project setup, symfony automatically adds some stubs with a few basic tests. |
| web/ | The root for the web server. The only files accessible from the Internet are the ones located in this directory. |

## Application Tree Structure

The tree structure of all application directories is the same:

```
apps/
[application name]/
config/
i18n/
lib/
modules/
templates/
layout.php
```

### Table 2-2 - Application Subdirectories

| Directory | Description |
| --- | --- |
| config/ | Holds a hefty set of YAML configuration files. This is where most of the application configuration is, apart from the default parameters that can be found in the framework itself. Note that the default parameters can still be overridden here if needed. You'll learn more about application configuration in the Chapter 5. |
| i18n/ | Contains files used for the internationalization of the application—mostly interface translation files (Chapter 13 deals with internationalization). You can bypass this directory if you choose to use a database for internationalization. |
| lib/ | Contains classes and libraries that are specific to the application. |
| modules/ | Stores all the modules that contain the features of the application. |
| templates/ | Lists the global templates of the application—the ones that are shared by all modules. By default, it contains a layout.php file, which is the main layout in which the module templates are inserted. |

The i18n/, lib/, and modules/ directories are empty for a new application.

The classes of an application are not able to access methods or attributes in other applications of the same project. Also note that hyperlinks between two applications of the same project must be in absolute form. You need to keep this last constraint in mind during initialization, when you choose how to divide your project into applications.

## Module Tree Structure

Each application contains one or more modules. Each module has its own subdirectory in the modules directory, and the name of this directory is chosen during the setup.

This is the typical tree structure of a module:

```
apps/
  [application name]/
    modules/
      [module name]/
        actions/
          actions.class.php
        config/
        lib/
        templates/
          indexSuccess.php
```

### Table 2-3 - Module Subdirectories

| Directory | Description |
| --- | --- |
| actions/ | Generally contains a single class file named `actions.class.php`, in which you can store all the actions of the module. You can also write different actions of a module in separate files. |
| config/ | Can contain custom configuration files with local parameters for the module. |
| lib/ | Stores classes and libraries specific to the module. |
| templates/ | Contains the templates corresponding to the actions of the module. A default template, called `indexSuccess.php`, is created during module setup. |

The config/ and lib/ directories are not created automatically for a new module so you will need to create them manually if required.

## Web Tree Structure

There are very few constraints for the web directory, which is the directory of publicly accessible files. Following a few basic naming conventions will provide default behaviors and useful shortcuts in the templates. Here is an example of a web directory structure:

```
web/
  css/
  images/
  js/
  uploads/
```
