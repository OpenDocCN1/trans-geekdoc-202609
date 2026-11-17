
## Complex Credentials

The YAML syntax used in the security.yml file allows you to restrict access to users having a combination of credentials, using either AND-type or OR-type associations. With such a combination, you can build a complex workflow and user privilege management system—for instance, a content management system (CMS) back-office accessible only to users with the admin credential, where articles can be edited only by users with the editor credential and published only by the ones with the publisher credential. Listing 6-25 shows this example.

### Listing 6-25 - Credentials Combination Syntax

```
Listing 6-25 - Credentials Combination Syntax

editArticle:
  credentials: [ admin, editor ]     # admin AND editor

publishArticle:
  credentials: [ admin, publisher ]  # admin AND publisher

userManagement:
  credentials: [ [ admin, superuser ]]  # admin OR superuser
```

Each time you add a new level of square brackets, the logic swaps between AND and OR. So you can create very complex credential combinations, such as this:

```
credentials: [[root, [supplier, [owner, quasiowner]]], accounts]]
  # root OR (supplier AND (owner OR quasiowner)) OR accounts
```

## Filters

The security process can be understood as a filter by which all requests must pass before executing the action. According to some tests executed in the filter, the processing of the request is modified—for instance, by changing the action executed (default/secure instead of the requested action in the case of the security filter). Symfony extends this idea to filter classes. You can specify any number of filter classes to be executed before the action execution or before the response rendering, and do this for every request. You can see filters as a way to package some code, similar to preExecute() and postExecute(), but at a higher level (for a whole application instead of for a whole module).

## The Filter Chain

Symfony actually sees the processing of a request as a chain of filters. When a request is received by the framework, the first filter (which is always the sfRenderingFilter) is executed. At some point, it calls the next filter in the chain, then the next, and so on. When the last filter (which is always sfExecutionFilter) is executed, the previous filter can finish, and so on back to the rendering filter. Figure 6-3 illustrates this idea with a sequence diagram, using an artificially small filter chain (the real one contains more filters).

### Figure 6-3 - Sample filter chain

![](img/0f886a7f4cbcc3939be96e985ca35ff4_91_0.png)

This process justifies the structure of the filter classes. They all extend the sfFilter class, and contain one execute() method, expecting a $filterChain object as parameter. Somewhere in this method, the filter passes to the next filter in the chain by calling $filterChain->execute(). See Listing 6-26 for an example. So basically, filters are divided into two parts:

- The code before the call to $filterChain->execute() executes before the action execution.
- The code after the call to $filterChain->execute() executes after the action execution and before the rendering.

### Listing 6-26 - Filter Class Structure

```php
class myFilter extends sfFilter
{
  public function execute($filterChain)
  {
    // Code to execute before the action execution
    ...

    // Execute next filter in the chain
    $filterChain->execute();

    // Code to execute after the action execution, before the rendering
    ...
  }
}
```

The default filter chain is defined in an application configuration file called filters.yml, and is shown in Listing 6-27. This file lists the filters that are to be executed for every request.

### Listing 6-27 - Default Filter Chain, in frontend/config/filters.yml

```yaml
rendering: ~
security: ~

# Generally, you will want to insert your own filters here

cache: ~
execution: ~
```

These declarations have no parameter (the tilde character, ~, means “null” in YAML), because they inherit the parameters defined in the symfony core. In the core, symfony defines class and param settings for each of these filters. For instance, Listing 6-28 shows the default parameters for the rendering filter.

### Listing 6-28 - Default Parameters of the rendering Filter, in sfConfig::get('sf_symfony_lib_dir')/config/config/filters.yml

```yaml
rendering:
  class: sfRenderingFilter   # Filter class
  param:                     # Filter parameters
    type: rendering
```

By leaving the empty value (~) in the application filters.yml, you tell symfony to apply the filter with the default settings defined in the core.

You can customize the filter chain in various ways:

- Disable some filters from the chain by adding an enabled: false parameter. For instance, to disable the security filter, write:

```
security:
  enabled: false
```

- Do not remove an entry from the filters.yml to disable a filter; symfony would throw an exception in this case.

- Add your own declarations somewhere in the chain (usually after the security filter) to add a custom filter (as discussed in the next section). Be aware that the rendering filter must be the first entry, and the execution filter must be the last entry of the filter chain.

- Override the default class and parameters of the default filters (notably to modify the security system and use your own security filter).

## Building Your Own Filter

It is pretty simple to build a filter. Create a class definition similar to the one shown in Listing 6-26, and place it in one of the project's lib/ folders to take advantage of the autoloading feature.

As an action can forward or redirect to another action and consequently relaunch the full chain of filters, you might want to restrict the execution of your own filters to the first action call of the request. The isFirstCall() method of the sfFilter class returns a Boolean for this purpose. This call only makes sense before the action execution.

These concepts are clearer with an example. Listing 6-29 shows a filter used to auto-log users with a specific MyWebSite cookie, which is supposedly created by the login action. It is a rudimentary but working way to implement the “remember me” feature offered in login forms.

### Listing 6-29 - Sample Filter Class File, Saved in apps/frontend/lib/rememberFilter.class.php

```php
class rememberFilter extends sfFilter
{
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

## Filter Activation and Parameters

Creating a filter file is not enough to activate it. You need to add your filter to the filter chain, and for that, you must declare the filter class in the filters.yml, located in the application or in the module config/ directory, as shown in Listing 6-30.

### Listing 6-30 - Sample Filter Activation File, Saved in apps/frontend/config/filters.yml

```yaml
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
