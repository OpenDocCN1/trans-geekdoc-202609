+   3. Project
+   4. Specific environment
+   5. All environments
+   6. Default

# # The Configuration Cache

Parsing YAML and dealing with the configuration cascade at runtime represent a significant overhead for each request. Symfony has a built-in configuration cache mechanism designed to speed up requests.

The configuration files, whatever their format, are processed by some special classes, called handlers, that transform them into fast-processing PHP code. In the development environment, the handlers check the configuration for changes at each request, to promote interactivity. They parse the recently modified files so that you can see a change in a YAML file immediately. But in the production environment, the processing occurs once during the first request, and then the processed PHP code is stored in the cache for subsequent requests. The performance is guaranteed, since every request in production will just execute some well-optimized PHP code.

For instance, if the app.yml file contains this:

```
all:
    # Setting for all environments
mail:
  webmaster:  webmaster@example.com
```

then the file config_app.yml.php, located in the cache/ folder of your project, will contain this:

```
<?php
sfConfig::add(array(
  'app_mail_webmaster' => 'webmaster@example.com',
));

```

As a consequence, most of the time, the YAML files aren't even parsed by the framework, which relies on the configuration cache instead. However, in the development environment, symfony will systematically compare the dates of modification of the YAML files and the cached files, and reprocess only the ones that have changed since the previous request.

This presents a major advantage over many PHP frameworks, where configuration files are compiled at every request, even in production. Unlike Java, PHP doesn't share an execution context between requests. For other PHP frameworks, keeping the flexibility of XML configuration files requires a major performance hit to process all the configuration at every request. This is not the case in symfony. Thanks to the cache system, the overhead caused by configuration is very low.

There is an important consequence of this mechanism. If you change the configuration in the production environment, you need to force the reparsing of all the configuration files for your modification to be taken into account. For that, you just need to clear the cache, either by deleting the content of the cache/ directory or, more easily, by calling the cache:clear task:

```
$ php symfony cache:clear
```