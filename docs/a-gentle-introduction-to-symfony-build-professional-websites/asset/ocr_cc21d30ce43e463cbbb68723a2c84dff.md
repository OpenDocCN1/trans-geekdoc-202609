they are operating). This can be particularly useful when you do reverse-engineering, or if
you prefer working on the database before working on the object model.

In order to do this, you need to make sure that the project databases.yml file points to the
correct database and contains all connection settings, and then call the propel:build-
schema command:

```
$ php symfony propel:build-schema
```

A brand-new schema.yml file built from your database structure is generated in the
config/ directory. You can build your model based on this schema.

The schema-generation command is quite powerful and can add a lot of database-dependent
information to your schema. As the YAML format doesn't handle this kind of vendor
information, you need to generate an XML schema to take advantage of it. You can do this
simply by adding an xml argument to the build-schema task:

```
$ php symfony propel:build-schema --xml
```

Instead of generating a schema.yml file, this will create a schema.xml file fully compatible
with Propel, containing all the vendor information. But be aware that generated XML
schemas tend to be quite verbose and difficult to read.

# The propel.ini Configuration

This file contains other settings used to configure the Propel generator to make generated
model classes compatible with symfony. Most settings are internal and of no interest to the
user, apart from a few:

```
// Base classes are autoloaded in symfony
// Set this to true to use include_once statements instead
// (Small negative impact on performance)
propel.builder.addIncludes = false
```

```
// Generated classes are not commented by default
// Set this to true to add comments to Base classes
// (Small negative impact on performance)
propel.builder.addComments = false
```

```
// Behaviors are not handled by default
// Set this to true to be able to handle them
propel.builder.AddBehaviors = false
```

After you make a modification to the propel.ini settings, don't forget to rebuild the
model so the changes will take effect.

# Summary

Symfony uses Propel as the ORM and PHP Data Objects as the database abstraction layer. It
means that you must first describe the relational schema of your database in YAML before
generating the object model classes. Then, at runtime, use the methods of the object and peer
classes to retrieve information about a record or a set of records. You can override them and
extend the model easily by adding methods to the custom classes. The connection settings are
defined in a databases.yml file, which can support more than one connection. And the
command line contains special tasks to avoid duplicate structure definition.