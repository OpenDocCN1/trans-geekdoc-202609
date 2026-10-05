# 4.4. CREATING A TEMPLATE

Box 4.3. Potential issues with auto-importing.

If you are using a plugin to automatically import packages for you, you might need to take a moment to make sure it imports the correct template package.

Go’s standard library ships with both a text/template and an html/template package, and both used nearly identically, so auto-importers have a hard time determining which you intended to use.

As a result, it is always a good idea to verify that you are using the template package you intended after writing code that uses templates. In this case we want the html/template package to be imported.

After calling ParseFiles we to see if an error was returned. If an error is present we panic. Otherwise we continue on our program knowing we have a valid template referenced by the t variable.

Next up we create the data variable, which is an anonymous struct with a Name field. When we instantiate data we set the Name field to “John Smith”.

Finally we execute the template we created earlier, passing in two arguments:

+   1. Where we want to write the template output
2. The data to be used when executing the template

In our case, we want to write the template output to Stdout, which is your terminal window. This is where functions like fmt.Println to write by default, and it is provided to us by the os package in Go’s standard library.

We also want to provide our template with the data it needs to render the template. In Listing 4.3 we use the line {{ .Name }} to render a name dynamically,