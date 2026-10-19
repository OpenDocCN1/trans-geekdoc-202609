```
\Illuminate\Routing\Middleware\SubstituteBindings::class,
\Illuminate\Auth\Middleware\Authorize::class,
];
```

# Middleware Parameters

Middleware can also receive additional parameters. For example, if your application needs toverify that the authenticated user has a given "role" before performing a given action, you could

create an EnsureUserHasRole middleware that receives a role name as an additional argument.

Additional middleware parameters will be passed to the middleware after the $next argument: