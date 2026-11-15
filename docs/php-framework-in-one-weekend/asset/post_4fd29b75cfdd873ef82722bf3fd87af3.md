
return Response::create("Not found", 404);
}

## Chapter 9
Design and Layout

Let's turn our attention to the front-end for a while and make the output look a bit more professional. The public folder is the only web-accessible folder in our project. We are using PHP's built-in web server for our development environment, but eventually this is where the production web server will be pointing.

Until now our public folder has contained just the index.php file that is used to launch our App. It creates the $request object from PHP's global request variables, instantiates the App, passes the $request to the app and then sends the generated $response.

We will now put some other files in this public folder so that our site users will be able to download them over the web. We don't have any CSS or JavaScript yet. Let's make use of Twitter Bootstrap, as it's a quick way to get started. We'll use the pre-compiled and minified version for now. Download the bundle from the getting started page [4], extract the archive and copy the css, fonts, and js folders into your public folder.

Listing 9.1 shows an updated base templates/index.html template file using the code from Bootstrap's basic template. Listing 9.2 shows our contact form updated to use Bootstrap's form markup.

```
2 <html lang="en">
3 <head>
4 <meta charset="utf-8">
5 <meta http-equiv="X-UA-Compatible" content="IE=edge">
6 <meta name="viewport" content="width=device-width, initial-scale=1">
7 <title>{{ title }}</title>
8 <link href="/css/bootstrap.min.css" rel="stylesheet">
9 <!--[if lt IE 9]>
10 <script src="https://oss.maxcdn.com/html5shiv/3.7.2/html5shiv.min.js"></script>
11 <script src="https://oss.maxcdn.com/respond/1.4.2/respond.min.js"></script>
12 <![endif]-->
13 </head>
14 <body>
15 <div class="container">
16 <h1>{{ title }}</h1>
17 <p>{{ content | raw }}</p>
18 </div>
19
20 <script src="https://ajax.googleapis.com/ajax/libs/jquery/1.11.3/jquery.min.js"></script>
21 <script src="/js/bootstrap.min.js"></script>
22 </body>
23 </html>
```

## Listing 9.1: templates/index.html

```
1 <form action="/contact" method="post">
2 <div class="form-group">
3 <label for="name">Name</label>
4 <input type="text" name="name" id="name" class="form-control">
5 </div>
6 <div class="form-group">
7 <label for="email">Email</label>
8 <input type="email" name="email" id="email" class="form-control">
9 </div>
10 <div class="form-group">
11 <label for="message">Message</label>
12 <textarea name="message" cols="30" rows="10" id="message" class="form-control"></textarea>
13 </div>
14 <input type="submit" value="Send" class="btn btn-primary">
15 </form>
```

## Listing 9.2: templates/forms/contact.html

## Template Inheritance

Remember when we added the contact form, and we had to change the output of {{ content }} to {{ content | raw }}? We did this because we rendered the form template and then passed this into our page template in the content variable. Twig has the raw filter to bypass its automatic filtering and escaping. This is an important security measure, so ideally we don't want to disable it.

We could create separate HTML page templates, one for our basic page controller, and one for our contact page, but this introduces unnecessary duplication. We want to be kind to our future selves and think about maintenance. When we come back in the future to update our design, we want a single place to make those changes. This can be achieved by putting all the common code into a single template, then extending this template to create custom versions when we need to do something different.

To show how this works we first change our main index.html to be a parent template that others can inherit from. To do this we define Twig blocks that can be customised. Lines 20-23 of listing 9.3 define a content block. We then create a new template file called basic.html that extends index.html. This is shown in listing 9.4. There is very little in this template because we don't have to recreate the whole page. This template reuses the HTML from the index template, except with the region defined by {% block content %} replaced with its own content block. Don't confuse the two uses of the word content in the basic.html template. We have a block called content, and an output variable called content. The block refers to the content block from the parent template that we are replacing. The variable refers to the content variable that is passed in to the template.

Listing 9.5 shows a new template created for the contact page. This also extends the main index template. We redefine the content block again, but this time include the form instead of printing the content variable.

Listings 9.6, 9.7, and 9.8 show the updates required to the controllers to output using the new templates.

```
2 <html lang="en">
3 <head>
4 <meta charset="utf-8">
5 <meta http-equiv="X-UA-Compatible" content="IE=edge">
6 <meta name="viewport" content="width=device-width, initial-scale=1">
7 <title>{{ title }}</title>
8 <link href="/css/bootstrap.min.css" rel="stylesheet">
9 <!--[if lt IE 9]>
10 <script src="https://oss.maxcdn.com/html5shiv/3.7.2/html5shiv.min.js"></script>
11 <script src="https://oss.maxcdn.com/respond/1.4.2/respond.min.js"></script>
12 <![endif]-->
13 </head>
14 <body>
15 <div class="container">
16 <h1>{{ title }}</h1>
17
18 {% block content %}
19 <p>Template will replace this content.</p>
20 {% endblock %}
21
22 </div>
23 <script src="https://ajax.googleapis.com/ajax/libs/jquery/1.11.3/jquery.min.js"></script>
24 <script src="/js/bootstrap.min.js"></script>
25 </body>
26 </html>
```

## Listing 9.3: templates/index.html

```
1 {% extends 'index.html' %}
2
3 {% block content %}
4 <p>{{ content }}</p>
5 {% endblock %}
```

## Listing 9.4: templates/basic.html

```
1 {% extends 'index.html' %}
2
3 {% block content %}
4 {% include 'forms/contact.html' %}
5 {% endblock %}
```

## Listing 9.5: templates/contact.html

## Listing 9.6: src/Controller/BasicPageController.php

```
25 $content = $this->twig->render('basic.html', $menu[$page]);
```

## Listing 9.7: src/Controller/ContactController.php

```
20 $content = $this->twig->render('contact.html', [
21     'title' => 'Contact'
22 ]);
```

## Listing 9.8: src/Controller/ContactController.php

```
29 $content = $this->twig->render('basic.html', [
30     'title' => 'Contact',
31     'content' => "Thank you for your message.",
32 ]);
```

## Template Logic

You may have noticed that we used a different syntax in our latest Twig templates. The first templates we created just made use of the expression delimiters, for example {{ title }}. We now introduce the other type of delimiters, {% ... %}.

The double curly-braces ( {{ ... }} ) always contain expressions. The content is evaluated and printed out. It may contain a single variable, in which case the value of that variable is output. It can contain more complex expressions, and use filters. Twig evaluates the expressions, passes the result through any specified filters, and outputs the result into the template.

We can add logic to our templates using the other style of delimiters ( {% ... %} ). This last example shows them used to define inheritance between templates, and to include one template inside another. We can also use them to add conditional statements to turn on or off parts of a template. They can also be used to add loops that repeat parts of a template.

Let's demonstrate this by adding a navigation to our template using the menu.json configuration file we created earlier. In order to do this we need to make the menu structure available to our Twig templates. You are encouraged to consider different ways of achieving this. As an example, we will create our own template service. At the moment we are using an instance of the Twig_Environment class provided by Twig as our templating service. Instead we can define our own template service that will delegate the work to Twig. This means we will have a single place to add things to the Twig environment. This approach also has the benefit of isolating our dependency on Twig. If all template calls are via a single service class, then it will be easier to adapt our framework if, in the future, we decide to use a different templating engine.

Create a new template to hold our navigation. I've created a subfolder called include in the templates folder which I plan to use for template snippets that can be included into other templates. An example navigation template, based on the navbar component from Bootstrap is shown in listing 9.9. The interesting part is lines 16 - 18 where the for command is used to repeat a section of the template. The nav variable is expected to be a list, and the section is repeated for each item in the list. Listing 9.10 shows the line added to the main index.html template that includes the navigation into the template. It will be automatically included in the basic page and contact templates because they both extend this template.

```
1 <nav class="navbar navbar-default">
2 <div class="container">
3 <div class="navbar-header">
4 <button type="button" class="navbar-toggle collapsed" data-toggle="collapse" data-target="#main-nav" aria-expanded="false">
5 <span class="sr-only">Toggle navigation</span>
6 <span class="icon-bar"></span>
7 <span class="icon-bar"></span>
8 <span class="icon-bar"></span>
9 </button>
10 <a class="navbar-brand" href="/">PHP Weekend</a>
11 </div>
```
