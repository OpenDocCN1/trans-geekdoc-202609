# Implementing the Basic Site

This code looks very simple because it mostly calls functions from the function API that you will construct for this application. We look at the details of these functions shortly. Just looking at this file, you can see that it includes a file (containing the functions) and then calls some functions to render an HTML header, display some content, and render an HTML footer.

The output from this script is shown in Figure 27.3.

![](bbox=[0.142, 0.233, 0.757, 0.573])

Figure 27.3 The front page of the PHPbookmark system is produced by the HTML rendering functions in login.php

The functions for the system are all included in the file bookmark_fns.php, shown in Listing 27.3.

# Listing 27.3 bookmark_fns.php—Include File of Functions for the Bookmark Application

```
<?php
// We can include this in all our files
// this way, every file will contain all our functions and exceptions
require_once('data_valid_fns.php');
require_once('db_fns.php');
require_once('user_auth_fns.php');
require_once('output_fns.php');
require_once('url_fns.php');
?>
```