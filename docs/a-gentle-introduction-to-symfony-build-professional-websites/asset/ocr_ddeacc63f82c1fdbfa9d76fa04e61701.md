# Title Configuration

The page title is a key part to search engine indexing. It is also very useful with modern browsers that provide tabbed browsing. In HTML, the title is both a tag and meta information of the page, so the view.yml file sees the title: key as a child of the metas: key. Listing 7-24 shows the title definition in view.yml, and Listing 7-25 shows the definition in the action.

Listing 7-24 - Title Definition in view.yml

```
indexSuccess:
  metas:
    title: Three little piggies
```

Listing 7-25 - Title Definition in the Action—Allows for Dynamic Titles

```
$this->getResponse()->setTitle(sprintf('%d little piggies', $number));
```

In the <head> section of the final document, the title definition sets the <meta name="title"> tag if the include_metas() helper is present, and the <title> tag if the include_title() helper is present. If both are included (as in the default layout of Listing 7-5), the title appears twice in the document source (see Listing 7-6), which is harmless.

> Another way to handle the title definition is to use slots, as discussed above. This method allow to keep a better separation of concern between controllers and templates : the title belongs to the view, not the controller.

# File Inclusion Configuration

Adding a specific style sheet or JavaScript file to a view is easy, as Listing 7-26 demonstrates.

Listing 7-26 - Asset File Inclusion

```
// In the view.yml
indexSuccess:
  stylesheets: [mystyle1, mystyle2]
  javascripts: [myscript]

// In the action
$this->getResponse()->addStylesheet('mystyle1');
$this->getResponse()->addStylesheet('mystyle2');
$this->getResponse()->addJavascript('myscript');

// In the Template
<?php use_stylesheet('mystyle1') ?>
<?php use_stylesheet('mystyle2') ?>
<?php use_javascript('myscript') ?>
```

In each case, the argument is a file name. If the file has a logical extension (.css for a style sheet and .js for a JavaScript file), you can omit it. If the file has a logical location (/css/ for a style sheet and /js/ for a JavaScript file), you can omit it as well. Symfony is smart enough to figure out the correct extension or location.

Like the meta and title definitions, the file inclusion definitions require the usage of the include_javascripts() and include_stylesheets() helpers in the template or layout to be included. This means that the previous settings will output the HTML code of Listing 7-27.

Listing 7-27 - File Inclusion Result