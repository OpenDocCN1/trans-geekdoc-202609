As a matter of fact, the variables in the template are not of the type you might expect. The output escaping system “decorates” them and transforms them into special objects:

```
<?php echo get_class($test_array) ?>
=> sfOutputEscaperArrayDecorator
<?php echo get_class($test_object) ?>
=> sfOutputEscaperObjectDecorator
```

This explains why some usual PHP functions (like array_shift(), print_r(), and so on) don’t work on escaped arrays anymore. But they can still be accessed using [], be traversed using foreach, and they give back the right result with count(). And in templates, the data should be read-only anyway, so most access will be through the methods that do work.

You still have a way to retrieve the raw data through the $sf_data object. In addition, methods of escaped objects are altered to accept an additional parameter: an escaping method. So you can choose an alternative escaping method each time you display a variable in a template, or opt for the ESC_RAW helper to deactivate escaping. See Listing 7-40 for an example.

# Listing 7-40 - Methods of Escaped Objects Accept an Additional Parameter

```
<?php echo $test_object->testSpecialChars('&') ?>
=> &lt;&amp;&gt;
// The three following lines return the same value
<?php echo $test_object->testSpecialChars('&', ESC_RAW) ?>
<?php echo $sf_data->getRaw('test_object')->testSpecialChars('&') ?>
<?php echo $sf_data->get('test_object', ESC_RAW)->testSpecialChars('&') ?>
=> <&>
```

If you deal with objects in your templates, you will use the additional parameter trick a lot, since it is the fastest way to get raw data on a method call.

> The usual symfony variables are also escaped when you turn on output escaping. So be aware that $sf_user, $sf_request, $sf_param, and $sf_context still work, but their methods return escaped data, unless you add ESC_RAW as a final argument to their method calls.

> Even if XSS is one of the most common exploit of websites, this is not the only one. CSRF is also very popular and symfony provides automatic forms protection. You will discover how this security protection works in the chapter 10.

# Summary

All kinds of tools are available to manipulate the presentation layer. The templates are built in seconds, thanks to helpers. The layouts, partials, and components bring both modularity and reusability. The view configuration takes advantage of the speed of YAML to handle (mostly) page headers. The configuration cascade exempts you from defining every setting for each view. For every modification of the presentation that depends on dynamic data, the action has access to the sfResponse object. And the view is secure from XSS attacks, thanks to the output escaping system.