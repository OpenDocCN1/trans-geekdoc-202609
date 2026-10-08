# The jQuery $.ajax() Method

From a prototype perspective, the $.ajax() method is rather simple:

```
$.ajax(string url, object settings);
```

The first parameter of the method is the URL which you want to perform the asynchronous request, and the second parameter includes any settings for that request. The complexity of this method doesn't reveal itself unless you want to examine the numerous settings that are available to control basically every detail of that request and its response. Since all of these various settings are well-documented in the jQuery documentation for the method, we won't discuss every one of them here—feel free to use /api.jquery.com/jquery/ajax/ or at a later date. Rather, we will introduce a few cases and how they are achieved using the $.ajax() method.

The first example performs a HTTP GET request. The success property is a function that is called upon success of the request, and is populated with the data retrieved during the request, the textual status of the request, and the jQuery request itself.

```
// Perform a HTTP GET request
$.ajax('/example.php', {
  'method': 'GET',
  'success': function(data, textStatus, jqXHR) {
    console.log(data);
  }
});
```

The next example performs a HTTP POST request that includes some data to the server. Upon success, just as was true with our earlier GET request, the function attached to the success property is called. However, in this case, we also have a function attached to the error property. This function is called in the event of an error (as the server returning a HTTP 500 status), and its results can be used to inform the user interface:

```
// Perform an HTTP POST request with error handling
$.ajax('/example.php', {
  'method': 'POST',
  'data': {
    'myBoolean': true,
    'myString': 'This is some sample data.'
  },
  'success': function(data, textStatus, jqXHR) {
    console.log(data);
  },
  'error': function(jqXHR, textStatus, errorThrown) {
    console.log("An error occurred: " + errorThrown);
  }
});
```

If you would like to add headers to your HTTP request, such as add authentication values, you can do so by using the headers and specifying the key / value pairs of the headers you wish to send, as below: