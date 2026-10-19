```
return Illuminate\Support\Facades\View::make('profile');

return view('profile');
```

There is absolutely no practical difference between facades and helper functions. When using helper functions, you may still test them exactly as you would the corresponding facade. For example, given the following route:

```
Route::get('/cache', function () {
    return cache('key');
});
```

Under the hood, the cache helper is going to call the get method on the class underlying the Cache facade. So, even though we are using the helper function, we can write the following test to verify that the method was called with the argument we expected: