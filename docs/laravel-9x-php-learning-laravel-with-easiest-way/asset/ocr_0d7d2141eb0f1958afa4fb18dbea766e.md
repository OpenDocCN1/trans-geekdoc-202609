```
```php
*/
public function __construct(UserRepository $users)
{
    $this->users = $users;
}

/**
 * Show the profile for the given user.
 *
 * @param int $id
 * @return Response
 */
public function show($id)
{
    $user = $this->users->find($id);

    return view('user.profile', ['user' => $user]);
}
}
```
```

In this example, the UserController needs to retrieve users from a data source. So, we will

inject a service that is able to retrieve users. In this context, our UserRepository most likely uses

Eloquent to retrieve user information from the database. However, since the repository is