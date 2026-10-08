# 502 Chapter 23 Integrating JavaScript and PHP

```
$(\#last_name').attr('placeholder', 'Appleseeded');
});

$('#myForm').on('submit', function(event) {
  var first_name = $('#first_name').val();
  var last_name = $('#last_name').val();

  webConsole("The form was submitted;");
  alert("Hello, " + first_name + " + " + last_name + "!");
});

$('.name').on('focusout', function(event) {
  var nameField = $(event.target);
  webConsole("Name field ' + 
    nameField.attr('id') + 
    "' was updated to '" + 
    nameField.val() + 
    """);
});

</script>
<body>
</html>
```

As you can see, we have made significant additions to our original HTML by including a number of JQuery event handlers to breathe life into this static document. The first thing we will discuss is the webConsole function we have defined as below:

```
var webConsole = function(msg) {
  var console = $('#webConsole');
  var newMessage = $('<<p>').text(msg);

  console.append(newMessage);
};
```

This function will be used at various points in the rest of our application to provide some real-time output of the script console. We accomplish this by appending a new paragraph <p> elements within an <div> element with the webConsole ID every time a new message is to be displayed. This is a great example of how to use jQuery to select, create, and then manipulate a loaded document using JavaScript.

Now that our helper function is out of the way, let's get into the actual functionality of our jQuery app with the first piece of JavaScript that will be executed once the document loaded:

```
$(document).on('ready', function () {
  $(\#first_name').attr('placeholder', 'Johnny');
  $(\#last_name').attr('placeholder', 'Appleseeded');
});
```