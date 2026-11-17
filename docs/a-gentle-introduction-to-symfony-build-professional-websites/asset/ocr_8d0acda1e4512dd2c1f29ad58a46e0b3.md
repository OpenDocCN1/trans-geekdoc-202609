```
Listing 8-1
public function getName()
{
    return $this->getFirstName().' '.$this->getLastName();
}
```

All the repeated data-access functions and the business logic of the data itself can be kept in such objects. Suppose you have a ShoppingCart class in which you keep Items (which are objects). To get the full amount of the shopping cart for the checkout, write a custom method to encapsulate the actual calculation, as shown in Listing 8-2.

# Listing 8-2 - Accessors Mask the Data Logic

```
Listing 8-2
public function getTotal()
{
    $total = 0;
    foreach ($this->getItems() as $item)
    {
        $total += $item->getPrice() * $item->getQuantity();
    }

    return $total;
}
```

There is another important point to consider when building data-access procedures: Database vendors use different SQL syntax variants. Switching to another database management system (DBMS) forces you to rewrite part of the SQL queries that were designed for the previous one. If you build your queries using a database-independent syntax, and leave the actual SQL translation to a third-party component, you can switch database systems without pain. This is the goal of the database abstraction layer. It forces you to use a specific syntax for queries, and does the dirty job of conforming to the DBMS particulars and optimizing the SQL code.

The main benefit of an abstraction layer is portability, because it makes switching to another database possible, even in the middle of a project. Suppose that you need to write a quick prototype for an application, but the client hasn't decided yet which database system would best suit his needs. You can start building your application with SQLite, for instance, and switch to MySQL, PostgreSQL, or Oracle when the client is ready to decide. Just change one line in a configuration file, and it works.

Symfony uses Propel or Doctrine as the ORM, and they use PHP Data Objects for database abstraction. These two third-party components, both developed by the Propel and Doctrine teams, are seamlessly integrated into symfony, and you can consider them as part of the framework. Their syntax and conventions, described in this chapter, were adapted so that they differ from the symfony ones as little as possible.

> In a symfony project, all the applications share the same model. That's the whole point of the project level: regrouping applications that rely on common business rules. This is the reason that the model is independent from the applications and the model files are stored in a lib/model/ directory at the root of the project.

# Symfony's Database Schema

In order to create the data object model that symfony will use, you need to translate whatever relational model your database has to an object data model. The ORM needs a description of the relational model to do the mapping, and this is called a schema. In a schema, you define the tables, their relations, and the characteristics of their columns.