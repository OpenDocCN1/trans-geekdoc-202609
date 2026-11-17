server tweaking to be activated. Ultimately, when you have to deal with XML and validation, it falls short because <? has a special meaning in XML.

> The template already has access to a few pieces of data without the need of any variable setup in the action. Every template can call methods of the $sf_request, $sf_params, $sf_response, and $sf_user objects. They contain data related to the current request, request parameters, response, and session. You will soon learn how to use them efficiently.

# Linking to Another Action

You already know that there is a total decoupling between an action name and the URL used to call it. So if you create a link to update in a template as in Listing 4-8, it will only work with the default routing. If you later decide to change the way the URLs look, then you will need to review all templates to change the hyperlinks.

# Listing 4-8 - Hyperlinks, the Classic Way

```
<a href="/frontend_dev.php/content/update?name=anonymous">
I never say my name
</a>
```

To avoid this hassle, you should always use the link_to() helper to create hyperlinks to your application's actions. And if you only want to generate the URL part, the url_for() is the helper you're looking for.

A helper is a PHP function defined by symfony that is meant to be used within templates. It outputs some HTML code and is faster to use than writing the actual HTML code by yourself. Listing 4-9 demonstrates the use of the hyperlink helpers.

# Listing 4-9 - The link_to(), and url_for() Helpers

```
<p>Hello, world!</p>
<?php if ($hour >= 18): ?>
<?php Or should I say good evening? It is already <?php echo $hour ?>.</p>
<?php endif; ?>
<form method="post" action="<?php echo url_for('content/update') ?>">
<label for="name">What is your name?</label>
<input type="text" name="name" id="name" value="" />
<input type="submit" value="Ok" />
<?php echo link_to('I never say my name', 'content/
update?name=anonymous') ?>
</form>
```

The resulting HTML will be the same as previously, except that when you change your routing rules, all the templates will behave correctly and reformat the URLs accordingly.

Form manipulation deserves a whole chapter of its own, since symfony provides many tools to make it even easier. You will learn more about these helpers in Chapter 10.

The link_to() helper, like many other helpers, accepts another argument for special options and additional tag attributes. Listing 4-10 shows an example of an option argument and the resulting HTML. The option argument is either an associative array or a simple string showing key=value couples separated by blanks.

# Listing 4-10 - Most Helpers Accept an Option Argument

```
// Option argument as an associative array
<?php echo link_to('I never say my name', 'content/update?name=anonymous',
```