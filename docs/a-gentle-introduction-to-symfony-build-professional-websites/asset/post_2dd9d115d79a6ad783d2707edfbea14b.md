
- view.yml: The structure of the default view (name of the layout, default style sheets and JavaScript files to be included, default content-type, and so on) is set in this file. Chapter 7 will tell you more about this file. These settings can be overridden for each module.

> All the symfony configuration files are described in great details in the symfony reference book32.

## Internationalization Configuration

Internationalized applications can display pages in several languages. This requires specific configuration. There are two configuration places for internationalization:

- The factories.yml of the application config/ directory: This file defines the i18n factory and general translation options, such as the default culture for the translation, whether the translations come from files or a database, and their format.

- Translation files in the application i18n/ directory: These are basically dictionaries, giving a translation for each of the phrases used in the application templates so that the pages show translated text when the user switches language.

Note that the activation of the i18n features is set in the settings.yml file. You will find more information about these features in Chapter 13.

## Additional Application Configuration

A second set of configuration files is in the symfony installation directory (in sfConfig::get('sf_symfony_lib_dir')/config/config/) and doesn't appear in the configuration directory of your applications. The settings defined there are defaults that seldom need to be modified, or that are global to all projects. However, if you need to modify them, just create an empty file with the same name in your myproject/apps/frontend/config/ directory, and override the settings you want to change. The settings defined in an application always have precedence over the ones defined in the framework. The following are the configuration files in the symfony installation config/ directory:

- autoload.yml: This file contains the settings of the autoloading feature. This feature exempts you from requiring custom classes in your code if they are located in specific directories. It is described in detail in Chapter 19.

- core_compile.yml: These are lists of classes to be included to start an application. These classes are actually concatenated into an optimized PHP file without comments, which will accelerate the execution by minimizing the file access operations (one file is loaded instead of more than forty for each request). This is especially useful if you don't use a PHP accelerator. Optimization techniques are described in Chapter 18.

- config_handlers.yml: This is where you can add or modify the handlers used to process each configuration file. Chapter 19 provides more details.

## Module Configuration

By default, a module has no specific configuration. But, if required, you can override some application-level settings for a given module. For instance, you might do this to include a specific JavaScript file for all actions of a module. You can also choose to add new parameters restricted to a specific module to preserve encapsulation.

As you may have guessed, module configuration files must be located in a myproject/apps/frontend/modules/mymodule/config/ directory. These files are as follows:

- generator.yml: For modules generated according to a database table (scaffoldings and administrations), this file defines how the interface displays rows and fields, and which interactions are proposed to the user (filters, sorting, buttons, and so on). Chapter 14 will tell you more about it.
- module.yml: This file contains custom parameters specific to a module and action configuration. Chapter 6 provides more details.
- security.yml: This file sets access restrictions for actions. This is where you specify that a page can be viewed only by registered users or by a subset of registered users with special permissions. Chapter 6 will tell you more about it.
- view.yml: This file contains configuration for the views of one or all of the actions of a module. It overrides the application view.yml and is described in Chapter 7.

Most module configuration files offer the ability to define parameters for all the views or all the actions of a module, or for a subset of them.

## Too many files?

You might be overwhelmed by the number of configuration files present in the application. But please keep the following in mind:

Most of the time, you don't need to change the configuration, since the default conventions match the most common requirements. Each configuration file is related to a particular feature, and the next chapters will detail their use one by one. When you focus on a single file, you can see clearly what it does and how it is organized. For professional web development, the default configuration is often not completely adapted. The configuration files allow for an easy modification of the symfony mechanisms without code. Imagine the amount of PHP code necessary to achieve the same amount of control. If all the configuration were located in one file, not only would the file be completely unreadable, but you could not redefine configuration at several levels (see the “Configuration Cascade” section later in this chapter).

The configuration system is one of the great strengths of symfony, because it makes symfony usable for almost every kind of web application, and not only for the ones for which the framework was originally designed.

## Environments

During the course of application development, you will probably need to keep several sets of configuration in parallel. For instance, you will need to have the connection settings for your tests database available during development, and the ones for your real data available for production. To answer the need of concurrent configurations, symfony offers different environments.

### What Is an Environment?

An application can run in various environments. The different environments share the same PHP code (apart from the front controller), but can have completely different configurations. For each application, symfony provides three default environments: production (prod), test (test), and development (dev). You're also free to add as many custom environments as you wish.

So basically, environments and configuration are synonyms. For instance, a test environment will log alerts and errors, while a prod environment will only log errors. Cache acceleration is often deactivated in the dev environment, but activated in the test and prod environments. The dev and test environments may need test data, stored in a database distinct from the one used in the production environment. So the database configuration will be different between the two environments. All environments can live together on the same machine, although a production server generally contains only the prod environment.

In the dev environment, the logging and debugging settings are all enabled, since maintenance is more important than performance. On the contrary, the prod environment has settings optimized for performance by default, so the production configuration turns off many features. A good rule of thumb is to navigate in the development environment until you are satisfied with the feature you are working on, and then switch to the production environment to check its speed.

The test environment differs from the dev and prod environment in other ways. You interact with this environment solely through the command line for the purpose of functional testing and batch scripting. Consequently, the test environment is close to the production one, but it is not accessed through a web browser. It simulates the use of cookies and other HTTP specific components.

To change the environment in which you're browsing your application, just change the front controller. Until now, you have seen only the development environment, since the URLs used in the example called the development front controller:

```
http://localhost/frontend_dev.php/mymodule/index
```

However, if you want to see how the application reacts in production, call the production front controller instead:

```
http://localhost/index.php/mymodule/index
```

If your web server has mod_rewrite enabled, you can even use the custom symfony rewriting rules, written in web/.htaccess. They define the production front controller as the default execution script and allow for URLs like this:

```
http://localhost/mymodule/index
```
