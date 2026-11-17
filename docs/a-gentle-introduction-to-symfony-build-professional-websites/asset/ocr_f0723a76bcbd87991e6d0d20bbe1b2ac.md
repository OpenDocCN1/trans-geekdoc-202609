```
config/
...
www/    # Public area
images/
css/
js/
index.php
```

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

# Understanding Configuration Handlers

Each configuration file has a handler. The job of configuration handlers is to manage the configuration cascade, and to do the translation between the configuration files and the optimized PHP code executable at runtime.

# Default Configuration Handlers

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
```