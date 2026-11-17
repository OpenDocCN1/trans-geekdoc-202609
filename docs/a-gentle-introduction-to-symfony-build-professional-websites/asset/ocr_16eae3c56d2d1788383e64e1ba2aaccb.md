# Customizing the plug-in schema

# Doctrine

When building the model, Doctrine will look for all the *schema.yml in application's and plugins' config/ directories, so a project schema can override a plugin schema. The merging process allows for addition or modification of table or columns. For instance, the following example shows how to add columns to a table defined in a plugin schema.

```
#Original schema, in plugins/myPlugin/config/schema.yml
Article:
  columns:
    name: string(50)

#Project schema, in config/schema.yml
Article:
  columns:
    stripped_title: string(50)

# Resulting schema, merged internally and used for model and sql generation
Article:
  columns:
    name: string(50)
    stripped_title: string(50)
```

# Propel

When building the model, symfony will look for custom YAML files for each existing schema, including plug-in ones, following this rule:

| Original schema name | Custom schema name |
| --- | --- |
| config/schema.yml | schema.custom.yml |
| config/foobar_schema.yml | foobar_schema.custom.yml |
| plugins/myPlugin/config/schema.yml | myPlugin-schema.custom.yml |
| plugins/myPlugin/config/foo_schema.yml | myPlugin_foo-schema.custom.yml |

Custom schemas will be looked for in the application's and plugins' config/ directories, so a plugin can override another plugin's schema, and there can be more than one customization per schema.

Symfony will then merge the two schemas based on each table's phpName. The merging process allows for addition or modification of tables, columns, and column attibutes. For instance, the next listing shows how a custom schema can add columns to a table defined in a plug-in schema.

```
# Original schema, in plugins/myPlugin/config/schema.yml
propel:
  article:
    _attributes:    { phpName: Article }
    title:          varchar(50)
    user_id:        { type: integer }
    created_at:
```