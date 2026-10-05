
[content]
# Installing Ion Auth

Ion Auth is a simple and lightweight authentication library for CodeIgniter, licensed under the MIT License. See the License Agreement for Ion Auth.

I changed the coding style of the authentication source code a bit. Download the latest version (in this book we use v2.6.0-343-g7d1f6af) from http://github.com/benedmund/CodeIgniter-Ion-Auth/zipball/2 and unzip. Copy the following files into your CodeIgniter/application directory from the corresponding directory in the Zip package, except for application/migrations/001_install_ion_auth.php, which we will place in the CodeIgniter/application/database/migrations/

- CodeIgniter/
  application/
    config/
      auth.php
    controller/
      auth.php
    database/
      migrations/
        001_install_ion_auth.php
    language/
      english/
        auth_lang.php
        ion_auth_lang.php
  libraries/
    Crypt.php
    Ion_auth.php
  models/
    ion_auth_model.php
  views/
    auth/

Rename the class files to make them work with CodeIgniter 3.0:

```
application/controllers/auth.php -> Auth.php
application/models/ion_auth_model.php -> Ion_auth_model.php
```

Rename the migration file to use the timestamp format.

# Testing Controllers

application/database/migrations/001_install_ion_auth.php
-> 20150920182600_install_ion_auth.php

# Database Migrations

Update the migration config file.

```diff
--- a/CodeIgniter/application/config/migration.php
+++ b/CodeIgniter/application/config/migration.php
@@ -6,7 +6,7 @@ $config['migration_auto_latest'] = FALSE
 | be upgraded | downgraded to.
 /*
-$config['migration_version'] = 20150907090030;
+$config['migration_version'] = 20150920182600;
 /*
 |\-
```

The listing above is in a format called unified diff. It shows the difference between two files. In short, remove the red line starting with - from the original file and add the green line starting with +, to get the new file. See Conventions Used in This Book for details.

Run the migrations via CLI.

```bash
$ php index.php dbfixture migrate
```

If there is no output, the migration ran and the groups, users, users_groups, login_attempts tables were created successfully. You can confirm this using the sqlite3 command.

```bash
$ sqlite3 application/data/sqlite-database.db
SQLite version 3.8.5 2014-08-15 22:37:57
Enter ".help" .schema groups
sqlite> CREATE TABLE "groups" (
  "id" INTEGER PRIMARY KEY AUTOINCREMENT,
  "name" VARCHAR NOT NULL,
  "description" VARCHAR NOT NULL
);
sqlite> .schema users
```

# Routing

```sql
CREATE TABLE "users" (
  "id" INTEGER PRIMARY KEY AUTOINCREMENT,
  "ip_address" VARCHAR NOT NULL,
  "username" VARCHAR NOT NULL,
  "password" VARCHAR NOT NULL,
  "salt" VARCHAR NOT NULL,
  "email" VARCHAR NOT NULL,
  "activation_code" VARCHAR NOT NULL,
  "forgotten_password_code" VARCHAR NOT NULL,
  "forgotten_code_password_time" INT NULL,
  "remember_code" VARCHAR NOT NULL,
  "created_on" INT NULL,
  "last_login" INT NULL,
  "active" TINYINT NULL,
  "first_name" VARCHAR NOT NULL,
  "last_name" VARCHAR NOT NULL,
  "company" VARCHAR NOT NULL,
  "phone" VARCHAR NOT NULL
);
sql> .schema users_groups
CREATE TABLE "users_groups" (
  "id" INTEGER PRIMARY KEY AUTOINCREMENT,
  "user_id" MEDIUMINT NOT NULL,
  "group_id" MEDIUMINT NOT NULL
);
sql> .schema login_attempts
CREATE TABLE "login_attempts" (
  "id" INTEGER PRIMARY KEY AUTOINCREMENT,
  "ip_address" VARCHAR NOT NULL,
  "login" VARCHAR NOT NULL,
  "time" INT NULL
);
sql> .exit
```

You can see all the tables in the database. Add a route for auth.

```diff
--- a/CodeIgniter/application/config/routes.php
+++ b/CodeIgniter/application/config/routes.php
@@ -52,6 +52,8 @@ defined('BASEPATH') OR exit('No direct script allowed');
 $route['404_override'] = '';
 $route['translate_uri'] = FALSE;
+$route['auth'] = 'auth';
+
+$route['news/create'] = 'news/create';
+$route['news/(:any)'] = 'news/$1';
```

Need to add the route for auth after the above code which prevents the auth route from being resolved automatically by CodeIgniter.

# Manual Testing with a Web Browser

Let's access the login page using PHP's built-in server.

```bash
$ php -S 127.0.0.1:8000 index.php
```

Then, access http://127.0.0.1:8000/auth in your web browser. You should be directed to login and see the form below.

# Login form

Try to login using the default user. Type admin@admin.com in the "Email/Username" field and password in the "Password" field, then submit the form using the "Login" button. If you logged in successfully, you should be redirected to the Home page.

Then, access http://127.0.0.1:8000/auth. You should see the user list:

# Redirection

Let’s look at an example controller included in Ion Auth: application/controllers/Auth.php

```php
<?php defined('BASEPATH') or exit('No direct script allowed');

class Auth extends CI_Controller
{
    public function __construct()
    {
        parent::__construct();
        $this->load->database();
        $this->load->library(['ion_auth', 'form_validation']);
        $this->load->helper(['url', 'language']);
    }

    $this->form_validation->set_error_delimiters(
        $this->config->item('error_start_delimiter', 'ion_auth'),
        $this->config->item('error_end_delimiter', 'ion_auth')
    );

    // redirect if needed, otherwise display the user list
    public function index()
    {
        if (!$this->ion_auth->logged_in()) {
            // redirect them to the login page
            redirect('auth/login', 'refresh');
        }
        // remove this if you want to enable this for non-admins
        elseif (!$this->ion_auth->is_admin()) {
            // redirect them to the home page because they must be an
            // administrator to view this
            return show_error('You must be an administrator to view this page.');
        } else {
            // set the flash error message if there is one
            $this->data['message'] =
                (validation_errors()) ? validation_errors()
                : $this->session->flashdata('message');
        }

        // list the users
        $this->data['users'] = $this->ion_auth->users()->result();
        foreach ($this->data['users'] as $k => $user) {
            $this->data['users'][$k]->groups =
                $this->ion_auth->get_users_groups($user->id)->result();
        }
        $this->render_page('auth/index', $this->data);
    }
}
```

Testing redirection is very simple, because ci-phpunit-test provides a special redirect() function by default. You can use the $this->assertRedirect() method in ci-phpunit-test with the argument set to a URI string which will be used as the target of the redirect. So, the test case will be like the following: application/tests/controllers/Auth_test.php

```php
<?php
class Auth_test extends TestCase
{
    public function test_When_not_login_user_get_auth_Then_redirected() {
        $this->request('GET', 'auth');
        $this->assertRedirect('auth/login');
    }
}
```

Run the phpunit command and check that the test passes.

# Mocking Auth Objects

If you want to test the output by authenticated users, mocking auth objects is easy. You can use the $this->request->setCallable() method in ci-phpunit-test to inject mocks. We add the test method to the bottom of the test case. application/tests/controllers/Auth_test.php

```php
public function test_When_admin_get_auth_Then_returns_user_list() {
    $this->request->setCallable(
        function ($CI) {
            $auth = $this->getDouble(
                'Ion_auth', ['logged_in' => true, 'is_admin' => true]
            );
            $CI->ion_auth = $auth;
        }
    );

    $output = $this->request('GET', 'auth');
    $this->assertContains('<p>Below is a list of the users.</p>', $output);
}
```

The $this->getDouble() helper method in ci-phpunit-test to create a partial mock object. The logged_in() and is_admin() methods of the object return true. Run the phpunit command and check that the tests pass.

# Exercise

At this point, please stop and write rest tests for the Auth controller.

# 7.5 What if My Controller Needs Else?

We have covered all the common cases for testing controllers and we will learn more in the next two chapters.

- Chapter 8, Unit Testing CLI Controllers
- Chapter 9, Testing REST Controllers

In my opinion, we will have covered more than 90% of techniques to write test code for controllers by the time we finish Chapter 9. So, you will be able to write test code for almost anything.
