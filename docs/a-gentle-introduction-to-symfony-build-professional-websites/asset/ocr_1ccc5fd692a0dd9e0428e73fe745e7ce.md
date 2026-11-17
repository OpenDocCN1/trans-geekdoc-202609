For instance, if your application doesn't use the session mechanism, or if you want to start the session handling by hand, you should turn the auto_start setting to false in the storage key of the factories.yml file, as in Listing 18-18.

# Listing 18-18 - Turning Sessions Off, in frontend/config/factories.yml

```
```yaml
all:
  storage:
    class: sfSessionStorage
    param:
      auto_start: false
```
```

The same applies for the database feature (as explained in the “Tweaking the Model” section earlier in this chapter). If your application makes no use of a database, deactivate it for a small performance gain, this time in the settings.yml file (see Listing 18-19).

# Listing 18-19 - Turning Database Features Off, in frontend/config/settings.yml

```
```yaml
all:
  .settings:
    use_database: false # Database and model features
```
```

As for the security features (see Chapter 6), you can deactivate them in the filters.yml file, as shown in Listing 18-20.

# Listing 18-20 - Turning Features Off, in frontend/config/filters.yml

```
```yaml
rendering: ~
security:
  enabled: false

# generally, you will want to insert your own filters here

cache: ~
execution: ~
```
```

Some features are useful only in development, so you should not activate them in production. This is already the case by default, since the production environment in symfony is really optimized for performance. Among the performance-impacting development features, the debug mode is the most severe. As for the symfony logs, the feature is also turned off in production by default.

You may wonder how to get information about failed requests in production if logging is disabled, and argue that problems arise not only in development. Fortunately, symfony can use the sfErrorLoggerPlugin plug-in, which runs in the background in production and logs the details of 404 and 500 errors in a database. It is much faster than the file logging feature, because the plug-in methods are called only when a request fails, while the logging mechanism, once turned on, adds a non-negligible overhead whatever the level. Check the installation instructions and manual66.

> Make sure you regularly check the server error logs—they also contain very valuable information about 404 and 500 errors.