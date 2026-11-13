# FIGURE 7.3 A sample value from the magic_quotes_gpc property as seen in the phpinfo() listing

![](bbox=[0.119, 0.18, 0.755, 0.56])

# Disabling magic_quotes

In less common server configurations this feature cannot be turned off. A quick test to determine if that setting is enabled ensures extra slashes will not be added.

```
if (!ini_get('magic_quotes_gpc'))
{
	$s = addslashes($s);
}
```

The other two functions in the sanitization class simply clean the passed-in data and return it.

# Using shared objects

As you begin to build more complete applications you will come to a point where storing some small amounts of data on the user's machine becomes necessary. These small pieces of information generally hold a user id or session that maps to a database entry on the live server. A Shared Object Flash cookie is used in this case because it is a small piece of data stored on the user's machine but isn't required for the application to run.