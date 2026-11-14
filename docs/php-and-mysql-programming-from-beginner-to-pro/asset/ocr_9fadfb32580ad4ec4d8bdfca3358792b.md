4. Module Entry Point: This defines the extension for the Zend Engine, including version details, dependencies, and references to initialization and shutdown functions.

```
zend_module_entry example_extension_module_entry = {
STANDARD_MODULE_HEADER,
"example_extension",
example_extension_functions, /* Function entries */
PHP_MINIT(example_extension), /* Module initialization */
NULL, /* Module shutdown */
NULL, /* Request initialization */
NULL, /* Request shutdown */
NULL, /* Module info */
"1.0", /* Version */
STANDARD_MODULE_PROPERTIES
};
```

5. Compiling the Extension: Use `phpize`, `./configure`, and `make` to compile the extension, producing a shared object file that can be loaded into PHP via the `extension` directive in `php.ini`.