
## Other Speedup tactics

In addition to the HTML cache, symfony has two other cache mechanisms, which are completely automated and transparent to the developer. In the production environment, the configuration and the template translations are cached in files stored in the myproject/cache/config/ and myproject/cache/i18n/ directories without any intervention.

PHP accelerators (eAccelerator, APC, XCache, and so on), also called opcode caching modules, increase performance of PHP scripts by caching them in a compiled state, so that the overhead of code parsing and compiling is almost completely eliminated. This is particularly effective for the ORMs classes, which contain a great amount of code. These accelerators are compatible with symfony and can easily triple the speed of an application. They are recommended in production environments for any symfony application with a large audience.

With a PHP accelerator, you can manually store persistent data in memory, to avoid doing the same processing for each request, with the sfAPCCache class if use APC for instance. And if you want to cache the result of a CPU-intensive function, you will probably use the sfFunctionCache object. Refer to Chapter 18 for more information about these mechanisms.

## Removing Items from the Cache

If the scripts or the data of your application change, the cache will contain outdated information. To avoid incoherence and bugs, you can remove parts of the cache in many different ways, according to your needs.

### Clearing the Entire Cache

The cache:clear task of the symfony command line erases the cache (HTML, configuration, routing, and i18n cache). You can pass it arguments to erase only a subset of the cache, as shown in Listing 12-8. Remember to call it only from the root of a symfony project.

Listing 12-8 - Clearing the Cache

```
// Erase the whole cache
$ php symfony cache:clear

// Short syntax
$ php symfony cc

// Erase only the cache of the frontend application
$ php symfony cache:clear --app=frontend

// Erase only the HTML cache of the frontend application
$ php symfony cache:clear --app=frontend --type=template

// Erase only the configuration cache of the frontend application
// The built-in types are config, i18n, routing, and template.
$ php symfony cache:clear --app=frontend --type=config

// Erase only the configuration cache of the frontend application and the prod environment
$ php symfony cache:clear --app=frontend --type=config --env=prod
```

### Clearing Selective Parts of the Cache

When the database is updated, the cache of the actions related to the modified data must be cleared. You could clear the whole cache, but that would be a waste for all the existing cached actions that are unrelated to the model change. This is where the remove() method of the sfViewCacheManager object applies. It expects an internal URI as argument (the same kind of argument you would provide to a link_to()), and removes the related action cache.

For instance, imagine that the update action of the user module modifies the columns of a User object. The cached versions of the list and show actions need to be cleared, or else the old versions, which contain erroneous data, are displayed. To handle this, use the remove() method, as shown in Listing 12-9.

Listing 12-9 - Clearing the Cache for a Given Action, in modules/user/actions/actions.class.php

```
public function executeUpdate($request)
{
  // Update a user
  $user_id = $request->getParameter('id');
  $user = UserPeer::retrieveByPk($user_id);
  $this->forward404Unless($user);
  $user->setName($request->getParameter('name'));
  ...
  $user->save();

  // Clear the cache for actions related to this user
  $cacheManager = $this->getContext()->getViewCacheManager();
  $cacheManager->remove('user/list');
  $cacheManager->remove('user/show?id=' . $user_id);
  ...
}
```

Removing cached partials and components is a little trickier. As you can pass them any type of parameter (including objects), it is almost impossible to identify their cached version afterwards. Let's focus on partials, as the explanation is the same for the other template components. Symfony identifies a cached partial with a special prefix (sf_cache_partial), the name of the module, and the name of the partial, plus a hash of all the parameters used to call it, as follows:

```
// A partial called by
<?php include_partial('user/my_partial', array('user' => $user)) ?>

// Is identified in the cache as
@sf_cache_partial?module=user&action=_my_partial
&sf_cache_key=bf41dd99c8d459f3574a5da244626dcc8
```

In theory, you could remove a cached partial with the remove() method if you knew the value of the parameters hash used to identify it, but this is very impracticable. Fortunately, if you add a sf_cache_key parameter to the include_partial() helper call, you can identify the partial in the cache with something that you know. As you can see in Listing 12-10, clearing a single cached partial—for instance, to clean up the cache from the partial based on a modified User—becomes easy.

Listing 12-10 - Clearing Partials from the Cache

```
<?php include_partial('user/my_partial', array(
  'user'   => $user,
  'sf_cache_key' => $user->getId()
) ?>
```

```
// Is identified in the cache as
@sf_cache_partial?module=user&action=_my_partial&sf_cache_key=12
```

```
// Clear _my_partial for a specific user in the cache with
$cacheManager->remove('@sf_cache_partial?module=user&action=_my_partial&sf_cache_key=' . $user->getId());
```

To clear template fragments, use the same remove() method. The key identifying the fragment in the cache is composed of the same sf_cache_partial prefix, the module name, the action name, and the sf_cache_key (the unique name of the cache fragment included by the cache() helper). Listing 12-11 shows an example.

Listing 12-11 - Clearing Template Fragments from the Cache

```
<!-- Cached code -->
<?php if (!cache('users')): ?>
    ... // Whatever
    <?php cache_save() ?>
<?php endif; ?>
```

```
// Is identified in the cache as
@sf_cache_partial?module=user&action=list&sf_cache_key=users
```

```
// Clear it with
$cacheManager->remove('@sf_cache_partial?module=user&action=list&sf_cache_key=users');
```

## Selective Cache Clearing Can damage your Brain

The trickiest part of the cache-clearing job is to determine which actions are influenced by a data update.

For instance, imagine that the current application has a publication module where publications are listed (list action) and described (show action), along with the details of their author (an instance of the User class). Modifying one User record will affect all the descriptions of the user's publications and the list of publications. This means that you need to add to the update action of the user module, something like this:

```
$c = new Criteria();
$c->add(PublicationPeer::AUTHOR_ID, $request->getParameter('id'));
$publications = PublicationPeer::doSelect($c);

$cacheManager = sfContext::getInstance()->getViewCacheManager();
foreach ($publications as $publication)
{
  $cacheManager->remove('publication/show?id='.$publication->getId());
}
$cacheManager->remove('publication/list');
```

When you start using the HTML cache, you need to keep a clear view of the dependencies between the model and the actions, so that new errors don't appear because of a misunderstood relationship. Keep in mind that all the actions that modify the model should probably contain a bunch of calls to the remove() method if the HTML cache is used somewhere in the application.

And, if you don't want to damage your brain with too difficult an analysis, you can always clear the whole cache each time you update the database...

## Clearing several cache parts at once

The remove() method accepts keys with wildcards. It allows you to remove several cache parts with a single call. You can do for instance:

```
$cacheManager->remove('user/show?id=*'); // Remove for all user records
```

Another good example is with applications handling several languages, where the language code appears in all URLs. The URL to a user profile page should look like this:

```
http://www.myapp.com/en/user/show/id/12
```

To remove the cached profile of the user having an id of 12 in all languages, you can simply call:

```
$cache->remove('user/show?sf_culture=*&id=12');
```

This also works for partials:

```
$cacheManager->remove('@sf_cache_partial?module=user&action=_my_partial&sf_cache_key=*'); // Remove for all keys
```

The remove() method accepts two additional parameters, allowing you to define which hosts and vary headers you want to clear the cache for. This is because symfony keeps one cache version for each host and vary headers, so that two applications sharing the same code base but not the same hostname use different caches. This can be of great use, for instance, when
