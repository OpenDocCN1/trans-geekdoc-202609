```
public function execute($filterChain)
{
    // Execute this filter only once
    if ($this->isFirstCall())
    {
        // Filters don't have direct access to the request and user objects.
        // You will need to use the context object to get them
        $request = $this->getContext()->getRequest();
        $user = $this->getContext()->getUser();

        if ($request->getCookie('MyWebSite'))
        {
            // sign in
            $user->setAuthenticated(true);
        }
    }

    // Execute next filter
    $filterChain->execute();
}
}
```

In some cases, instead of continuing the filter chain execution, you will need to forward to a specific action at the end of a filter. sfFilter doesn't have a forward() method, but sfController does, so you can simply do that by calling the following:

```
return $this->getContext()->getController()->forward('mymodule',
'myAction');
```

> The sfFilter class has an initialize() method, executed when the filter object is created. You can override it in your custom filter if you need to deal with filter parameters (defined in filters.yml, as described next) in your own way.

# Filter Activation and Parameters

Creating a filter file is not enough to activate it. You need to add your filter to the filter chain, and for that, you must declare the filter class in the filters.yml, located in the application or in the module config/ directory, as shown in Listing 6-30.

Listing 6-30 - Sample Filter Activation File, Saved in apps/frontend/config/filters.yml

```
rendering: ~
security: ~

remember:
    # Filters need a unique name
    class: rememberFilter
    param:
        cookie_name: MyWebSite
        condition: %APP_ENABLE_REMEMBER_ME%

cache: ~
execution: ~
```

When activated, the filter is executed for each request. The filter configuration file can contain one or more parameter definitions under the param key. The filter class has the