# # Permalinks

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
 $this->forward404Unless($article); // Display 404 if no article
 matches slug
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

# # Setting Default Values

You can give named wildcards a default value to make a rule work, even if the parameter is not defined. Set default values in the param: array.

For instance, the article_by_id rule doesn't match if the id parameter is not set. You can force it, as shown in Listing 9-19.

Listing 9-19 - Setting a Default Value for a Wildcard