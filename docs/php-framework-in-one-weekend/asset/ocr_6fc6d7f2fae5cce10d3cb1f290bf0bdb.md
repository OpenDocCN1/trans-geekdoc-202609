```
case '/contact':
$Controller = new ContactController(); return $controller->get();
```

You will get an error if you now try and access /contact. The error is coming from Twig because we have asked it to render a template that does not exist. To get it working create the templates/formsfolder with a contact.htmltemplate form as per listing 7.4.

```
1 <form action="/contact" method="post">
2 <label for="name">Name</label>
3 <input type="text" name="name"><br>
4 <label for="email">Email</label>
5 <input type="text" name="email"><br>
6 <label for="message">Message</label>
7 <textarea name="message" cols="30" rows="10"></textarea><br>
8 <input type="submit" value="Send">
9 </form>
```

# **Listing 7.4:** templates/forms/contact.html

You will also need to update your index.htmltemplate because it will automatically escape the $contentvariable and display the HTML tags. This is the security measure described earlier. We add the rawfilter to disable the automatic escaping in the template, as we know it won’t be user input. But, we will revisit later and see how this can be improved. For now, update your index.htmltemplate file so the content is output raw:

```
<p>{{ content | raw }}</p>
```

You should now see a contact form when you visit /contact. But, because the router doesn’t know the difference between the GET and POST requests you also see the form when you click submit. The submit button causes the form data to be send via a POST request. Let’s add a route to our router to dispatch this to the post() callback on the ContactController.

The HTTP method is available from the $requestobject:
$method = $request->getMethod();

We use this $methodvariable in the router to decide which callback method is called on the controller. Notice that I also pass the $requestvariable so that the post()callback can get the submitted data:

```
case '/contact': $Controller = new ContactController(); if ($method == 'POST')
{
return $controller->post($request); }
return $controller->get();
```

All that remains is to implement the post()request, handle the form data, then respond with a thank you message:

```
public function post(Request $Request) {
// TODO: validate input and send email $content = $this->twig->render('index.html', [ 'title' => 'Contact',
'content' => "Thank you for your message.", ]);
return new Response($content);
}
```

I’ve deliberately left the validation of input and the sending of email as a future task to be implemented later. The important thing here is to see how different controllers can be mapped to different requests, and how different HTTP methods can be mapped to different