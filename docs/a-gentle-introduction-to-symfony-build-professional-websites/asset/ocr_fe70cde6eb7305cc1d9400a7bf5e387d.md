# URLs are part of the response

Symfony contains a routing system that allows you to have a complete separation between the actual action name and the form of the URL needed to call it. This allows for custom formatting of the URL as if it were part of the response. You are no longer limited by the file structure nor by the request parameters; the URL for an action can look like the phrase you want. For instance, the call to the index action of a module called article usually looks like this:

```
http://localhost/frontend_dev.php/article/index?id=123
```

This URL retrieves a given article from a database. In this example, it retrieves an article (with id=123) in the Europe section that specifically discusses finance in France. But the URL can be written in a completely different way with a simple change in the routing.yml configuration file:

```
http://localhost/articles/europe/france/finance.html
```

Not only is the resulting URL search engine-friendly, it is also significant for the user, who can then use the address bar as a pseudo command line to do custom queries, as in the following:

```
http://localhost/articles/tagged/finance+france+euro
```

Symfony knows how to parse and generate smart URLs for the user. The routing system automatically peels the request parameters from a smart URL and makes them available to the action. It also formats the hyperlinks included in the response so that they look “smart”. You will learn more about this feature in Chapter 9.

Overall, this means that the way you name the actions should not be influenced by the way the URL used to call them should look, but by the actions’ functions in the application. An action name explains what the action actually does, and it is often a verb in the infinitive form (like show, list, edit, and so on). Action names can be made totally invisible to the end user, so don’t hesitate to use explicit action names (like listByName or showWithComments). You will economize on code comments to explain your action function, plus the code will be much easier to read.

# Adding a Template

The action expects a template to render itself. A template is a file located in the templates/ directory of a module, named by the action and the action termination. The default action termination is a “success,” so the template file to be created for the show action is to be called showSuccess.php.

Templates are supposed to contain only presentational code, so keep as little PHP code in them as possible. As a matter of fact, a page displaying “Hello, world!” can have a template as simple as the one in Listing 4-3.

# *Listing 4-3 - The content/templates/showSuccess.php Template*

```
<p>Hello, world!</p>
```

If you need to execute some PHP code in the template, you should avoid using the usual PHP syntax, as shown in Listing 4-4. Instead, write your templates using the PHP alternative syntax, as shown in Listing 4-5, to keep the code understandable for non-PHP programmers. Not only will the final code be correctly indented, but it will also help you keep the complex PHP code in the action, because only control statements (if, foreach, while, and so on) have an alternative syntax.