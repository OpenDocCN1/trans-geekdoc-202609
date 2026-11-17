```
# Project files
/cache/*
/log/*
/web/*_dev.php
/web/uploads/*

# SCM files
.arch-params
.bzr
_darcs
.git
.hg
.monotone
.svn
CVS
```

> The cache/ and log/ directories must not be synchronized with the development server, but they must at least exist in the production server. Create them by hand if the myproject/ project tree structure doesn't contain them.

# Managing a Production Application

The command that is used most often in production servers is cache:clear. You must run it every time you upgrade symfony or your project (for instance, after calling the project:deploy task), and every time you change the configuration in production.

```
$ php symfony cache:clear
```

> If the command-line interface is not available in your production server, you can still clear the cache manually by erasing the contents of the cache/ folder.

You can temporarily disable your application—for instance, when you need to upgrade a library or a large amount of data.

```
$ php symfony project:disable APPLICATION_NAME ENVIRONMENT_NAME
```

By default, a disabled application displays the sfConfig::get('sf_symfony_lib_dir')/exception/data/unavailable.php page, but if you create your own unavailable.php file in your project's config/ directory, symfony will use it instead.

The project:enable task reenables the application and clears the cache.

```
$ php symfony project:enable APPLICATION_NAME ENVIRONMENT_NAME
```

> project:disable currently has no effect if the check_lock parameter is not set to true in settings.yml.