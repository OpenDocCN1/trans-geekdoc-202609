
## Customizing the Spool with any Criteria

The previous example uses a standard message header, the priority. But if you want to use any criteria, or if you don't want to alter the sent message, you can also store the criteria as a custom header, and remove it before sending the email.

First, add a custom header to the message to be sent:

Listing 11-36
```php
public function executeIndex()
{
    $message = $this->getMailer()
        ->compose('john@doe.com', 'foo@example.com', 'Subject', 'Body')
        ;

    $message->getHeaders()->addTextHeader('X-Queue-Criteria', 'foo');

    $this->getMailer()->send($message);
}
```

Then, retrieve the value from this header when storing the message in the queue, and remove it immediately:

Listing 11-37
```php
public function setMessage($message)
{
    $msg = unserialize($message);

    $headers = $msg->getHeaders();
    $criteria = $headers->get('X-Queue-Criteria')->getFieldBody();
    $this->setCriteria($criteria);
    $headers->remove('X-Queue-Criteria');

    parent::setMessage($message);
}
```

## Chapter 12 Caching

One of the ways to speed up an application is to store chunks of generated HTML code, or even full pages, for future requests. This technique is known as caching, and it can be managed on the server side and on the client side.

Symfony offers a flexible server-caching system. It allows saving the full response, the result of an action, a partial, or a template fragment into a file, through a very intuitive setup based on YAML files. When the underlying data changes, you can easily clear selective parts of the cache with the command line or special action methods. Symfony also provides an easy way to control the client-side cache through HTTP 1.1 headers. This chapter deals with all these subjects, and gives you a few tips on monitoring the improvements that caching can bring to your applications.

## Caching the Response

The principle of HTML caching is simple: Part or all of the HTML code that is sent to a user upon a request can be reused for a similar request. This HTML code is stored in a special place (the cache/ folder in symfony), where the front controller will look for it before executing an action. If a cached version is found, it is sent without executing the action, thus greatly speeding up the process. If no cached version is found, the action is executed, and its result (the view) is stored in the cache folder for future requests.

As all the pages may contain dynamic information, the HTML cache is disabled by default. It is up to the site administrator to enable it in order to improve performance.

Symfony handles three different types of HTML caching:

- Cache of an action (with or without the layout)
- Cache of a partial or a component
- Cache of a template fragment

The first two types are handled with YAML configuration files. Template fragment caching is managed by calls to helper functions in the template.

## Global Cache Settings

For each application of a project, the HTML cache mechanism can be enabled or disabled (the default), per environment, in the cache setting of the settings.yml file. Listing 12-1 demonstrates enabling the ability to cache. Note this will not cause anything to be cached; to do so you must enable caching in each module/action (see below).

Listing 12-1 - Activating the Cache, in frontend/config/settings.yml

```
dev:
.settings:
cache: true
```

## Caching an Action

Actions displaying static information (not depending on database or session-dependent data) or actions reading information from a database but without modifying it (typically, GET requests) are often ideal for caching. Figure 12-1 shows which elements of the page are cached in this case: either the action result (its template) or the action result together with the layout.

## Figure 12-1 - Caching an action

![](img/0f886a7f4cbcc3939be96e985ca35ff4_201_0.png)

For instance, consider a user/list action that returns the list of all users of a website. Unless a user is modified, added, or removed (and this matter will be discussed later in the “Removing Items from the Cache” section), this list always displays the same information, so it is a good candidate for caching.

Cache activation and settings, action by action, are defined in a cache.yml file located in the module config/ directory. See Listing 12-2 for an example.

## Listing 12-2 - Activating the Cache for an Action, in frontend/modules/user/config/cache.yml

```
list:
enabled: true
with_layout: false # Default value
lifetime: 86400 # Default value
```

This configuration stipulates that the cache is on for the list action, and that the layout will not be cached with the action (which is the default behavior). It means that even if a cached version of the action exists, the layout (together with its partials and components) is still executed. If the with_layout setting is set to true, the layout is cached with the action and not executed again.

To test the cache settings, call the action in the development environment from your browser.

## Listing 12-3

```
http://myapp.example.com/frontend_dev.php/user/list
```

You will notice a border around the action area in the page. The first time, the area has a blue header, showing that it did not come from the cache. Refresh the page, and the action area will have a yellow header, showing that it did come from the cache (with a notable boost in response time). You will learn more about the ways to test and monitor caching later in this chapter.

Slots are part of the template, and caching an action will also store the value of the slots defined in this action's template. So the cache works natively for slots.

The caching system also works for pages with arguments. The user module may have, for instance, a show action that expects an id argument to display the details of a user. Modify the cache.yml file to enable the cache for this action as well, as shown in Listing 12-3.

In order to organize your cache.yml, you can regroup the settings for all the actions of a module under the all: key, also shown in Listing 12-3.

## Listing 12-3 - A Full cache.yml Example, in frontend/modules/user/config/cache.yml

```
list:
  enabled:  true
show:
  enabled:  true

all:
  with_layout:  false  # Default value
  lifetime:   86400    # Default value
```

Now, every call to the user/show action with a different id argument creates a new record in the cache. So the cache for this:

```
http://myapp.example.com/user/show/id/12
```

will be different than the cache for this:

```
http://myapp.example.com/user/show/id/25
```

> Actions called with a POST method or with GET parameters are not cached.

The with_layout setting deserves a few more words. It actually determines what kind of data is stored in the cache. For the cache without layout, only the result of the template execution and the action variables are stored in the cache. For the cache with layout, the whole response object is stored. This means that the cache with layout is much faster than the cache without it.

If you can functionally afford it (that is, if the layout doesn't rely on session-dependent data), you should opt for the cache with layout. Unfortunately, the layout often contains some dynamic elements (for instance, the name of the user who is connected), so action cache without layout is the most common configuration. However, RSS feeds, pop-ups, and pages that don't depend on cookies can be cached with their layout.

## Caching a Partial or Component

Chapter 7 explained how to reuse code fragments across several templates, using the include_partial() helper. A partial is as easy to cache as an action, and its cache activation follows the same rules, as shown in Figure 12-2.

## Figure 12-2 - Caching a partial or component

## Component Cache

For instance, Listing 12-4 shows how to edit the cache.yml file to enable the cache on a _my_partial.php partial located in the user module. Note that the with_layout setting doesn't make sense in this case.

Listing 12-4 - Caching a Partial, in frontend/modules/user/config/cache.yml

```
__my_partial:
  enabled: true
  list:
    enabled: true
    ...
```

Now all the templates using this partial won't actually execute the PHP code of the partial, but will use the cached version instead.

Listing 12-8

```php
<?php include_partial('user/my_partial') ?>
```

Just as for actions, partial caching is also relevant when the result of the partial depends on parameters. The cache system will store as many versions of a template as there are different values of parameters.

Listing 12-9

```php
<?php include_partial('user/my_other_partial', array('foo' => 'bar')) ?>
```

> The action cache is more powerful than the partial cache, since when an action is cached, the template is not even executed; if the template contains calls to partials, these calls are not performed. Therefore, partial caching is useful only if you don't use action caching in the calling action or for partials included in the layout.

A little reminder from Chapter 7: A component is a light action put on top of a partial. This inclusion type is very similar to partials, and support caching in the same way. For instance, if your global layout includes a component called day with include_component('general/day') in order to show the current date, set the cache.yml file of the general module as follows to enable the cache on this component:

Listing 12-10

```
_day:
  enabled: true
```

When caching a component or a partial, you must decide whether to store a single version for all calling templates or a version for each template. By default, a component is stored independently of the template that calls it. But contextual components, such as a component that displays a different sidebar with each action, should be stored as many times as there are templates calling it. The caching system can handle this case, provided that you set the contextual parameter to true, as follows:
