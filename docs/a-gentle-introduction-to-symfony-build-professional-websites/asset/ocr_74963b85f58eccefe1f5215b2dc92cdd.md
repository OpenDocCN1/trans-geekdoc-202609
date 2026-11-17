+   - BaseCommentPeer.php

In addition, the actual data model classes will be created in lib/model/:

+   - Article.php
+   - ArticlePeer.php
+   - Comment.php
+   - CommentPeer.php

You defined only two tables, and you end up with eight files. There is nothing wrong, but it deserves some explanation.

# Base and Custom Classes

Why keep two versions of the data object model in two different directories?

You will probably need to add custom methods and properties to the model objects (think about the getName() method in Listing 8-1). But as your project develops, you will also add tables or columns. Whenever you change the schema.yml file, you need to regenerate the object model classes by making a new call to propel:build-model. If your custom methods were written in the classes actually generated, they would be erased after each generation.

The Base classes kept in the lib/model/om/ directory are the ones directly generated from the schema. You should never modify them, since every new build of the model will completely erase these files.

On the other hand, the custom object classes, kept in the lib/model/ directory, actually inherit from the Base ones. When the propel:build-model task is called on an existing model, these classes are not modified. So this is where you can add custom methods.

Listing 8-4 presents an example of a custom model class as created by the first call to the propel:build-model task.

```
Listing 8-4 - Sample Model Class File, in lib/model/Article.php

class Article extends BaseArticle
{
}
```

It inherits all the methods of the BaseArticle class, but a modification in the schema will not affect it.

The mechanism of custom classes extending base classes allows you to start coding, even without knowing the final relational model of your database. The related file structure makes the model both customizable and evolutionary.

# Object and Peer Classes

Article and Comment are object classes that represent a record in the database. They give access to the columns of a record and to related records. This means that you will be able to know the title of an article by calling a method of an Article object, as in the example shown in Listing 8-5.

```
Listing 8-5 - Getters for Record Columns Are Available in the Object Class

$article = new Article();
// ...
$title = $article->getTitle();
```

ArticlePeer and CommentPeer are peer classes; that is, classes that contain static methods to operate on the tables. They provide a way to retrieve records from the tables.