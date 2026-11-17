```
Listing A-23
$ php symfony configure:database --env=dev
"mysql:host=localhost;dbname=blog_dev" root mySExcret
```

This configuration can also be overridden per application. For instance, you can use this approach to have different security policies for a front-end and a back-end application, and define several database users with different privileges in your database to handle this:

```
Listing A-24
$ php symfony configure:database --app=frontend
"mysql:host=localhost;dbname=blog" root mySExcret
```

For each environment, you can define many connections. Each connection refers to a schema being labeled with the same name. The default connection name used is propel and it refers to the propel schema in Listing 8-3. The name option allows you to create another connection:

```
Listing A-25
$ php symfony configure:database --name=main
"mysql:host=localhost;dbname=example" root mySExcret
```

You can also enter these connection settings manually in the databases.yml file located in the config/ directory. Listing 8-17 shows an example of such a file and Listing 8-18 shows the same example with the extended notation.

# Listing 8-17 - Shorthand Database Connection Settings

```
Listing A-26
all:
  propel:
    class: sfPropelDatabase
    param:
      dsn: mysql://login:passwd@localhost/blog
```

# Listing 8-18 - Sample Database Connection Settings, in myproject/config/
databases.yml

```
Listing A-27
prod:
  propel:
    param:
      hostspec: mydataserver
      username: myusername
      password: xxxxxxxx
```

```
all:
  propel:
    class: sfPropelDatabase
    param:
      phptype: mysql     # Database vendor
      hostspec: localhost
      database: blog
      username: login
      password: passwd
      port: 80
      encoding: utf8     # Default charset for table creation
      persistent: true   # Use persistent connections
```

The permitted values of the phptype parameter are the ones of the database systems supported by PDO:

+   - mysql
+   - mssql