
config/
...
www/    # Public area
images/
css/
js/
index.php

In this case, the root directory is the symfony/ directory. So the index.php front controller simply needs to include the config/ProjectConfiguration.class.php file as follows for the application to work:

```
Listing 19-9
require_once(dirname(__FILE__).'/../symfony/config/ProjectConfiguration.class.php');
```

In addition, use the setWebDir() method to change the public area from the usual web/ to www/, as follows:

```
Listing 19-10
class ProjectConfiguration extends sfProjectConfiguration
{
    public function setup()
    {
        // ...

        $this->setWebDir($this->getRootDir().'/../www');
    }
}
```

## Understanding Configuration Handlers

Each configuration file has a handler. The job of configuration handlers is to manage the configuration cascade, and to do the translation between the configuration files and the optimized PHP code executable at runtime.

## Default Configuration Handlers

The default handler configuration is stored in sfConfig::get('sf_symfony_lib_dir')/config/config/config_handlers.yml. This file links the handlers to the configuration files according to a file path. Listing 19-6 shows an extract of this file.

Listing 19-6 - Extract of sfConfig::get('sf_symfony_lib_dir')/config/config/config_handlers.yml

```
Listing 19-11
config/settings.yml:
class:   sfDefineEnvironmentConfigHandler
param:
  prefix: sf_

config/app.yml:
class:   sfDefineEnvironmentConfigHandler
param:
  prefix: app_

config/filters.yml:
class:   sfFilterConfigHandler
modules/*/config/module.yml:
 class: sfDefineEnvironmentConfigHandler
 param:
   prefix: mod_
   module: yes
```

For each configuration file (`config_handlers.yml` identifies each file by a file path with wildcards), the handler class is specified under the `class` key.

The settings of configuration files handled by `sfDefineEnvironmentConfigHandler` can be made available directly in the code via the `sfConfig` class, and the `param` key contains a prefix value.

You can add or modify the handlers used to process each configuration file—for instance, to use INI or XML files instead of YAML files.

> The configuration handler for the `config_handlers.yml` file is `sfRootConfigHandler` and, obviously, it cannot be changed.

If you ever need to modify the way the configuration is parsed, create an empty `config_handlers.yml` file in your application’s `config/` folder and override the `class` lines with the classes you wrote.

## Adding Your Own Handler

Using a handler to deal with a configuration file provides two important benefits:

- The configuration file is transformed into executable PHP code, and this code is stored in the cache. This means that the configuration is parsed only once in production, and the performance is optimal.
- The configuration file can be defined at different levels (project and application) and the final parameter values will result from a cascade. So you can define parameters at a project level and override them on a per-application basis.

If you feel like writing your own configuration handler, follow the example of the structure used by the framework in the `sfConfig::get('sf_symfony_lib_dir')/config/` directory.

Let’s suppose that your application contains a `myMapAPI` class, which provides an interface to a third-party web service delivering maps. This class needs to be initialized with a URL and a user name, as shown in Listing 19-7.

## Listing 19-7- Example of Initialization of the `myMapAPI` Class

```
$mapApi = new myMapAPI();
$mapApi->setUrl($url);
$mapApi->setUser($user);
```

You may want to store these two parameters in a custom configuration file called `map.yml`, located in the application `config/` directory. This configuration file might contain the following:

```
api:
  url: map.api.example.com
  user: foobar
```

In order to transform these settings into code equivalent to Listing 19-7, you must build a configuration handler. Each configuration handler must extend `sfConfigHandler` and provide an `execute()` method, which expects an array of file paths to configuration files as a parameter, and must return data to be written in a cache file. Handlers for YAML files should extend the sfYamlConfigHandler class, which provides additional facilities for YAML parsing. For the map.yml file, a typical configuration handler could be written as shown in Listing 19-8.

## Listing 19-8 - A Custom Configuration Handler, in frontend/lib/myMapConfigHandler.class.php

```
<?php

class myMapConfigHandler extends sfYamlConfigHandler
{
    public function execute($configFiles)
    {
        // Parse the yaml
        $config = $this->parseYamls($configFiles);

        $data = "<?php\n";
        $data .= "\$mapApi = new myMapAPI();\n";

        if (isset($config['api']['url']))
        {
            $data .= sprintf("\$mapApi->setUrl('%s');\n", $config['api']['url']);
        }

        if (isset($config['api']['user']))
        {
            $data .= sprintf("\$mapApi->setUser('%s');\n", $config['api']['user']);
        }

        return $data;
    }
}
```

The $configFiles array that symfony passes to the execute() method will contain a path to all the map.yml files found in the config/ folders. The parseYamls() method will handle the configuration cascade.

In order to associate this new handler with the map.yml file, you must create a config_handlers.yml configuration file with the following content:

```
Listing 19-15
config/map.yml:
class: myMapConfigHandler
```

> The class must either be autoloaded (that's the case here) or defined in the file whose path is written in a file parameter under the param key.

As with many other symfony configuration files, you can also register a configuration handler directly in your PHP code:

```
Listing 19-16
sfContext::getInstance()->getConfigCache()->registerConfigHandler('config/map.yml', 'myMapConfigHandler', array());
```

When you need the code based on the map.yml file and generated by the myMapConfigHandler handler in your application, call the following line:

```
include sfContext::getInstance()->getConfigCache()->checkConfig('config/map.yml');
```

When calling the checkConfig() method, symfony looks for existing map.yml files in the configuration directories and processes them with the handler specified in the config_handlers.yml file, if a map.yml.php does not already exist in the cache or if the map.yml file is more recent than the cache.

If you want to handle environments in a YAML configuration file, the handler can extend the sfDefineEnvironmentConfigHandler class instead of sfYamlConfigHandler. Instead of calling the parseYaml() method to retrieve the configuration, you should call the getConfiguration() method: $config = $this->getConfiguration($configFiles).

## Using Existing configuration handlers

If you just need to allow users to retrieve values from the code via sfConfig, you can use the sfDefineEnvironmentConfigHandler configuration handler class. For instance, to have the url and user parameters available as sfConfig::get('map_url') and sfConfig::get('map_user'), define your handler as follows:

```
config/map.yml:
class: sfDefineEnvironmentConfigHandler
param:
  prefix: map_
```

Be careful not to choose a prefix already used by another handler. Existing prefixes are sf_, app_, and mod_.

## Summary

The configuration files can heavily modify the way the framework works. Because symfony relies on configuration even for its core features and file loading, it can adapt to many more environments than just the standard dedicated host. This great configurability is one of the main strengths of symfony. Even if it sometimes frightens newcomers, who see in configuration files a lot of conventions to learn, it allows symfony applications to be compatible with a very large number of platforms and environments. Once you become a master of symfony's configuration, no server will ever refuse to run your applications!
