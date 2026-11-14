# 1: Can PHP comments be nested?

**Answer:**
PHP supports C, C++ and perl style of comments. PHP C-style comments cannot be nested.

# 2: What's the difference between echo and print?

**Answer:**
echo and print both are PHP constructs used for printing on the console. The main difference is that echo doesn't return any value, while print does. This makes echo faster than print.

# 3: What are the different types of errors in PHP?

**Answer:**
PHP has three different types of errors:

+   a) Notices: Non-trivial and non-critical errors that don't cause termination of script. For example, using a variable that has not been defined yet.

+   b) Warnings: For example, attempting to include file which doesn't exist. These errors are displayed to the users by default.

+   c) Fatal Errors: These cause the termination of script. For example, calling a non-existent function.

These can be listed as below –

E_ERROR: A fatal error that causes script termination

E_WARNING: Run-time warning that does not cause script termination

E_PARSE: Compile time parse error.

E_NOTICE: Run time notice caused due to error in code

E_CORE_ERROR: Fatal errors that occur during PHP's initial startup (installation)

E_CORE_WARNING: Warnings that occur during PHP's initial startup

E_COMPILE_ERROR: Fatal compile-time errors indication problem with script.

E_USER_ERROR: User-generated error message.

E_USER_WARNING: User-generated warning message.