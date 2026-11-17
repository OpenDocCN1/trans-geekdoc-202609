your web server (such as the Apache error logs). In this case, you will find the PHP logs under
the web server log directory.

# Symfony Logs

In addition to the standard PHP logs, symfony can log a lot of custom events. You can find all
the symfony logs under the myproject/log/ directory. There is one file per application and
per environment. For instance, the development environment log file of the frontend
application is named frontend_dev.log, the production one is named
frontend_prod.log, and so on.

If you have a symfony application running, take a look at its log files. The syntax is very
simple. For every event, one line is added to the log file of the application. Each line includes
the exact time of the event, the nature of the event, the object being processed, and any
additional relevant details. Listing 16-2 shows an example of symfony log file content.

# Listing 16-2 - Sample Symfony Log File Content, in log/frontend_dev.log

```
Nov 15 16:30:25 symfony [info] {sfAction} call
"barActions->executemessages()"
Nov 15 16:30:25 symfony [info] {sfPropelLogger} executeQuery: SELECT
bd_message.ID...
Nov 15 16:30:25 symfony [info] {sfView} set slot "leftbar" (bar/index)
Nov 15 16:30:25 symfony [info] {sfView} set slot "messageblock" (bar/
mes...
Nov 15 16:30:25 symfony [info] {sfView} execute view for template
"messa...
Nov 15 16:30:25 symfony [info] {sfView} render "/home/production/
myproject/...
Nov 15 16:30:25 symfony [info] {sfView} render to client
```

You can find many details in these files, including the actual SQL queries sent to the
database, the templates called, the chain of calls between objects, and so on.

> The format of the file logs is configurable by overriding the format and/or the
> time_format settings in factories.yml as shown in Listing 16-3.

# Listing 16-3 - Changing the Log Format

```
all:
  logger:
    param:
      sf_file_debug:
        param:
          format:      %time% %type% [%priority%] %message%%EOL%
          time_format: %b %d %H:%M:%S
```

# Symfony Log Level Configuration

There are eight levels of symfony log messages: emerg, alert, crit, err, warning,
notice, info, and debug, which are the same as the PEAR::Log^55 package levels. You can
configure the maximum level to be logged in each environment in the factories.yml
configuration file of each application, as demonstrated in Listing 16-4.

# Listing 16-4 - Default Logging Configuration, in frontend/config/factories.yml