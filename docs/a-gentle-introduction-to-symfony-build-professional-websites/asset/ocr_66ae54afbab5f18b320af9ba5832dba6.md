```
edit: ~
new: ~
```

This configuration is enough to generate the basic administration. Any customization is added under the config key. Listing 14-4 shows a typical customized generator.yml.

# Listing 14-4 - Typical Complete Generator Configuration

```
generator:
  class: sfPropelGenerator
  param:
    model_class:          BlogArticle
    theme:                admin
    non_verbose_templates: true
    with_show:            false
    singular:             BlogArticle
    plural:               BlogArticles
    route_prefix:         blog_article
    with_propel_route:    1
    actions_base_class:   sfActions

  config:
    actions:
      _new: { label: "Create a new article" }

    fields:
      author_id:   { label: Article author }
      published_on: { credentials: editor }

    list:
      title:         Articles
      display:       [title, blog_author, blog_category]
      fields:
        published_on: { date_format: dd/MM/yy }
      layout:        stacked
      params:        |
        %%is_published%%<strong>%%=title%%</strong><br />by
        %%blog_author%%
        in %%blog_category%% (%%created_at%%)<p>%%content%%</p>
      max_per_page:  2
      sort:          [title, asc]

    filter:
      display: [title, blog_category_id, blog_author_id, is_published]

    form:
      display:
        "Post":      [title, blog_category_id, content]
        "Workflow":  [blog_author_id, is_published, created_at]
      fields:
        published_at: { help: "Date of publication" }
        title:        { attributes: { style: "width: 350px" } }

    new:
      title: New article

    edit:
      title: Editing article "%%title%%"
```