```
<p>
Hello, <?php echo $sf_user->getAttribute('nickname') ?>
</p>
```

# Flash Attributes

A recurrent problem with user attributes is the cleaning of the user session once the attribute is not needed anymore. For instance, you may want to display a confirmation after updating data via a form. As the form-handling action makes a redirect, the only way to pass information from this action to the action it redirects to is to store the information in the user session. But once the confirmation message is displayed, you need to clear the attribute; otherwise, it will remain in the session until it expires.

The flash attribute is an ephemeral attribute that you can define and forget, knowing that it will disappear after the very next request and leave the user session clean for the future. In your action, define the flash attribute like this:

```
Listing 6-29
$this->getUser()->setFlash('notice', $value);
```

The template will be rendered and delivered to the user, who will then make a new request to another action. In this second action, just get the value of the flash attribute like this:

```
Listing 6-30
$value = $this->getUser()->getFlash('notice');
```

Then forget about it. After delivering this second page, the notice flash attribute will be flushed. And even if you don't require it during this second action, the flash will disappear from the session anyway.

If you need to access a flash attribute from a template, use the $sf_user object:

```
Listing 6-31
<?php if ($sf_user->hasFlash('notice')): ?>
<?php echo $sf_user->getFlash('notice') ?>
<?php endif; ?>
```

or just:

```
Listing 6-32
<?php echo $sf_user->getFlash('notice') ?>
```

Flash attributes are a clean way of passing information to the very next request.

# Session Management

Symfony's session-handling feature completely masks the client and server storage of the session IDs to the developer. However, if you want to modify the default behaviors of the session-management mechanisms, it is still possible. This is mostly for advanced users.

On the client side, sessions are handled by cookies. The symfony session cookie is called symfony, but you can change its name by editing the factories.yml configuration file, as shown in Listing 6-17.

Listing 6-17 - Changing the Session Cookie Name, in apps/frontend/config/factories.yml

```
Listing 6-33
all:
storage:
class: sfSessionStorage
param:
session_name: my_cookie_name
```