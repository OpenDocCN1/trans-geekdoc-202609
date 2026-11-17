generator can also hide interactions according to credentials. Listing 14-31 demonstrates these features.

# Listing 14-31 - Using Credentials in generator.yml

```
config:
  # The id column is displayed only for users with the admin credential
  list:
    title:       List of Articles
    display:     [id, =title, content, nb_comments]
    fields:
      id:        { credentials: [admin] }

  # The addcomment interaction is restricted to the users with the admin credential
  actions:
    addcomment: { credentials: [admin] }
```

# Modifying the Presentation of Generated Modules

You can modify the presentation of the generated modules so that it matches any existing graphical charter, not only by applying your own style sheet, but also by overriding the default templates.

# Using a Custom Style Sheet

Since the generated HTML is structured content, you can do pretty much anything you like with the presentation.

You can define an alternative CSS to be used for an administration module instead of a default one by adding a css parameter to the generator configuration, as in Listing 14-32.

# Listing 14-32 - Using a Custom Style Sheet Instead of the Default One

```
generator:
  class: sfPropelGenerator
  param:
    model_class:       BlogArticle
    theme:             admin
    non_verbose_templates: true
    with_show:         false
    singular:          BlogArticle
    plural:            BlogArticles
    route_prefix:      blog_article
    with_propel_route: 1
    actions_base_class: sfActions
    css:               mystylesheet
```

Alternatively, you can also use the mechanisms provided by the module view.yml to override the styles on a per-view basis.

# Creating a Custom Header and Footer

The list, new, and edit views systematically include a header and footer partial. There is no such partial by default in the templates/ directory of an administration module, but you just need to add one with one of the following names to have it included automatically: