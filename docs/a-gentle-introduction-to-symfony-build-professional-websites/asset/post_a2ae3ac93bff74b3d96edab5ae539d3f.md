
## Debugging

No matter how proficient a coder you are, you will eventually make mistakes, even if you use symfony. Detecting and understanding errors is one of the keys of fast application development. Fortunately, symfony provides several debug tools for the developer.

### Symfony Debug Mode

Symfony has a debug mode that facilitates application development and debugging. When it is on, the following happens:

- The configuration is checked at each request, so a change in any of the configuration files has an immediate effect, without any need to clear the configuration cache.
- The error messages display the full stack trace in a clear and useful way, so that you can more efficiently find the faulty element.
- More debug tools are available (such as the detail of database queries).
- The Propel/Doctrine debug mode is also activated, so any error in a call to a Propel/Doctrine object will display a detailed chain of calls through the Propel/Doctrine architecture.

On the other hand, when the debug mode is off, processing is handled as follows:

- The YAML configuration files are parsed only once, then transformed into PHP files stored in the `cache/config/` folder. Every request after the first one ignores the YAML files and uses the cached configuration instead. As a consequence, the processing of requests is much faster.
- To allow a reprocessing of the configuration, you must manually clear the configuration cache.
- An error during the processing of the request returns a response with code 500 (Internal Server Error), without any explanation of the internal cause of the problem.

The debug mode is activated per application in the front controller. It is controlled by the value of the third argument passed to the `getApplicationConfiguration()` method call, as shown in Listing 16-8.

*Listing 16-8 - Sample Front Controller with Debug Mode On, in web/frontend_dev.php*

```php
<?php

require_once(dirname(__FILE__).'/../config/ProjectConfiguration.class.php');

$configuration = ProjectConfiguration::getApplicationConfiguration('frontend', 'dev', true);
sfContext::createInstance($configuration)->dispatch();
```

> In your production server, you should not activate the debug mode nor leave any front controller with debug mode on available. Not only will the debug mode slow down the page delivery, but it may also reveal the internals of your application. Even though the debug tools never reveal database connection information, the stack trace of exceptions is full of dangerous information for any ill-intentioned visitor.

### Symfony Exceptions

When an exception occurs in the debug mode, symfony displays a useful exception notice that contains everything you need to find the cause of the problem.

The exception messages are clearly written and refer to the most probable cause of the problem. They often provide possible solutions to fix the problem, and for most common problems, the exception pages even contain a link to a symfony website page with more details about the exception. The exception page shows where the error occurred in the PHP code (with syntax highlighting), together with the full stack of method calls, as shown in Figure 16-1. You can follow the trace to the first call that caused the problem. The arguments that were passed to the methods are also shown.

Symfony really relies on PHP exceptions for error reporting. For instance, the 404 error can be triggered by an sfError404Exception.

Figure 16-1 - Sample exception message for a symfony application

![](img/0f886a7f4cbcc3939be96e985ca35ff4_287_0.png)

During the development phase, the symfony exceptions will be of great use as you debug your application.

### Xdebug Extension

The Xdebug PHP extension allows you to extend the amount of information that is logged by the web server. Symfony integrates the Xdebug messages in its own debug feedback, so it is a good idea to activate this extension when you debug the application. The extension installation depends very much on your platform; refer to the Xdebug website for detailed installation guidelines.

56. http://xdebug.org/

Once Xdebug is installed, you need to activate it manually in your php.ini file after installation. For *nix platforms, this is done by adding the following line:

```ini
zend_extension="/usr/local/lib/php/extensions/no-debug-non-zts-20041030/xdebug.so"
```

For Windows platforms, the Xdebug activation is triggered by this line:

```ini
extension=php_xdebug.dll
```

Listing 16-9 gives an example of Xdebug configuration, which must also be added to the php.ini file.

Listing 16-9 - Sample Xdebug Configuration

```ini
;xdebug.profiler_enable=1
;xdebug.profiler_output_dir="/tmp/xdebug"
xdebug.auto_trace=1          ; enable tracing
xdebug.trace_format=0
;xdebug.show_mem_delta=0     ; memory difference
;xdebug.show_local_vars=1
;xdebug.max_nesting_level=100
```

You must restart your web server for the Xdebug mode to be activated.

> Don't forget to deactivate Xdebug mode in your production platform. Not doing so will slow down the execution of every page a lot.

### Web Debug Toolbar

The log files contain interesting information, but they are not very easy to read. The most basic task, which is to find the lines logged for a particular request, can be quite tricky if you have several users simultaneously using an application and a long history of events. That's when you start to need a web debug toolbar.

This toolbar appears as a semitransparent box superimposed over the normal content in the browser, in the top-right corner of the window, as shown in Figure 16-2. It gives access to the symfony log events, the current configuration, the properties of the request and response objects, the details of the database queries issued by the request, and a chart of processing times related to the request.

Figure 16-2 - The web debug toolbar appears in the top-right corner of the window

![](img/0f886a7f4cbcc3939be96e985ca35ff4_288_0.png)

The color of the debug toolbar background depends on the highest level of log message issued during the request. If no message passes the debug level, the toolbar has a gray background. If a single message reaches the err level, the toolbar has a red background.

Don't confuse the debug mode with the web debug toolbar. The debug toolbar can be displayed even when the debug mode is off, although, in that case, it displays much less information.

To activate the web debug toolbar for an application, open the settings.yml file and look for the web_debug key. In the prod and test environments, the default value for web_debug is false, so you need to activate it manually if you want it. In the dev environment, the default configuration has it set to true, as shown in Listing 16-10.

Listing 16-10 - Web Debug Toolbar Activation, in frontend/config/settings.yml

```yaml
dev:
  .settings:
    web_debug: true
```

When displayed, the web debug toolbar offers a lot of information/interaction:

- Click the symfony logo to toggle the visibility of the toolbar. When reduced, the toolbar doesn't hide the elements located at the top of the page.
- Click the “config” section to show the details of the request, response, settings, globals, and PHP properties, as shown in Figure 16-3. The top line sums up the important configuration settings, such as the debug mode, the cache, and the presence of a PHP accelerator (they appear in red if they are deactivated and in green if they are activated).

Figure 16-3 - The “config” section shows all the variables and constants of the request

![](img/0f886a7f4cbcc3939be96e985ca35ff4_289_0.png)

- When the cache is enabled, a green arrow appears in the toolbar. Click this arrow to reprocess the page, regardless of what is stored in the cache (but the cache is not cleared).
- Click the “logs” section to reveal the log messages for the current request, as shown in Figure 16-4. According to the importance of the events, they are displayed in gray, yellow, or red lines. You can filter the events that are displayed by category using the links displayed at the top of the list.

Figure 16-4 - The “logs” section shows the log messages for the current request
