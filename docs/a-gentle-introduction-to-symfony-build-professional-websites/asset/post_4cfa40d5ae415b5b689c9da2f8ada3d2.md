
## Using Model Behaviors

Some model modifications are generic and can be reused. For instance, methods to make a model object sortable and an optimistic lock to prevent conflicts between concurrent object saving are generic extensions that can be added to many classes.

Symfony packages these extensions into behaviors. Behaviors are external classes that provide additional methods to model classes. The model classes already contain hooks, and symfony knows how to extend them.

To enable behaviors in your model classes, you must modify your schema and use the actAs option:

```
Article:
  actAs: [Timestampable, Sluggable]
  tableName: blog_article
  columns:
    id:
      type: integer
      primary: true
      autoincrement: true
    title: string(255)
    content: clob
```

After rebuilding the model, the Article model have a slug column that is automatically set to a url friendly string based on the title.

Some behaviors that come with Doctrine are:

- Timestampable
- Sluggable
- SoftDelete
- Searchable
- I18n
- Versionable
- NestedSet

## Extended Schema Syntax

A schema.yml file can be simple, as shown in Listing 8-3. But relational models are often complex. That's why the schema has an extensive syntax able to handle almost every case.

## Attributes

Connections and tables can have specific attributes, as shown in Listing 8-24. They are set under an _attributes key.

### Listing 8-24 - Attributes for Model Settings

```
Listing 8-33
Article:
  attributes:
    export: tables
    validate: none
```

The export attribute controls what SQL is exported to the database when creating tables for that model. Using the tables value would only export the table structure and no foreign keys, indexes, etc.

Tables that contain localized content (that is, several versions of the content, in a related table, for internationalization) should use the I18n behavior (see Chapter 13 for details), as shown in Listing 8-25.

### Listing 8-25 - I18n Behavior

```
Listing 8-34
Article:
  actAs:
    I18n:
      fields: [title, content]
```

## Dealing with multiple Schemas

You can have more than one schema per application. Symfony will take into account every file ending with `.yml` in the `config/doctrine` folder. If your application has many models, or if some models don't share the same connection, you will find this approach very useful.

Consider these two schemas:

```
// In config/doctrine/business-schema.yml
Article:
  id:
    type: integer
    primary: true
    autoincrement: true
  title: string(50)

// In config/doctrine/stats-schema.yml
Hit:
  actAs: [Timestampable]
  columns:
    id:
      type: integer
      primary: true
      autoincrement: true
    resource: string(100)
```

Both schemas share the same connection (doctrine), and the Article and Hit classes will be generated under the same lib/model/doctrine directory. Everything happens as if you had written only one schema.

You can also have different schemas use different connections (for instance, doctrine and doctrine_bis, to be defined in databases.yml) and associate it with that connection:

```
// In config/doctrine/business-schema.yml
Article:
  connection: doctrine
  id:
    type: integer
    primary: true
    autoincrement: true
  title: string(50)

// In config/doctrine/stats-schema.yml
Hit:
  connection: doctrine_bis
  actAs: [Timestampable]
  columns:
    id:
      type: integer
      primary: true
      autoincrement: true
    resource: string(100)
```

Many applications use more than one schema. In particular, some plug-ins have their own schema to avoid messing with your own classes (see Chapter 17 for details).

## Column Details

The basic syntax lets you define the type with one of the type keywords. Listing 8-26 demonstrates these choices.

### Listing 8-26 - Basic Column Attributes

```
Article:
columns:
  title: string(50) # Specify the type and length
```

But you can define much more for a column. If you do, you will need to define column settings as an associative array, as shown in Listing 8-27.

### Listing 8-27 - Complex Column Attributes

```
Article:
columns:
  id:     { type: integer, notnull: true, primary: true,
            autoincrement: true }
  name:   { type: string(50), default: foobar }
  group_id: { type: integer }
```

The column parameters are as follows:

- * type: Column type. The choices are boolean, integer, double, float, decimal, string(size), date, time, timestamp, blob, and clob.
- * notnull: Boolean. Set it to true if you want the column to be required.
- * length: The size or length of the field for types that support it
- * scale: Number of decimal places for use with decimal data type (size must also be specified)
- * default: Default value.
- * primary: Boolean. Set it to true for primary keys.
- * autoincrement: Boolean. Set it to true for columns of type integer that need to take an auto-incremented value.
- * sequence: Sequence name for databases using sequences for autoIncrement columns (for example, PostgreSQL and Oracle).
- * unique: Boolean. Set it to true if you want the column to be unique.

## Relationships

You can specify foreign key relationships under the relations key in a model. The schema in Listing 8-28 will create a foreign key on the user_id column, matching the id column in the blog_user table.

### Listing 8-28 - Foreign Key Alternative Syntax

```
Article:
  actAs: [Timestampable]
  tableName: blog_article
  columns:
    id:
      type: integer
      primary: true
      autoincrement: true
    title:   string(255)
    content: clob
    user_id: integer
  relations:
    User:
      onDelete: CASCADE
      foreignAlias: Articles
```

## Indexes

You can add indexes under the indexes: key in a model. If you want to define unique indexes, you must use the type: unique syntax. For columns that require a size, because they are text columns, the size of the index is specified the same way as the length of the column using parentheses. Listing 8-30 shows the alternative syntax for indexes.

### Listing 8-30 - Indexes and Unique Indexes

```
Article:
  actAs: [Timestampable]
  tableName: blog_article
  columns:
    id:
      type: integer
      primary: true
      autoincrement: true
    title: string(255)
    content: clob
    user_id: integer
  relations:
    User:
      onDelete: CASCADE
      foreignAlias: Articles
  indexes:
    my_index:
      fields:
        title:
          length: 10
      user_id: []
    my_other_index:
      type: unique
      fields:
        created_at
```

## I18n Tables

Symfony supports content internationalization in related tables. This means that when you have content subject to internationalization, it is stored in two separate tables: one with the invariable columns and another with the internationalized columns.

### Listing 8-33 - Explicit i18n Mechanism

```
DbGroup:
  actAs:
    I18n:
      fields: [name]
  columns:
    name: string(50)
```

## Behaviors

Behaviors are model modifiers provided by plug-ins that add new capabilities to your Doctrine classes. Chapter 17 explains more about behaviors. You can define behaviors right in the schema, by listing them for each table, together with their parameters, under the actAs key. Listing 8-34 gives an example by extending the Article class with the Sluggable behavior.

### Listing 8-34 - Behaviors Declaration

```
Article:
  actAs: [Sluggable]
  # ...
```

## Don't Create the Model Twice

The trade-off of using an ORM is that you must define the data structure twice: once for the database, and once for the object model. Fortunately, symfony offers command-line tools to generate one based on the other, so you can avoid duplicate work.

## Building a SQL Database Structure Based on an Existing Schema

If you start your application by writing the schema.yml file, symfony can generate a SQL query that creates the tables directly from the YAML data model. To use the query, go to your root project directory and type this:

```
$ php symfony doctrine:build-sql
```

A schema.sql file will be created in myproject/data/sql/. Note that the generated SQL code will be optimized for the database system defined in the databases.yml.

You can use the schema.sql file directly to build the tables. For instance, in MySQL, type this:

```
$ mysqladmin -u root -p create blog
$ mysql -u root -p blog < data/sql/schema.sql
```

The generated SQL is also helpful to rebuild the database in another environment, or to change to another DBMS.

> The command line also offers a task to populate your database with data based on a text file. See Chapter 16 for more information about the doctrine:data-load task and the YAML fixture files.

## Generating a YAML Data Model from an Existing Database

Symfony can use Doctrine to generate a schema.yml file from an existing database, thanks to introspection (the capability of databases to determine the structure of the tables on which they are operating). This can be particularly useful when you do reverse-engineering, or if you prefer working on the database before working on the object model.

In order to do this, you need to make sure that the project databases.yml file points to the correct database and contains all connection settings, and then call the doctrine:build-schema command:

```
$ php symfony doctrine:build-schema
```

A brand-new schema.yml file built from your database structure is generated in the config/doctrine/ directory. You can build your model based on this schema.
