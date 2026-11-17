
Symfony packages these extensions into behaviors. Behaviors are external classes that provide additional methods to model classes. The model classes already contain hooks, and symfony knows how to extend them.

To enable behaviors in your model classes, you must modify one setting in the config/propel.ini file:

```
propel.builder.AddBehaviors = true    // Default value is false
```

There is no behavior bundled by default in symfony, but they can be installed via plug-ins. Once a behavior plug-in is installed, you can assign the behavior to a class with a single line. For instance, if you install the sfPropelParanoidBehaviorPlugin in your application, you can extend an Article class with this behavior by adding the following at the end of the Article.class.php:

```
sfPropelBehavior::add('Article', array(
  'paranoid' => array('column' => 'deleted_at')
));
```

After rebuilding the model, deleted Article objects will remain in the database, invisible to the queries using the ORM, unless you temporarily disable the behavior with sfPropelParanoidBehavior::disable().

Alternatively, you can also declare behaviors directly in the schema.yml, by listing them under the _behaviors key (see Listing 8-34 below).

Check the list of symfony plug-ins on the official repository to find behaviors. Each has its own documentation and installation guide.

## Extended Schema Syntax

A schema.yml file can be simple, as shown in Listing 8-3. But relational models are often complex. That's why the schema has an extensive syntax able to handle almost every case.

### Attributes

Connections and tables can have specific attributes, as shown in Listing 8-24. They are set under an _attributes key.

### Listing 8-24 - Attributes for Connections and Tables

```
propel:
  _attributes: { noXsd: false, defaultIdMethod: none, package: lib.model }
  blog_article:
    _attributes: { phpName: Article }
```

You may want your schema to be validated before code generation takes place. To do that, deactivate the noXSD attribute for the connection. The connection also supports the defaultIdMethod attribute. If none is provided, then the database's native method of generating IDs will be used—for example, autoincrement for MySQL, or sequences for PostgreSQL. The other possible value is none.

The package attribute is like a namespace; it determines the path where the generated classes are stored. It defaults to lib/model/, but you can change it to organize your model in subpackages. For instance, if you don't want to mix the core business classes and the classes defining a database-stored statistics engine in the same directory, then define two schemas with lib.model.business and lib.model.stats packages.

You already saw the phpName table attribute, used to set the name of the generated class mapping the table.

Tables that contain localized content (that is, several versions of the content, in a related table, for internationalization) also take two additional attributes (see Chapter 13 for details), as shown in Listing 8-25.

### Listing 8-25 - Attributes for i18n Tables

```
propel:
  blog_article:
    _attributes: { isI18N: true, i18nTable: db_group_i18n }
```

## Dealing with multiple Schemas

You can have more than one schema per application. Symfony will take into account every file ending with `schema.yml` or `schema.xml` in the `config/` folder. If your application has many tables, or if some tables don't share the same connection, you will find this approach very useful.

Consider these two schemas:

```
// In config/business-schema.yml
propel:
  blog_article:
    _attributes: { phpName: Article }
    id:
    title: varchar(50)

// In config/stats-schema.yml
propel:
  stats_hit:
    _attributes: { phpName: Hit }
    id:
    resource: varchar(100)
    created_at:
```

Both schemas share the same connection (propel), and the `Article` and `Hit` classes will be generated under the same `lib/model/` directory. Everything happens as if you had written only one schema.

You can also have different schemas use different connections (for instance, propel and propel_bis, to be defined in `databases.yml`) and organize the generated classes in subdirectories:

```
// In config/business-schema.yml
propel:
  blog_article:
    _attributes: { phpName: Article, package: lib.model.business }
    id:
    title: varchar(50)

// In config/stats-schema.yml
propel_bis:
  stats_hit:
    _attributes: { phpName: Hit, package: lib.model.stat }
    id:
    resource: varchar(100)
    created_at:
```

Many applications use more than one schema. In particular, some plug-ins have their own schema and package to avoid messing with your own classes (see Chapter 17 for details).

## Column Details

The basic syntax gives you two choices: let symfony deduce the column characteristics from its name (by giving an empty value) or define the type with one of the type keywords. Listing 8-26 demonstrates these choices.

### Listing 8-26 - Basic Column Attributes

```
propel:
  blog_article:
    id: ~ # Let symfony do the work
    title: varchar(50) # Specify the type yourself
```

But you can define much more for a column. If you do, you will need to define column settings as an associative array, as shown in Listing 8-27.

### Listing 8-27 - Complex Column Attributes

```
propel:
  blog_article:
    id: { type: integer, required: true, primaryKey: true,
      autoIncrement: true }
    name: { type: varchar(50), default: foobar, index: true }
    group_id: { type: integer, foreignTable: db_group, foreignReference:
      id, onDelete: cascade }
```

The column parameters are as follows:

- * type: Column type. The choices are boolean, tinyint, smallint, integer, bigint, double, float, real, decimal, char, varchar(size), longvarchar, date, time, timestamp, bu_date, bu_timestamp, blob, and clob.
- * required: Boolean. Set it to true if you want the column to be required.
- * size: The size or length of the field for types that support it
- * scale: Number of decimal places for use with decimal data type (size must also be specified)
- * default: Default value.
- * primaryKey: Boolean. Set it to true for primary keys.
- * autoIncrement: Boolean. Set it to true for columns of type integer that need to take an auto-incremented value.
- * sequence: Sequence name for databases using sequences for autoIncrement columns (for example, PostgreSQL and Oracle).
- * index: Boolean. Set it to true if you want a simple index or to unique if you want a unique index to be created on the column.
- * foreignTable: A table name, used to create a foreign key to another table.
- * foreignReference: The name of the related column if a foreign key is defined via foreignTable.
- * onDelete: Determines the action to trigger when a record in a related table is deleted. When set to setnull, the foreign key column is set to null. When set to cascade, the record is deleted. If the database engine doesn't support the set behavior, the ORM emulates it. This is relevant only for columns bearing a foreignTable and a foreignReference.
- * isCulture: Boolean. Set it to true for culture columns in localized content tables (see Chapter 13).

## Foreign Keys

As an alternative to the foreignTable and foreignReference column attributes, you can add foreign keys under the _foreignKeys: key in a table. The schema in Listing 8-28 will create a foreign key on the user_id column, matching the id column in the blog_user table.

### Listing 8-28 - Foreign Key Alternative Syntax

```
propel:
  blog_article:
    id: ~
    title: varchar(50)
    user_id: { type: integer }
    _foreignKeys:
        -
            foreignTable: blog_user
            onDelete: cascade
            references:
                - { local: user_id, foreign: id }
```

The alternative syntax is useful for multiple-reference foreign keys and to give foreign keys a name, as shown in Listing 8-29.

### Listing 8-29 - Foreign Key Alternative Syntax Applied to Multiple Reference Foreign Key

```
_foreignKeys:
    my_foreign_key:
        foreignTable: db_user
        onDelete: cascade
        references:
            - { local: user_id, foreign: id }
            - { local: post_id, foreign: id }
```

## Indexes

As an alternative to the index column attribute, you can add indexes under the `_indexes:` key in a table. If you want to define unique indexes, you must use the `_uniques:` header instead. For columns that require a size, because they are text columns, the size of the index is specified the same way as the length of the column using parentheses. Listing 8-30 shows the alternative syntax for indexes.

### Listing 8-30 - Indexes and Unique Indexes Alternative Syntax

```
propel:
    blog_article:
        id:        ~
        title:     varchar(50)
        created_at:
        _indexes:
            my_index:       [title(10), user_id]
            _uniques:
                my_other_index: [created_at]
```

The alternative syntax is useful only for indexes built on more than one column.

## Empty Columns

When meeting a column with no value, symfony will do some magic and add a value of its own. See Listing 8-31 for the details added to empty columns.

### Listing 8-31 - Column Details Deduced from the Column Name

```
// Empty columns named id are considered primary keys
id: { type: integer, required: true, primaryKey: true,
      autoIncrement: true }

// Empty columns named XXX_id are considered foreign keys
foobar_id: { type: integer, foreignTable: db_foobar, foreignReference: id
}
