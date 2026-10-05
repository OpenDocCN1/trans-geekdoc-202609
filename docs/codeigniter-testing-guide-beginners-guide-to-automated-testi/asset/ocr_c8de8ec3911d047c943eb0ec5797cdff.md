# Testing Controllers

```
--- a/CodeIgniter/application/config/routes.php
+++ b/CodeIgniter/application/config/routes.php
@@ -52,6 +52,8 @@ defined('BASEPATH') OR exit('No direct script access allowed');
$route['404_override'] = '';
$route['translate_uri_dashes'] = FALSE;

+$route['auth'] = 'auth';
+
$route['news/create'] = 'news/create';
$route['news/(:any)'] = 'news/view/$1';
$route['news/'] = 'news';```
```

> To CodeIgniter users
Need to add the route for auth, because we have the route '$route['(:any)'] = 'pages/view/$1;' after the above code, which prevents the auth route from being resolved automatically by CodeIgniter.

# Manual Testing with a Web Browser

Let's access the login page using PHP's built-in web server.

```
$ php -S 127.0.0.1:8000 index.php
```

Then, access http://127.0.0.1:8000/auth in your web browser. You should be directed to auth/login and see the form below.