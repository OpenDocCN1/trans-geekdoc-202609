# Appendix C

# Output Buffer Functions

The functions in the table that enable you to control the output buffer from PHP.

| Function | Description |
| --- | --- |
| flush() | Flushes the output buffer. |
| ob_start() | Enables output buffering. |
| ob_get_contents() | Gets the contents of the output buffer. |
| ob_get_length() | Gets the length of the output buffer. |
| ob_end_flush() | Sends the output buffer contents and disables buffering. |
| ob_end_clean() | Deletes the output buffer contents and disables buffering. |
| ob_implicit_flush() | Toggles implicit flushing on and off. |

# PHP Configuration Information

With these functions, you can easily determine what your PHP is communicating to the server based on its setup, and alter configuration options from your PHP script.

| Function | Description |
| --- | --- |
| assert (assertion) | Verifies whether or not an assertion is false. |
| assert_options(what, [ value]) | Returns the assert flags. |
| dl(library) | Loads the named extension library. |
| extension_loaded(name) | Verifies whether or not an extension library has been loaded. |
| get_cfg_var(var) | Returns the named configuration value. |
| get_current_user() | Returns the owner of the PHP script. |
| get_defined_constants() | Returns an array with all the defined constants and values. |
| get_extension_funcs(module_name) | Returns the functions in the named module. |
| get_include_path() | Returns the current include_path configuration option. |
| get_included_files() | Returns an array containing the filenames of those included in the script with the include_once() function. |

636