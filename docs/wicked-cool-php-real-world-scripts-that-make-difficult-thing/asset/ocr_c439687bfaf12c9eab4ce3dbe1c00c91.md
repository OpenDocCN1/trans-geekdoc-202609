+   4. On your server, create another directory called *templates* for your Smarty templates. Create two subdirectories here: *html* for the raw templates and *compile* for Smarty-compiled templates.

+   5. Make the compile directory writeable by the webserver. If you’re not sure how to do that, “File Permissions” on page 91 will show you the way.

+   6. In the templates directory, create (or upload) a file called smarty_initialize.php, containing the following:

```
<?php
define ("SMARTY_DIR", "/path/to/web/root/smarty/");
require_once (SMARTY_DIR."Smarty.class.php");
$smarty = new Smarty;
$smarty->compile_dir = "/path/to/web/root/templates/compile";
$smarty->template_dir = "/path/to/web/root/templates/html";
?>
```

Four aspects of the smarty_initialize.php file are very important:

+   - The SMARTY_DIR constant points at the Smarty library directory.
+   - To load the library, smarty_initialize.php requires the Smarty.class.php file.
+   - Because Smarty is object-oriented, you must create a new Smarty object. This script does so with $smarty = new Smarty.
+   - Smarty needs to know where your template and compile directories are. Two object attributes (compile_dir and template_dir) control this location.

Now that you’ve got Smarty set up, it’s time to learn how to use it.

# ## A Brief Smarty Tutorial

Let’s look at the Smarty language. In the smarty_initialize.php file outlined in the previous section, Smarty templates go in the templates/html directory. Typically, template files are everyday HTML, JavaScript, CSS, or anything else that you’d want to send to a web browser. Let’s say that you have some HTML in a template named basic.tpl. To make Smarty display this template, use Smarty’s display() method, as shown in the following code:

```
<?php
require_once("smarty_initialize.php");
$smarty->display("basic.tpl");
?>
```

To access the true power of Smarty, you need to put PHP-created data into a template. Use curly braces with a dollar sign ($) to create a Smarty