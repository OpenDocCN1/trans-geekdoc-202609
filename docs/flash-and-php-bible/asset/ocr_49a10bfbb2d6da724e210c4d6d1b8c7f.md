# Configuration files

Modifying the configuration files (*.conf) can produce a performance increase if you remove directives that are not being used. As you learn the configuration layout, you can remove the comments, which will make it easier to look at it in the long run.

Apache provides a series of configuration starter files, but try to avoid the high-performance version because it actually becomes less efficient in the long run. The reason is because this version overly optimizes Apache, which forces it to run less efficiently unless you are experiencing very high traffic.

# Logging and errors

Whenever possible try to limit the amount of log usage. You can either disable logging altogether or limit the amount of information that is written to the logs. Errors are harder to trace because Apache does not inform you of these issues. In most cases, however, when a server is functioning properly this is not a problem.

If you choose to enable logging, make sure you edit those files on a different machine because the process of opening and parsing these sometimes large files can have a performance impact.

# MaxClients

You can modify the MaxClients directive in the httpd.conf configuration file to increase performance, but be aware that any client attempting to connect after the limit is hit will be unable to view your site. In rare cases, this may not be a bad thing because it will preserve the performance for the existing users.

```
<IfModule prefork.c>
StartServers 8
MinSpareServers 5
MaxSpareServers 20
MaxClients 150
MaxRequestsPerChild 1000
</IfModule>
```

> **NOTE** The MaxClients directive only applies when the prefork module is configured and enabled.

There are other ways to optimize Apache, but short of adding additional hardware and cost to your organization, this list will have your server running much more efficiently.

# Optimizing MySQL

Now that you have optimized PHP and the Apache Web server, the next logical place to optimize is MySQL. You can optimize MySQL after it is installed, but there are some good practices to keep in mind prior to installing it, when possible.