# FIGURE 2.3

PHP require() error as seen in the browser

![](bbox=[0.123, 0.18, 0.75, 0.56])

# include

The include() statement is similar to the require with the exception it will display an error but not stop the execution of the script.

```
include("optionalFile.php");
```

# require_once

The require_once statement behaves similarly to require, with the exception that if the current file is already loaded it will not attempt to load it again. This is more useful as you continue to build large applications that sometimes share many files. This ensures that no redundant code is loaded.

```
require_once("requiredFile.php");
// ... other code here
require_once("requiredFile.php");
```

The second require_once will not run because the file has already been loaded in the previous portion of the code.