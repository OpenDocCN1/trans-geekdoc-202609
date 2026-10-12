
</a>

<div class="dropdown-menu dropdown-menu-right" aria-labelledby="navbarDropdown">

    <a class="dropdown-item" href="#">Edit Profile</a>

    <a class="dropdown-item" href="#">Change Password</a>

    <div class="dropdown-divider"></div>

    <a class="dropdown-item" href="{{ route('logout') }}"
       onclick="event.preventDefault(); document.getElementById('logout-form').submit();">
        Logout

        <form id="logout-form" action="{{ route('logout') }}" method="POST" style="display: none;">
            {{ csrf_field() }}
        </form>
    </a>

</div>

</li>

</ul>

</div>

</nav>

---

Now if you refresh your page, it's starting to look like a real Laraventory app. Click on the account settings menu on the right of the navbar then click logout. You should now be logged out of the application. If you are thinking, how did we get here? I will explain shortly.

## Logout

From the authentication scaffold that was generated earlier, Laravel already created a route and controller to handle clearing the current user session and redirecting you to the login page. If you run `php artisan route:list` on the terminal you would see the list of all existing routes registered.

Notice from the above snippet that once the user clicks the logout button, we added an inline javascript to submit a hidden form. It sends a `POST` request to the logout route and this is because the logout route was registered as a post request.

Also in the logout form is a `csrf_field()` function to add an input field with a csrf token into the form and session to prevent Cross Site Request Forgery. Any request made to this form from an outside attacker can't go through because it will be hard for the attacker to guess the csrf token in a user session to allow the attacker pass through the csrf middleware.

The output of the function looks something like below. Inspect the form to see the generated hidden input with the csrf token as the value.

```
<input type="hidden" name="_token" value="S50zdnqbwioh0VQN8OoETHecuBUKbRIRLAGs4TaI">
```

---

## Displaying A Welcome Message

We will be adding a notification message to the dashboard to welcome users when they login. Open `resources/views/dashboard.blade.php` and update it to match below.

```
@extends('layout.master')

@section('page-title')
    Welcome
@endsection

@section('content')
    <div class="container-fluid">
        <div class="alert alert-success mt-4" role="alert">
            <h4 class="alert-heading">Welcome!</h4>
            <p>{{auth()->user()->name}}, you have successfully logged in. There are<strong>3</strong> items in our inventory.</p>
            <hr>
        </div>
    </div>
@endsection
```

---

You can access any attribute of a logged in user from the User model via `auth()->user()`. If you are trying to access a logged user details from a route that is not protected by the auth middleware, to avoid getting an error you should first check if the user is logged in by using `auth()->check()` in an if statement.

The `auth()` function is made available by Laravel in every of your pages. That's how much Laravel makes things easier for you.

Before we move into the next section, let us update the url linking to the dashboard on the sidenav. Open `resources/views/layout/partials/_sidenav.blade.php` and update the menu with our dashboard url using the named route.

```
<a href="{{route('inventory.home')}}" class="list-group-item list-group-item-action bg-light">Dashboard</a>
```

---

One more benefit of using a named route, is that in the future if we decide to change our dashboard url from `/app` to `/app/dashboard` we don't need to go everywhere we used that url to make the changes. We only need to make the changes in our route file, since the named route references the changes we made, we always get the new url every time. See it like a key and value thing in an array where the key is the same but value changes and since we reference the array key we get the updated value every time.

## Create Inventory

Let me break down the steps to allow logged in users create a new inventory. This will help you follow through easily. We will be building this feature in the following order:

*   Create an inventories migration to generate the inventories table
*   Create an Inventory Model for the inventories table
*   Define relationship between a user and many inventories in our Model
*   Create an Inventory Controller class
*   Define a get route to display the create new inventory page
*   Define a create method in the `InventoryController` class
*   Create a form with matching fields to our database
*   Define a post route to submit the new inventory
*   Create validation for our inventory
*   Define a store method to create the entry into the database
*   Redirect to new inventory page and display a success notification

Without much ado let us get started! Shall we?

To create our migration, run:

```
php artisan make:migration create_inventories_table --create=inventories
```

---

The `--create` option is to indicate whether the migration is for a new table. To edit an existing table the `--table` option will be passed instead. That being said, let us add fields to our migration. Laravel provides us with methods to create different data types such as string, int, longText, boolean, foreign key with constraint etc.

For our inventories table, edit your migration file located in the `database/migrations` directory and update the content of the `up` method to match below. The `up` method is called when we run the migrate command to create the database while the `down` method, you can guess already, is called when we run the command to rollback our migration, to drop tables from the database.

```
// up method
Schema::create('inventories', function (Blueprint $table) {
    $table->increments('id');
    $table->string('item');
    $table->integer('quantity');
    $table->integer('user_id');
    $table->foreign('user_id')->references('id')->on('users');
    $table->softDeletes();
    $table->timestamps();
});
```

---

To start with, the `increments` method creates an incrementing column ID (primary key) using an "UNSIGNED INTEGER" equivalent.

```
$table->increments('id');
```

---

The `string` method creates a "VARCHAR" equivalent column ITEM. This method can take a second argument of the size, default is 255.

```
$table->string('item');
```

---

The `integer` methods create an "INTEGER" equivalent column QUANTITY.

```
$table->integer('user_id');
```

---

The `foreign` method is used to specify foreign key constraints, which are used to force referential integrity at the database level. It references the "PRIMARY KEY" ID on the users table. We added the `user_id` column to specify which inventory was created by a particular user using the user PRIMARY ID.

```
$table->foreign('user_id')->references('id')->on('users');
```

---

The `softDeletes` method adds nullable `deleted_at` columns for soft deletes. What this does is ensure that once we call the laravel query builder delete method, the current timestamp will be added to that row on the inventories table instead of dropping the row from the table. This will aid us in building the recycle bin feature.

```
$table->softDeletes();
```

---
