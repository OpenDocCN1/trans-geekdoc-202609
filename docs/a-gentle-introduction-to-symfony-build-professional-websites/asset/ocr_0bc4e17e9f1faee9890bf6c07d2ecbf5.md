To customize these pages, simply create error/error.html.php and unavailable.php in your project or application's config/ directory. Symfony will use these templates instead of its own.

To have requests redirected to the unavailable.php page when needed, you need to set the check_lock setting to true in the application settings.yml. The check is deactivated by default, because it adds a very slight overhead for every request.

# Optional Feature Activation

Some parameters of the settings.yml file control optional framework features that can be enabled or disabled. Deactivating unused features boosts performances a bit, so make sure to review the settings listed in Table 19-1 before deploying your application.

# Table 19-1 - Optional Features Set Through settings.yml

| Parameter | Description | Default Value |
| :--- | :--- | :--- |
| use_database | Enables the database manager. Set it to false if you don't use a database. | true |
| i18n | Enables interface translation (see Chapter 13). Set it to true for multilingual applications. | false |
| logging_enabled | Enables logging of symfony events. Set it to false when you want to turn symfony logging off completely. | true |
| escaping_strategy | Enables the output escaping feature (see Chapter 7). Set it to true if you want data passed to your templates to be escaped. | true |
| cache | Enables template caching (see Chapter 12). Set it to true if one of your modules includes cache.yml file. The cache filter (sfCacheFilter) is enabled only if it is on. | false in development, true in production |
| web_debug | Enables the web debug toolbar for easy debugging (see Chapter 16). Set it to true to display the toolbar on every page. | true in development, false in production |
| check_symfony_version | Enables the check of the symfony version for every request. Set it to true for automatic cache clearing after a framework upgrade. Leave it set to false if you always clear the cache after an upgrade. | false |
| check_lock | Enables the application lock system, triggered by the cache:clear and project:disable tasks (see the previous section). Set it to true to have all requests to disabled applications redirected to the sfConfig::get('sf_symfony_lib_dir')/exception/data/unavailable.php page. | false |
| compressed | Enables PHP response compression. Set it to true to compress the outgoing HTML via the PHP compression handler. | false |