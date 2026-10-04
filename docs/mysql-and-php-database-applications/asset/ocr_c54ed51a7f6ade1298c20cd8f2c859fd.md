# Appendix E: PHP Function Reference

| Function | Returns | Action |
| --- | --- | --- |
| flush(void) | void | Flushes the output buffer |
| sleep(int seconds) | void | Delays for a given number of seconds |
| usleep(int micro seconds) | void | Delays for a given number of microseconds |
| get_current_user(void) | string | Gets the name of the owner of the current PHP script |
| get_cfg_var(string option_name) | string | Gets the value of a PHP configuration option |
| is_resource(mixed var) | bool | Returns true if variable is a resource |
| error_log(string message, int message_type string destination [, string extra_headers]) | int | Sends an error to an error log, TCP port, or file |
| call_user_func(string function_name [, mixed parameter]) | mixed | Calls a user function that is the parameter |
| call_user_method(string method_name, object object [, mixed parameter ...]) | mixed | Calls a user method on a specific object where the first argument is the method name, the second argument is the object, and the subsequent arguments are the parameters |
| register_shutdown_function(function_name) | void | Registers a user-level function to be called on request termination |
| highlight_file(string file_name) | void | Outputs a PHP source file with syntax highlights |
| highlight_string(string string) | void | Syntax highlights a string |
| ini_get(string varname) | string | Gets a configuration option |
| ini_set(string varname, string value) | string | Sets a configuration option, returns false on error and the string of the old value of the configuration option on success |

Continued