segment_separators parameter. For instance, if you add the dash (-), you can write a pattern like '/article/:year-:month-:day/:title'.

+   - The pattern routing uses its own cache, in production mode, to speed up conversions between external URLs and internal URLs. By default, this cache uses the filesystem, but you can use any cache class, provided that you declare the class and its settings in the cache parameter. See Chapter 15 for the list of available cache storage classes. To deactivate the routing cache in production, set the debug parameter to true.

These are only the settings for the sfPatternRouting class. You can use another class for your application routing, either your own or one of symfony's routing factories (sfNoRouting and sfPathInfoRouting). With either of these two factories, all external URLs look like ‘module/action?key1=param1’. No customization possible—but it's fast. The difference is that the first uses PHP's GET, and the second uses PATH_INFO. Use them mainly for backend interfaces.

There is one additional parameter related to routing, but this one is stored in settings.yml:

+   - no_script_name enables the front controller name in generated URLs. The no_script_name setting can be on only for a single application in a project, unless you store the front controllers in various directories and alter the default URL rewriting rules. It is usually on for the production environment of your main application and off for the others.

# Form Validation Settings

> > The features described in this section are deprecated since symfony 1.1 and only work if you enable the sfCompat10 plugin.

Form validation settings control the way error messages output by the Validation helpers look (see Chapter 10). These errors are included in <div> tags, and they use the validation_error_ class setting as a class attribute and the validation_error_id_prefix setting to build up the id attribute. The default values are form_error and error_for_, so the attributes output by a call to the form_error() helper for an input named foobar will be class="form_error" id="error_for_foobar".

Two settings determine which characters precede and follow each error message: validation_error_prefix and validation_error_suffix. You can change them to customize all error messages at once.

# Cache Settings

Cache settings are defined in cache.yml for the most part, except for two in settings.yml: cache enables the template cache mechanism, and etag enables ETag handling on the server side (see Chapter 15). You can also specify which storage to use for two all cache systems (the view cache, the routing cache, and the i18n cache) in factories.yml. Listing 19-2 show the default view cache factory configuration.

*Listing 19-2 - View Cache Configuration Settings, in frontend/config/factories.yml*

```
view_cache:
  class: sfFileCache
  param:
    automatic_cleaning_factor: 0
    cache_dir: %SF_TEMPLATE_CACHE_DIR%
    lifetime: 86400
    prefix: %SF_APP_DIR%/template
```