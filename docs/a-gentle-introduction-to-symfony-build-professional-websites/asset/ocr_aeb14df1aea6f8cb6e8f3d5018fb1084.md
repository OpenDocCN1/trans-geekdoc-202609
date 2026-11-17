# # Feature Configuration

Symfony uses some parameters of `settings.yml` to alter the behavior of built-in features such as form validation, cache, and third-party modules.

# ## Output Escaping Settings

Output escaping settings control the way the variables are accessible in the template (see Chapter 7). The `settings.yml` file includes two settings for this feature:

+   * The `escaping_strategy` setting can take the value `true`, or `false`.
+   * The `escaping_method` setting can be set to `ESC_RAW`, `ESC_SPECIALCHARS`, `ESC_ENTITIES`, `ESC_JS`, or `ESC_JS_NO_ENTITIES`.

# ## Routing Settings

The routing settings (see Chapter 9) are defined in `factories.yml`, under the `routing` key. Listing 19-1 show the default routing configuration.

# #### Listing 19-1 - Routing Configuration Settings, in frontend/config/factories.yml

```
routing:
  class: sfPatternRouting
  param:
    load_configuration: true
    suffix:               .
    default_module:       default
    default_action:       index
    variable_prefixes:    [':']
    segment_separators:   ['/', '.']
    variable_regex:       '[\w\d_+]'
    debug:                %SF_DEBUG%
    logging:              %SF_LOGGING_ENABLED%
    cache:
      class: sfFileCache
      param:
        automatic_cleaning_factor: 0
        cache_dir:                 %SF_CONFIG_CACHE_DIR%/routing
        lifetime:                  31556926
        prefix:                    %SF_APP_DIR%
```

+   * The `suffix` parameter sets the default suffix for generated URLs. The default value is a period (`.`), and it corresponds to no suffix. Set it to `.html`, for instance, to have all generated URLs look like static pages.
+   * When a routing rule doesn't define the `module` or the `action` parameter, values from the `factories.yml` are used instead:
+     * `default_module`: Default module request parameter. Defaults to the `default` module.
+     * `default_action`: Default action request parameter. Defaults to the `index` action.
+   * By default, route patterns identify named wildcards by a colon (`:`) prefix. But if you want to write your rules in a more PHP-friendly syntax, you can add the dollar (`$`) sign in the `variable_prefixes` array. That way, you can write a pattern like `'/article/$year/$month/$day/$title'` instead of `'/article/:year/:month/:day/:title'`.
+   * The pattern routing will identify named wildcards between separators. The default separators are the slash and the dot, but you can add more if you want in the