As you may have guessed, module configuration files must be located in a myproject/apps/frontend/modules/mymodule/config/ directory. These files are as follows:

+   - generator.yml: For modules generated according to a database table (scaffoldings and administrations), this file defines how the interface displays rows and fields, and which interactions are proposed to the user (filters, sorting, buttons, and so on). Chapter 14 will tell you more about it.
+   - module.yml: This file contains custom parameters specific to a module and action configuration. Chapter 6 provides more details.
+   - security.yml: This file sets access restrictions for actions. This is where you specify that a page can be viewed only by registered users or by a subset of registered users with special permissions. Chapter 6 will tell you more about it.
+   - view.yml: This file contains configuration for the views of one or all of the actions of a module. It overrides the application view.yml and is described in Chapter 7.

Most module configuration files offer the ability to define parameters for all the views or all the actions of a module, or for a subset of them.

# Too many files?

You might be overwhelmed by the number of configuration files present in the application. But please keep the following in mind:

Most of the time, you don't need to change the configuration, since the default conventions match the most common requirements. Each configuration file is related to a particular feature, and the next chapters will detail their use one by one. When you focus on a single file, you can see clearly what it does and how it is organized. For professional web development, the default configuration is often not completely adapted. The configuration files allow for an easy modification of the symfony mechanisms without code. Imagine the amount of PHP code necessary to achieve the same amount of control. If all the configuration were located in one file, not only would the file be completely unreadable, but you could not redefine configuration at several levels (see the “Configuration Cascade” section later in this chapter).

The configuration system is one of the great strengths of symfony, because it makes symfony usable for almost every kind of web application, and not only for the ones for which the framework was originally designed.

# Environments

During the course of application development, you will probably need to keep several sets of configuration in parallel. For instance, you will need to have the connection settings for your tests database available during development, and the ones for your real data available for production. To answer the need of concurrent configurations, symfony offers different environments.

# What Is an Environment?

An application can run in various environments. The different environments share the same PHP code (apart from the front controller), but can have completely different configurations. For each application, symfony provides three default environments: production (prod), test (test), and development (dev). You're also free to add as many custom environments as you wish.

So basically, environments and configuration are synonyms. For instance, a test environment will log alerts and errors, while a prod environment will only log errors. Cache acceleration