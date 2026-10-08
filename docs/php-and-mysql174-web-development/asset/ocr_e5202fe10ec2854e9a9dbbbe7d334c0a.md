```
// Sending headers with a GET request
$.ajax('/example.php', {
  'method' : 'GET',
  'headers' : {
    'X-my-auth' : 'SomeAuthValue'
  },
  success: function (data, textStatus, jqXHR) {
    console.log(data);
  }
});
```

In modern versions of jQuery, when specifically using the HTTP authentication protocol during an AJAX request, you no longer need to use HTTP authentication headers before sending them in the request. You can simply use the username and password settings to specify the HTTP authentication credentials:

```
// Make a request using HTTP Auth
$.ajax('/example.php', {
  'method' : 'GET',
  'username' : 'myusername',
  'password' : 'mypassword',
  'success' : function (data, textStatus, jqXHR) {
    console.log(data);
  }
});
```

Depending on the complexity of your AJAX requests, and how closely you want to control the request itself, you may be able to use one of the various AJAX helper-methods instead of the complexity of the $.ajax() method and all of its settings. In the next section we'll walk you through some simplified AJAX methods for making requests to a web server, before jumping in your jQuery and PHP-driven application.

# jQuery AJAX Helper Methods

In many cases the flexibility and complexity provided by the $.ajax() method described above are a bit of overkill for the developer. For this reason, jQuery provides several AJAX helper methods that encapsulate common use. Easy use of these of these methods comes at a price, as sometimes they lack functionality like error handling that is built in to the $.ajax() method.

For example, the following is a considerably straightforward way to perform an HTTP GET request for a resource on the server:

```
// Simplified GET requests
$.get('/example.php', {
  'queryParam' : 'paramValue',
  function (data, textStatus, jqXHR) {
    console.log(data);
  }
});
```