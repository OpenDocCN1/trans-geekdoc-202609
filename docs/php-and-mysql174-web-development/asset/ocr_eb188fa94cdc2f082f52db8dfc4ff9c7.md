will, upon loading of the HTML document, add new placeholder attributes to the input fields with the IDs of first_name and last_name, respectively. To the end user, this process happens fast enough that it is nearly indistinguishable from including those attributes statically within the HTML document.

Since all of the remaining code is in the form of event listeners, there is no logical progression to the next piece of code we use. Let's pick one at random and look at the code that handles the focusout event for our input events:

```
$('.name').on('focusout', function(event) {
  var nameField = $(event.target);
  console.log('Name field ' + \
    nameField.attr('id') + \
    ' updated to ' + \
    nameField.val() + \
    ');
});
```

Using losing (presumably the user entered some data into the <form> element), the focusout event will be triggered and our function called. The function examines the element that triggered the event (by using the target property of the passed event object) and creates a message using the console function previously explained. The result is a real-time updating of the web page every time the user changes the input of either form element. You can see some examples of these messages in Figure 23.1.

![](bbox=[0.141, 0.542, 0.727, 0.816])

Figure **23.1** Performing actions in the jQuery-enabled form shows a log to the user