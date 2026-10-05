# 16.3. CSRF PROTECTION

The csrf package also provides us with a helper to generate tokens for our HTML forms. The package's docs then explain their recommended way of providing this to your HTML forms is to add it as a data field that you pass in to your templates. For instance, we might add this field to our views.Data type.

We are going to take a slightly different approach where we instead add it as a template function. The primary benefit to this approach over the recommended approach is that we can access it in any template, even if no data was passed into the template. This makes it easier to generate forms without having to worry about or not the CSRF token was provided as data to the form.

To do this we are going to look at the Funcs function¹ by the template package. With it we can introduce new functions that are available inside of our templates.

We are going to name the function csrfField and we will start by adding it to all of our templates that we need. We are going to assume that calling the function csrfField will return everything we need to generate a CSRF token hidden input field; that is, we are assuming it returns the entire HTML blob we need, not just a token.

```
$ atom views/galleries/edit.gohtml
```

In the edit gallery template we need to add this function call for every form we create. All four of these templates are shown below, but it is important to note that we are only adding the csrfField function call directly after the form tag. Everything else remains unchanged.

```
{{"editGalleryForm"}}
<form action="/galleries/{{.ID}}/update" method="POST" class="form-horizontal">
<--
  This line will return:
```

> ¹https://golang.org/pkg/html/template#Template.Funcs