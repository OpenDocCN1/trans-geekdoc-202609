+   ◆ Indexes: Directives controlling directory indexing
+   ◆ Limit: Directives limiting host access
+   ◆ Option: Directives controlling directory features

For more information on specific directives, see the next section, “Using Directives.”

![](bbox=[0.05, 0.255, 0.15, 0.33])

The .htaccess file can be a security risk. It’s better to set directory-specific settings in the main configuration file. Use .htaccess files only if you’re unable to set directory options in the main configuration file — such as when you don’t have access to the main configuration file.

# Using Directives

Many Apache directives are made available as part of the Apache core features. Other directives are made available and handled by modules. Some modules are compiled into Apache by default, but some must be specifically enabled when Apache is installed. You can’t use a directive unless the module that handles the directive is added to Apache. The documentation on the Apache Web site (httpd.apache.org) provides information on its availability for each module, as follows:

+   ◆ Core: A Core directive is provided by the Apache core and is always available.
+   ◆ MPM: An MPM directive is provided by a Multi-Processing Module. MPM is a type of module in Apache 2. A specific MPM is installed based on your operating system. Which directives are available depends on which MPM is installed. The documentation tells you which MPM is installed.
+   ◆ Base: A Base directive is provided by modules that are included in Apache by default. The directives are always available unless you specifically disabled a module during installation.
+   ◆ Extension: An Extension directive is provided by modules that are downloaded with Apache but not compiled into Apache by default. You must enable the module during installation before the directive is available.
+   ◆ Experimental: An Experimental directive is provided with Apache but is not yet considered stable. Use it at your own peril.

Directives have the following format:

```
Directive setting
```