# CHAPTER 13. DISPLAYING ERRORS TO THE END USER

That means we could update our bootstrap template with code similar to the code below.

```
<div class="container-fluid">
{{if .}}
  {{template "alert" .}}
  {{end}}
  {{template "yield" .}}
  {{template "footer"}}
</div>
```

Note: We won't be using this code; it is meant for illustration purposes only.

In the code above we will check to see if any non-empty data was passed into our template, and if it was we would try to render the alert template using that data. We would then continue to pass that same data into the yield template as well.

That list sounds problematic. We don't want to render the alert if there is any data in our template, but instead want to render it when specifically is an alert message. We also don't want to pass the alert message into our yield template, but rather pass data meant to be rendered there.

Let's head back to our users controller and look at one way to solve this problem.

```
$ atom controllers/users.go
```

We know we want to separate our alert data from the data used to render our yield template, so why don't we simply create a type that has two fields - Alert and Yield. Then we will know for which piece of data is intended for each template.

Note: In case you forgot, the yield template is used to render each specific page. For example, we use it to render the sign up form, the home page, and any non-layout information.