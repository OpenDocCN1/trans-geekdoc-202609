+   - $comment->getArticle(): To get the related Article object
+   - $comment->getArticleId(): To get the ID of the related Article object
+   - $comment->setArticle($article): To define the related Article object
+   - $comment->setArticleId($id): To define the related Article object from an ID
+   - $article->getComments(): To get the related Comment objects

The getArticleId() and setArticleId() methods show that you can consider the article_id column as a regular column and set the relationships by hand, but they are not very interesting. The benefit of the object-oriented approach is much more apparent in the three other methods. Listing 8-9 shows how to use the generated setters.

# Listing 8-9 - Foreign Keys Are Translated into a Special Setter

```
$comment = new Comment();
$comment->setAuthor('Steve');
$comment->setContent('Gee, dude, you rock: best article ever!');

// Attach this comment to the previous $article object
$comment->setArticle($article);

// Alternative syntax
// Only makes sense if the object is already saved in the database
// $comment->setArticleId($article->getId());
```

Listing 8-10 shows how to use the generated getters. It also demonstrates how to chain method calls on model objects.

# Listing 8-10 - Foreign Keys Are Translated into Special Getters

```
// Many to one relationship
echo $comment->getArticle()->getTitle();
=> My first article
echo $comment->getArticle()->getContent();
=> This is my very first article.
Hope you enjoy it!

// One to many relationship
$comments = $article->getComments();
```

The getArticle() method returns an object of class Article, which benefits from the getTitle() accessor. This is much better than doing the join yourself, which may take a few lines of code (starting from the $comment->getArticleId() call).

The $comments variable in Listing 8-10 contains an array of objects of class Comment. You can display the first one with $comments[0] or iterate through the collection with foreach ($comments as $comment).

# Saving and Deleting Data

By calling the new constructor, you created a new object, but not an actual record in the blog_article table. Modifying the object has no effect on the database either. In order to save the data into the database, you need to call the save() method of the object.

```
$article->save();
```

The ORM is smart enough to detect relationships between objects, so saving the $article object also saves the related $comment object. It also knows if the saved object has an existing counterpart in the database, so the call to save() is sometimes translated in SQL by