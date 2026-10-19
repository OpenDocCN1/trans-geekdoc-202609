```
if (App::environment('local')) {
    // The environment is local
}

if (App::environment(['local', 'staging'])) {
    // The environment is either local OR staging...
}
```

{tip} The current application environment detection can be overridden by defining a serverlevel APP_ENV environment variable.

# Accessing Configuration Values

You may effortlessly get to your arrangement values utilizing the worldwide config assistant capacity from anyplace in your application. The arrangement values might got to utilize "spot" linguistic structure, which incorporates the name of the document and choice you wish to get to. A default worth may likewise be determined also, will be returned in the event that the arrangement choice doesn't exist:

```
$value = config('app.timezone');

// Retrieve a default value if the configuration value does not exist...
$value = config('app.timezone', 'Asia/Seoul');
```

To set configuration values at runtime, pass an array to the config helper: