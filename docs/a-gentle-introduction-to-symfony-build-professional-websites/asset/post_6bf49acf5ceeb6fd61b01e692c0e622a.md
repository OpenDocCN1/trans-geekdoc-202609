
decoration process), and the partials are executed when they are called in a template. Does it sound too abstract? Let’s see an example.

Imagine a layout with one zone for the template and two slots: one for the sidebar and the other for the footer. The slot values are defined in the templates. During the decoration process, the layout code wraps the template code, and the slots are filled with the previously defined values, as illustrated in Figure 7-4. The sidebar and the footer can then be contextual to the main action. This is like having a layout with more than one “hole”.

Figure 7-4 - Layout slots defined in a template

![](img/0f886a7f4cbcc3939be96e985ca35ff4_107_0.png)

Seeing some code will clarify things further. To include a slot, use the include_slot() helper. The has_slot() helper returns true if the slot has been defined before, providing a fallback mechanism as a bonus. For instance, define a placeholder for a ‘sidebar’ slot in the layout and its default content as shown in Listing 7-14.

Listing 7-14 - Including a ‘sidebar’ Slot in the Layout

```php
<div id="sidebar">
<?php if (has_slot('sidebar')): ?>
    <?php include_slot('sidebar') ?>
<?php else: ?>
    <!-- default sidebar code -->
    <h1>Contextual zone</h1>
    <p>This zone contains links and information
    relative to the main content of the page.</p>
<?php endif; ?>
</div>
```

As it’s quite common to display some default content if a slot is not defined, the include_slot helper returns a Boolean indicating if the slot has been defined. Listing 7-15 shows how to take this return value into account to simplify the code.

Listing 7-15 - Including a ‘sidebar’ Slot in the Layout

```php
<div id="sidebar">
<?php if (!include_slot('sidebar')): ?>
    <!-- default sidebar code -->
    <h1>Contextual zone</h1>
    <p>This zone contains links and information
    relative to the main content of the page.</p>
<?php endif; ?>
</div>
```

Each template has the ability to define the contents of a slot (actually, even partials can do it). As slots are meant to hold HTML code, symfony offers a convenient way to define them: just write the slot code between a call to the slot() and end_slot() helpers, as in Listing 7-16.

Listing 7-16 - Overriding the ‘sidebar’ Slot Content in a Template

```php
// ...
<?php slot('sidebar') ?>

<!-- custom sidebar code for the current template-->
<h1>User details</h1>
<p>name: <?php echo $user->getName() ?></p>
<p>email: <?php echo $user->getEmail() ?></p>
<?php end_slot() ?>
```

The code between the slot helpers is executed in the context of the template, so it has access to all the variables that were defined in the action. Symfony will automatically put the result of this code in the response object. It will not be displayed in the template, but made available for future include_slot() calls, like the one in Listing 7-14.

Slots are very useful to define zones meant to display contextual content. They can also be used to add HTML code to the layout for certain actions only. For instance, a template displaying the list of the latest news might want to add a link to an RSS feed in the <head> part of the layout. This is achieved simply by adding a 'feed' slot in the layout and overriding it in the template of the list.

If the content of the slot is very short, as this is the case when defining a title slot for example, you can simply pass the content as a second argument of the slot() method as shown in Listing 7-17.

Listing 7-17 - Using slot() to define a short Value

```php
<?php slot('title', 'The title value') ?>
```

## Where to find template fragments

People working on templates are usually web designers, who may not know symfony very well and may have difficulties finding template fragments, since they can be scattered all over the application. These few guidelines will make them more comfortable with the symfony templating system.

First of all, although a symfony project contains many directories, all the layouts, templates, and template fragments files reside in directories named templates/. So as far as a web designer is concerned, a project structure can be reduced to something like this:

```
myproject/
apps/
application1/
templates/	# Layouts for application 1
modules/
module1/
templates/	# Templates and partials for module 1
module2/
templates/	# Templates and partials for module 2
module3/
templates/	# Templates and partials for module 3
```

All other directories can be ignored.

When meeting an include_partial(), web designers just need to understand that only the first argument is important. This argument's pattern is module_name/partial_name, and that means that the presentation code is to be found in modules/module_name/templates/_partial_name.php.

For the include_component() helper, module name and partial name are the first two arguments. As for the rest, a general idea about what helpers are and which helpers are the most common in templates should be enough to start designing templates for symfony applications.

## View Configuration

In symfony, a view consists of two distinct parts:

- The HTML presentation of the action result (stored in the template, in the layout, and in the template fragments)
- All the rest, including the following:
  - Meta declarations: Keywords, description, or cache duration.
  - Page title: Not only does it help users with several browser windows open to find yours, but it is also very important for search sites’ indexing.
  - File inclusions: JavaScript and style sheet files.
  - Layout: Some actions require a custom layout (pop-ups, ads, and so on) or no layout at all (such as Ajax actions).

In the view, all that is not HTML is called view configuration, and symfony provides two ways to manipulate it. The usual way is through the view.yml configuration file. It can be used whenever the values don’t depend on the context or on database queries. When you need to set dynamic values, the alternative method is to set the view configuration via the sfResponse object attributes directly in the action.

> If you ever set a view configuration parameter both via the sfResponse object and via the view.yml file, the sfResponse definition takes precedence.

### The view.yml File

Each module can have one view.yml file defining the settings of its views. This allows you to define view settings for a whole module and per view in a single file. The first-level keys of the view.yml file are the module view names. Listing 7-18 shows an example of view configuration.

Listing 7-18 - Sample Module-Level view.yml

```yaml
editSuccess:
  metas:
    title: Edit your profile

editError:
  metas:
    title: Error in the profile edition

all:
  stylesheets: [my_style]
  metas:
    title: My website
```

> Be aware that the main keys in the view.yml file are view names, not action names. As a reminder, a view name is composed of an action name and an action termination. For instance, if the edit action returns sfView::SUCCESS (or returns nothing at all, since it is the default action termination), then the view name is editSuccess.

The default settings for the module are defined under the all: key in the module view.yml. The default settings for all the application views are defined in the application view.yml. Once again, you recognize the configuration cascade principle:

- In apps/frontend/modules/mymodule/config/view.yml, the per-view definitions apply only to one view and override the module-level definitions.
- In apps/frontend/modules/mymodule/config/view.yml, the all: definitions apply to all the actions of the module and override the application-level definitions.
- In apps/frontend/config/view.yml, the default: definitions apply to all modules and all actions of the application.

> > Module-level view.yml files don't exist by default. The first time you need to adjust a view configuration parameter for a module, you will have to create an empty view.yml in its config/ directory.

After seeing the default template in Listing 7-5 and an example of a final response in Listing 7-6, you may wonder where the header values come from. As a matter of fact, they are the default view settings, defined in the application view.yml and shown in Listing 7-19.

Listing 7-19 - Default Application-Level View Configuration, in apps/frontend/config/view.yml

```yaml
default:
  http_metas:
    content-type: text/html

  metas:
    #title:         symfony project
    #description:   symfony project
    #keywords:      symfony, project
    #language:      en
    #robots:        index, follow

  stylesheets:    [main]

  javascripts:    []

  has_layout:     true
  layout:         layout
```

Each of these settings will be described in detail in the “View Configuration Settings” section.

### The Response Object

Although part of the view layer, the response object is often modified by the action. Actions can access the symfony response object, called sfResponse, via the getResponse() method. Listing 7-20 lists some of the sfResponse methods often used from within an action.

Listing 7-20 - Actions Have Access to the sfResponse Object Methods

```php
class mymoduleActions extends sfActions
{
  public function executeIndex()
  {
    $response = $this->getResponse();

    // HTTP headers
    $response->setContentType('text/xml');
    $response->setHttpHeader('Content-Language', 'en');
    $response->setStatusCode(403);
    $response->addVaryHttpHeader('Accept-Language');
  }
}
```

