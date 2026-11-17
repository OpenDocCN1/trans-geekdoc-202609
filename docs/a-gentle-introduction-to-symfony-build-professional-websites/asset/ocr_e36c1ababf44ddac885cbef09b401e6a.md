# Base and Custom Classes

Why keep two versions of the data object model in two different directories?

You will probably need to add custom methods and properties to the model objects (think about the getName() method in Listing 8-1). But as your project develops, you will also add tables or columns. Whenever you change the schema.yml file, you need to regenerate the object model classes by making a new call to doctrine:build-model. If your custom methods were written in the classes actually generated, they would be erased after each generation.

The Base classes kept in the lib/model/doctrine/base/ directory are the ones directly generated from the schema. You should never modify them, since every new build of the model will completely erase these files.

On the other hand, the custom object classes, kept in the lib/model/doctrine directory, actually inherit from the Base ones. When the doctrine:build-model task is called on an existing model, these classes are not modified. So this is where you can add custom methods.

Listing 8-4 presents an example of a custom model class as created by the first call to the doctrine:build-model task.

Listing 8-4 - Sample Model Class File, in lib/model/doctrine/Article.php

```
class Article extends BaseArticle
{
}
```

It inherits everything of the BaseArticle class, but a modification in the schema will not affect it.

The mechanism of custom classes extending base classes allows you to start coding, even without knowing the final relational model of your database. The related file structure makes the model both customizable and evolutionary.

# Object and Table Classes

Article and Comment are object classes that represent a record in the database. They give access to the columns of a record and to related records. This means that you will be able to know the title of an article by calling a method of an Article object, as in the example shown in Listing 8-5.

Listing 8-5 - Getters for Record Columns Are Available in the Object Class

```
$article = new Article();
// ...
$title = $article->getTitle();
```

ArticleTable and CommentTable are table classes; that is, classes that contain public methods to operate on the tables. They provide a way to retrieve records from the tables. Their methods usually return an object or a collection of objects of the related object class, as shown in Listing 8-6.

Listing 8-6 - Public Methods to Retrieve Records Are Available in the Table Class

```
// $article is an instance of class Article
$article = Doctrine_Core::getTable('Article')->find(123);
```