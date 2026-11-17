+   _filters_field.php
+   _flashes.php
+   _form.php
+   _form_actions.php
+   _form_field.php
+   _form_fieldset.php
+   _form_footer.php
+   _form_header.php
+   _list.php
+   _list_actions.php
+   _list_batch_actions.php
+   _list_field_boolean.php
+   _list_footer.php
+   _list_header.php
+   _list_td_actions.php
+   _list_td_batch_actions.php
+   _list_td_stacked.php
+   _list_td_tabular.php
+   _list_th_stacked.php
+   _list_th_tabular.php
+   _pagination.php
+   editSuccess.php
+   indexSuccess.php
+   newSuccess.php

This shows that a generated administration module is composed mainly of three views, list, new, and edit. If you have a look at the code, you will find it to be very modular, readable, and extensible.

# Introducing the generator.yml Configuration File

The generated administration modules rely on parameters found in the generator.yml YAML configuration file. To see the default configuration of a newly created administration module, open the generator.yml file, located in the backend/modules/article/config/generator.yml directory and reproduced in Listing 14-3.

Listing 14-3 - Default Generator Configuration, in backend/modules/article/config/generator.yml

```
generator:
  class: sfPropelGenerator
  param:
    model_class:           BlogArticle
    theme:                 admin
    non_verbose_templates: true
    with_show:             false
    singular:              BlogArticle
    plural:                BlogArticles
    route_prefix:          blog_article
    with_propel_route:     1
    actions_base_class:    sfActions

  config:
    actions: ~
    fields: ~
    list: ~
    filter: ~
    form: ~
```