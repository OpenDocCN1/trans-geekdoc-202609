
- A pattern to be matched (url key)
- An array of request parameter values (param key)

Patterns can contain wildcards (represented by an asterisk, *) and named wildcards (starting with a colon, :). A match to a named wildcard becomes a request parameter value. For instance, the default rule defined in Listing 9-15 will match any URL like /foo/bar, and set the module parameter to foo and the action parameter to bar.

Named wildcards can be separated by a slash or a dot, so you can write a pattern like:

```
my_rule:
  url:   /foo/:bar.:format
  param: { module: mymodule, action: myaction }
```

That way, an external URL like 'foo/12.xml' will match my_rule and execute mymodule/myaction with two parameters: $bar=12 and $format=xml. You can add more separators by changing the segment_separators parameter value in the sfPatternRouting factory configuration (see chapter 19).

The routing system parses the routing.yml file from the top to the bottom and stops at the first match. This is why you must add your own rules on top of the default ones. For instance, the URL /foo/123 matches both of the rules defined in Listing 9-16, but symfony first tests my_rule:, and as that rule matches, it doesn't even test the default: one. The request is handled by the mymodule/myaction action with bar set to 123 (and not by the foo/123 action).

### Listing 9-16 - Rules Are Parsed Top to Bottom

```
my_rule:
  url: /foo/:bar
  param: { module: mymodule, action: myaction }

# default rules
default:
  url:  /:module/:action/*
```

When a new action is created, it does not imply that you must create a routing rule for it. If the default module/action pattern suits you, then forget about the routing.yml file. If, however, you want to customize the action's external URL, add a new rule above the default one.

Listing 9-17 shows the process of changing the external URL format for an article/read action.

### Listing 9-17 - Changing the External URL Format for an article/read Action

```
<?php echo url_for('article/read?id=123') ?>
=> /article/read/id/123   // Default formatting

// To change it to /article/123, add a new rule at the beginning
// of your routing.yml
article_by_id:
  url:   /article/:id
  param: { module: article, action: read }
```

The problem is that the article_by_id rule in Listing 9-17 breaks the default routing for all the other actions of the article module. In fact, a URL like article/delete will match this rule instead of the default one, and call the read action with id set to delete instead of the delete action. To get around this difficulty, you must add a pattern constraint so that the article_by_id rule matches only URLs where the id wildcard is an integer.

## Pattern Constraints

When a URL can match more than one rule, you must refine the rules by adding constraints, or requirements, to the pattern. A requirement is a set of regular expressions that must be matched by the wildcards for the rule to match.

For instance, to modify the article_by_id rule so that it matches only URLs where the id parameter is an integer, add a line to the rule, as shown in Listing 9-18.

### Listing 9-18 - Adding a Requirement to a Routing Rule

```
article_by_id:
  url: /article/:id
  param: { module: article, action: read }
  requirements: { id: \d+ }
```

Now an article/delete URL can't match the article_by_id rule anymore, because the 'delete' string doesn't satisfy the requirements. Therefore, the routing system will keep on looking for a match in the following rules and finally find the default rule.

## Permalinks

A good security guideline for routing is to hide primary keys and replace them with significant strings as much as possible. What if you wanted to give access to articles from their title rather than from their ID? It would make external URLs look like this:

```
http://www.example.com/article/Finance_in_France
```

To that extent, you need to create a new permalink action, which will use a slug parameter instead of an id one, and add a new rule for it:

```
article_by_id:
  url: /article/:id
  param: { module: article, action: read }
  requirements: { id: \d+ }
```

```
article_by_slug:
  url: /article/:slug
  param: { module: article, action: permalink }
```

The permalink action needs to determine the requested article from its title, so your model must provide an appropriate method.

```
public function executePermalink($request)
{
 $article = ArticlePeer::retrieveBySlug($request->getParameter('slug'));
 $this->forward404Unless($article); // Display 404 if no article matches slug
 $this->article = $article; // Pass the object to the template
}
```

You also need to replace the links to the read action in your templates with links to the permalink one, to enable correct formatting of internal URLs.

```
// Replace
<?php echo link_to('my article', 'article/read?id='.$article->getId()) ?>
```

```
// With
<?php echo link_to('my article', 'article/permalink?slug='.$article->getSlug()) ?>
```

Thanks to the requirements line, an external URL like /article/Finance_in_France matches the article_by_slug rule, even though the article_by_id rule appears first.

Note that as articles will be retrieved by slug, you should add an index to the slug column in the Article model description to optimize database performance.

## Setting Default Values

You can give named wildcards a default value to make a rule work, even if the parameter is not defined. Set default values in the param: array.

For instance, the article_by_id rule doesn't match if the id parameter is not set. You can force it, as shown in Listing 9-19.

### Listing 9-19 - Setting a Default Value for a Wildcard

```
article_by_id:
  url: /article/:id
  param: { module: article, action: read, id: 1 }
```

The default parameters don't need to be wildcards found in the pattern. In Listing 9-20, the display parameter takes the value true, even if it is not present in the URL.

### Listing 9-20 - Setting a Default Value for a Request Parameter

```
article_by_id:
  url: /article/:id
  param: { module: article, action: read, id: 1, display: true }
```

If you look carefully, you can see that article and read are also default values for module and action variables not found in the pattern.

> You can define a default parameter for all the routing rules by calling the sfRouting::setDefaultParameter() method. For instance, if you want all the rules to have a theme parameter set to default by default, add $this->context->getRouting()->setDefaultParameter('theme', 'default'); to one of your global filters.

## Speeding Up Routing by Using the Rule Name

The link helpers accept a rule label instead of a module/action pair if the rule label is preceded by an 'at' sign (@), as shown in Listing 9-21.

### Listing 9-21 - Using the Rule Label Instead of the Module/Action

```
<?php echo link_to('my article', 'article/read?id='.$article->getId()) ?>
// can also be written as
<?php echo link_to('my article', '@article_by_id?id='.$article->getId()) ?>
// or the fastest one (does not need extra parsing):
<?php echo link_to('my article', 'article_by_id', array('id' => $article->getId())) ?>
```

There are pros and cons to this trick. The advantages are as follows:

- The formatting of internal URIs is done faster, since symfony doesn't have to browse all the rules to find the one that matches the link. In a page with a great number of routed hyperlinks, the boost will be noticeable if you use rule labels instead of module/action pairs.

- Using the rule label helps to abstract the logic behind an action. If you decide to change an action name but keep the URL, a simple change in the routing.yml file will suffice. All of the link_to() calls will still work without further change.

- The logic of the call is more apparent with a rule name. Even if your modules and actions have explicit names, it is often better to call @display_article_by_slug than article/display.

- You know exactly which actions are enabled by reading the routing.yml file

On the other hand, a disadvantage is that adding new hyperlinks becomes less self-evident, since you always need to refer to the routing.yml file to find out which label is to be used for an action. And in a big project, you will certainly end with a lot of routing rules, making a bit hard to maintain them. In this case, you should package your application in several plugins, each one defining a limited set of features.

However, the experience states that using routing rules is the best choice in the long run.
