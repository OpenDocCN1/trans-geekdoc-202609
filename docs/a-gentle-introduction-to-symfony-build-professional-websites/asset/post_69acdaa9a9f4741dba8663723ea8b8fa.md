
```
# Project files
/cache/*
/log/*
/web/*_dev.php
/web/uploads/*

# SCM files
.arch-params
.bzr
_darcs
.git
.hg
.monotone
.svn
CVS
```

> The cache/ and log/ directories must not be synchronized with the development server, but they must at least exist in the production server. Create them by hand if the myproject/ project tree structure doesn't contain them.

## Managing a Production Application

The command that is used most often in production servers is cache:clear. You must run it every time you upgrade symfony or your project (for instance, after calling the project:deploy task), and every time you change the configuration in production.

```
$ php symfony cache:clear
```

> If the command-line interface is not available in your production server, you can still clear the cache manually by erasing the contents of the cache/ folder.

You can temporarily disable your application—for instance, when you need to upgrade a library or a large amount of data.

```
$ php symfony project:disable APPLICATION_NAME ENVIRONMENT_NAME
```

By default, a disabled application displays the sfConfig::get('sf_symfony_lib_dir')/exception/data/unavailable.php page, but if you create your own unavailable.php file in your project's config/ directory, symfony will use it instead.

The project:enable task reenables the application and clears the cache.

```
$ php symfony project:enable APPLICATION_NAME ENVIRONMENT_NAME
```

> project:disable currently has no effect if the check_lock parameter is not set to true in settings.yml.

## Displaying an unavailable page when clearing the cache

If you set the check_lock parameter to true in the settings.yml file, symfony will lock the application when the cache is being cleared, and all the requests arriving before the cache is finally cleared are then redirected to a page saying that the application is temporarily unavailable. If the cache is large, the delay to clear it may be longer than a few milliseconds, and if your site’s traffic is high, this is a recommended setting. This unavailable page is the same as the one displayed when you call the symfony disable task. The check_lock parameter is deactivated by default because it has a very slight negative impact on performance.

The project:clear-controllers task clears the web/ directory of all controllers other than the ones running in a production environment. If you do not include the development front controllers in the rsync_exclude.txt file, this command guarantees that a backdoor will not reveal the internals of your application.

```
$ php symfony project:clear-controllers
```

The permissions of the project files and directories can be broken if you use a checkout from an SVN repository. The project:permissions task fixes directory permissions, to change the log/ and cache/ permissions to 0777, for example (these directories need to be writable for the framework to work correctly).

```
$ php symfony project:permissions
```

## Summary

By combining PHP logs and symfony logs, you can monitor and debug your application easily. During development, the debug mode, the exceptions, and the web debug toolbar help you locate problems. You can even insert custom messages in the log files or in the toolbar for easier debugging.

The command-line interface provides a large number of tools that facilitate the management of your applications, during development and production phases. Among others, the data population, and synchronization tasks are great time-savers.

## Chapter 17
### Extending Symfony

Eventually, you will need to alter symfony’s behavior. Whether you need to modify the way a certain class behaves or add your own custom features, the moment will inevitably happen because all clients have specific requirements that no framework can forecast. Actually, this situation is so common that symfony provides a mechanism to extend existing classes at runtime, beyond simple class inheritance. You can even replace the core symfony classes by modifying the factories settings. Once you have built an extension, you can easily package it as a plug-in, so that it can be reused in other applications, or by other symfony users.

### Events

PHP does not support multiple inheritance, which means it is not possible to have a class extend more than one other class. Also it is not possible to add new methods to an existing class or override existing methods. To ease these two limitations and to make the framework truly extendable, symfony introduces an event system, inspired by the Cocoa notification center, and based on the Observer design pattern⁵⁸.

### Understanding Events

Some of the symfony classes “notify the dispatcher of an event” at various moments of their life. For instance, when the user changes their culture, the user object notifies that a change_culture event has occurred. This is like a shout in the project’s space, saying: “I’m doing that. Do whatever you want about it”.

You can decide to do something special when an event is fired. For instance, you could save the user culture to a database table each time the change_culture event occurs. In order to do so, you need to register an event listener, in other words you must declare a function that will be called when the event occurs. Listing 17-1 shows how to register a listener on the user’s change_culture event.

```
Listing 17-1 - Registering an Event Listener

$dispatcher->connect('user.change_culture', 'changeUserCulture');

function changeUserCulture(sfEvent $event)
{
    $user = $event->getSubject();
    $culture = $event['culture'];
}
```

All events and listener registrations are managed by a special object called the *event dispatcher*. This object is available from everywhere in symfony by way of the `ProjectConfiguration` instance, and most symfony objects offer a `getEventDispatcher()` method to get direct access to it. Using the dispatcher's `connect()` method, you can register any PHP callable (either a class method or a function) to be called when an event occurs. The first argument of `connect()` is the event identifier, which is a string composed of a namespace and a name. The second argument is a PHP callable.

Retrieving the event dispatcher from anywhere in the application:

`$dispatcher = ProjectConfiguration::getActive()->getEventDispatcher();`

Once the function is registered with the event dispatcher, it waits until the event is fired. The event dispatcher keeps a record of all event listeners, and knows which ones to call when an event occurs. When calling these methods or functions, the dispatcher passes them an `sfEvent` object as a parameter.

The event object stores information about the notified event. The event notifier can be retrieved thanks to the `getSubject()` method, and the event parameters are accessible by using the event object as an array (for example, `$event['culture']` can be used to retrieve the *culture* parameter passed by `sfUser` when notifying `user.change_culture`).

To wrap up, the event system allows you to add abilities to an existing class or modify its methods at runtime, without using inheritance.

### Notifying an Event Listener

Just like symfony classes notify that events have occurred, your own classes can offer runtime extensibility and notify of events at certain occasions. For instance, let's say that your application requests several third-party web services, and that you have written an `sfRestRequest` class to wrap the REST logic of these requests. A good idea would be to trigger an event each time this class makes a new request. This would make the addition of logging or caching capabilities easier in the future. Listing 17-2 shows the code you need to add to an existing `fetch()` method to make it notify an event listener.

### Listing 17-2 - Notifying an Event Listener

```
class sfRestRequest
{
    protected $dispatcher = null;

    public function __construct(sfEventDispatcher $dispatcher)
    {
        $this->dispatcher = $dispatcher;
    }

    /**
     * Makes a query to an external web service
     */
    public function fetch($uri, $parameters = array())
    {
        // Notify the dispatcher of the beginning of the fetch process
        $this->dispatcher->notify(new sfEvent($this,
```
