```
Route::get(
    '/user/profile',
    [UserProfileController::class, 'show']
)->name('profile');
```

> {note} Route names should always be unique.

# Generating URLs To Named Routes

Once you have assigned a name to a given route, you may use the route's name when generating

URLs or redirects via Laravel's route and redirect helper functions:

```
// Generating URLs...
$url = route('profile');

// Generating Redirects...
return redirect()->route('profile');
```

If the named route defines parameters, you may pass the parameters as the second argument to

the route function. The given parameters will automatically be inserted into

the generated URL