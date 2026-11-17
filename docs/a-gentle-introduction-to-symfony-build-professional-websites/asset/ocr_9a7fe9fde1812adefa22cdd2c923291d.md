> **Note about assets inclusions using the view.yml file**
> 
> The best practice is to define the defaults stylesheets and javascripts file in the project view.yml file, and include specifics stylesheets or javascripts files in your templates using the dedicated helper. This way, you do not have to remove or replace already included assets, which can be a painfull in some cases.

# Layout Configuration

According to the graphical charter of your website, you may have several layouts. Classic websites have at least two: the default layout and the pop-up layout.

You have already seen that the default layout is myproject/apps/frontend/templates/layout.php. Additional layouts must be added in the same global templates/ directory. If you want a view to use a frontend/templates/my_layout.php file, use the syntax shown in Listing 7-36.

```
Listing 7-36 - Layout Definition

// In view.yml
indexSuccess:
  layout: my_layout

// In the action
$this->setLayout('my_layout');

// In the template
<?php decorate_with('my_layout') ?>
```

Some views don't need any layout at all (for instance, plain text pages or RSS feeds). In that case, set has_layout to false, as shown in Listing 7-37.

```
Listing 7-37 - Layout Removal

// In `view.yml`
indexSuccess:
  has_layout: false

// In the Action
$this->setLayout(false);

// In the template
<?php decorate_with(false) ?>
```

> Ajax actions views have no layout by default.

# Output Escaping

When you insert dynamic data in a template, you must be sure about the data integrity. For instance, if data comes from forms filled in by anonymous users, there is a risk that it may include malicious scripts intended to launch cross-site scripting (XSS) attacks. You must be able to escape the output data, so that any HTML tag it contains becomes harmless.

As an example, suppose that a user fills an input field with the following value: