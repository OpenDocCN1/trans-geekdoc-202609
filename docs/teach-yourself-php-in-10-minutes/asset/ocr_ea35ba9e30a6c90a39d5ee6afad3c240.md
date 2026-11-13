**Include Directories** If you want to list more than one location in the `safe_mode_include_dir` directive, you can separate them using colons on Linux/Unix or semicolons on Windows systems just as you do with the `include_path` setting.

To allow inclusion of files in `/usr/local/include/php` for any user in Safe Mode, you would use the following directive:

```
safe_mode_include_dir = /usr/local/include/php
```

To provide a location from which the system can be executed, you use the `safe_mode_exec_dir` directive.

To allow programs in `/usr/local/php-bin` to be executed in Safe Mode, you would use the following directive:

```
safe_mode_exec_dir = /usr/local/php-bin
```

**Executables** Rather than allow execution of all programs from `/usr/bin` or some other system location, you should create a new directory and copy or link only selected binaries into it.

To allow setting of certain environment variables, you use the `safe_mode_allowed_env_vars` directive. The value given is a prefix, and by default it allows only environment variables that begin with `PHP_` to be changed. If more than one value is given, the list should be separated by commas.

The following directive also allows the time zone environment variable, `TZ`, to be changed:

```
safe_mode_allowed_env_vars = PHP_, TZ
```