# Template Logic

You may have noticed that we used a different syntax in our latest Twig templates. The first templates we created just made use of the expression delimiters, for example {{ title }}. We now introduce the other type of delimiters, {% ... %}.

The double curly-braces ( {{ ... }} ) always contain expressions. The content is evaluated and printed out. It may contain a single variable, in which case the value of that variable is output. It can contain more complex expressions, and use filters. Twig evaluates the expressions, passes the result through any specified filters, and outputs the result into the template.

We can add logic to our templates using the other style of delimiters ( {% ... %} ). This last example shows them used to define inheritance between templates, and to include one template inside another. We can also use them to add conditional statements to turn on or off parts of a template. They can also be used to add loops that repeat parts of a template.

Let's demonstrate this by adding a navigation to our template using the menu.jsonconfiguration file we created earlier. In order to do this we need to make the menu structure available to our Twig templates. You are encouraged to consider different ways of achieving this. As an example, we will create our own template service. At the moment we are using an instance of the Twig_EnvironmentClass provided by Twig as our templating service. Instead we can define our own template service that will delegate the work to Twig. This means we will have a single place to add things to the Twig environment. This approach also has the benefit of isolating our dependency on Twig. If all template calls are via a single service class, then it will be easier to adapt our framework if, in the future, we decide to use a different templating engine.

Create a new template to hold our navigation. I've created a subfolder called include in the templates folder which I plan to use for template snippets that can be included into other templates. An example navigation template, based on the navbarComponent from Bootstrap is shown in listing 9.9. The interesting part is lines 16 - 18 where the for command is used to repeat a section of the template. The navvariable is expected to be a list, and the section is repeated for each itemin the list. Listing 9.10 shows the line added to the main index.htmltemplate that includes the navigation into the template. It will be automatically included in the basic page and contact templates because they both extend this template.

```
1 <nav class="navbar navbar-default">
2 <div class="container">
3 <div class="navbar-header">
4 <button type="button" class="navbar-toggle collapsed" data-toggle=" collapse" data-target="#main-nav" aria-expanded="false">
5 <span class="sr-only">Toggle navigation</span>
6 <span class="icon-bar"></span>
7 <span class="icon-bar"></span>
8 <span class="icon-bar"></span>
9 </button>
10 <a class="navbar-brand" href="/">PHP Weekend</a>
11 </div>
```