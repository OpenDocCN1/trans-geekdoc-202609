+   view.yml: The structure of the default view (name of the layout, default style sheets and JavaScript files to be included, default content-type, and so on) is set in this file. Chapter 7 will tell you more about this file. These settings can be overridden for each module.

> All the symfony configuration files are described in great details in the symfony reference book32.

# Internationalization Configuration

Internationalized applications can display pages in several languages. This requires specific configuration. There are two configuration places for internationalization:

+   The factories.yml of the application config/ directory: This file defines the i18n factory and general translation options, such as the default culture for the translation, whether the translations come from files or a database, and their format.

+   Translation files in the application i18n/ directory: These are basically dictionaries, giving a translation for each of the phrases used in the application templates so that the pages show translated text when the user switches language.

Note that the activation of the i18n features is set in the settings.yml file. You will find more information about these features in Chapter 13.

# Additional Application Configuration

A second set of configuration files is in the symfony installation directory (in sfConfig::get('sf_symfony_lib_dir')/config/config/) and doesn't appear in the configuration directory of your applications. The settings defined there are defaults that seldom need to be modified, or that are global to all projects. However, if you need to modify them, just create an empty file with the same name in your myproject/apps/frontend/config/ directory, and override the settings you want to change. The settings defined in an application always have precedence over the ones defined in the framework. The following are the configuration files in the symfony installation config/ directory:

+   autoload.yml: This file contains the settings of the autoloading feature. This feature exempts you from requiring custom classes in your code if they are located in specific directories. It is described in detail in Chapter 19.

+   core_compile.yml: These are lists of classes to be included to start an application. These classes are actually concatenated into an optimized PHP file without comments, which will accelerate the execution by minimizing the file access operations (one file is loaded instead of more than forty for each request). This is especially useful if you don't use a PHP accelerator. Optimization techniques are described in Chapter 18.

+   config_handlers.yml: This is where you can add or modify the handlers used to process each configuration file. Chapter 19 provides more details.

# Module Configuration

By default, a module has no specific configuration. But, if required, you can override some application-level settings for a given module. For instance, you might do this to include a specific JavaScript file for all actions of a module. You can also choose to add new parameters restricted to a specific module to preserve encapsulation.