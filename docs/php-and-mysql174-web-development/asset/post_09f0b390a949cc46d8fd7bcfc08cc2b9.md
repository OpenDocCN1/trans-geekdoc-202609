
```php
} catch(\Exception $e) {
    print json_encode({
        'success' => false,
        'error' => $e->getMessage()
    });
}
```

We start our chat server by enabling sessions and output buffering by calls to the session_start() and ob_start() functions. We then set a Content-Type response header with the value of application/json to ensure the requesting client knows we will be returning a JSON document as a response. So that your timeouts are all lined up, you use date_default_timezone() to match the timezone for our server.

With the basics out of the way, we then open a database connection to MySQL and check to see that the connection is good—if it is not, we exit immediately because a lack of a database at this stage means a pretty boring chat with no messages to display to any user.

However, with our database connection ready, we figure out exactly how the script should respond to the request at hand. In our case, we are going to define the action we take by the nature of the request we receive from the user interface. For HTTP GET requests, we will retrieve a list of messages that be seen by the user and return them to the screen. For HTTP POST requests (form submissions), we will accept a new message to broadcast to all the other users.

Regardless of the nature of the request, this script always returns a JSON object that has a key called success that returns a true or false depending on the success of the operation. If fail, we will also provide an error key with an error message. If we are handling an HTTP GET request we additionally return a messages containing a list of messages the client should render.

Listing 23.2 is a simple PHP script that employs several concepts you have seen throughout this to insert or retrieve information from a database. The key to this script, however, is in how it is executed. The intention is that this script will be executed at regular intervals by the user’s browser via AJAX to update the interface with any messages received. Currently, the browser interface will also provide the ability to send a message using AJAX back to the server to be broadcast to anyone else looking in the chat as well. Let’s move on now by taking a look at the client side of our application and the AJAX methods we will use.

## The jQuery AJAX Methods

Before we build the simple user interface for our application, let’s return to the discussion of jQuery by introducing the various methods available to performing AJAX requests. Fundamentally, the AJAX methods you will learn about in the next sections are all simplified versions of a single API method—$.ajax() method.

## The jQuery $.ajax() Method

From a prototype perspective, the $.ajax() method is rather simple:

```javascript
$.ajax(string url, object settings);
```

The first parameter of the method is the URL which you want to perform the asynchronous request, and the second parameter includes any settings for that request. The complexity of this method doesn't reveal itself unless you want to examine the numerous settings that are available to control basically every detail of that request and its response. Since all of these various settings are well-documented in the jQuery documentation for the method, we won't discuss every one of them here—feel free to use /api.jquery.com/jquery/ajax/ or at a later date. Rather, we will introduce a few cases and how they are achieved using the $.ajax() method.

The first example performs a HTTP GET request. The success property is a function that is called upon success of the request, and is populated with the data retrieved during the request, the textual status of the request, and the jQuery request itself.

```javascript
// Perform a HTTP GET request
$.ajax('/example.php', {
  'method': 'GET',
  'success': function(data, textStatus, jqXHR) {
    console.log(data);
  }
});
```

The next example performs a HTTP POST request that includes some data to the server. Upon success, just as was true with our earlier GET request, the function attached to the success property is called. However, in this case, we also have a function attached to the error property. This function is called in the event of an error (as the server returning a HTTP 500 status), and its results can be used to inform the user interface:

```javascript
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

```javascript
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

```javascript
// Make a request using HTTP
$.ajax('/example.php', {
  'method' : 'GET',
  'username' : 'myusername',
  'password' : 'mypassword',
  'success' : function (data, textStatus, jqXHR) {
    console.log(data);
  }
});
```

Depending on the nature of the request, and how closely you want to control the request, you may use one of the helper methods instead of $.ajax() method.

## jQuery Helper Methods

In many cases the flexibility provided by $.ajax() described above are a bit overkill for the developer. For this reason, jQuery provides several helper methods that encapsulate common use. Easy use of these methods comes at a price, as sometimes they lack functionality like error handling that is built into $.ajax() method.

```javascript
// Simplified GET requests
$.get('/example.php', {
  'queryParam' : 'paramValue',
  function (data, textStatus, jqXHR) {
    console.log(data);
  }
});
```

## Integrating JavaScript and PHP

The $.ajax() method is built-in. For the $.get() method, we simply pass the URL we are requesting (in the form of a JavaScript object), and the callback to use when the request returns successfully. If an error occurs while performing the request, the $.get() method silently fails.

One might think, there is a corresponding $.post() method that functions in an identical fashion (except performing an HTTP POST):

```javascript
// Simplified POST requests
$.post('/example.php', {
  'postParam' : 'paramValue',
  function(data, textStatus, jqXHR) {
    console.log(data);
  }
});
```

There are two additional methods that can be useful under certain circumstances beyond the simple HTTP and HTTP POST. The first is $.getJSON() method, which dynamically loads a JavaScript document from the server and executes it in a single command:

```javascript
$.getJSON('/path/to/my.js', function() {
  // my.js has been loaded and any functions defined can now be used
});
```

In a similar fashion, the $.JSON() method performs an HTTP GET request to the specified URI, parses the return value as a JSON document, and makes it available to the callback function:

```javascript
// Load a JSON document via HTTP GET
$.JSON('/example.php', {
  'jsonParam' : 'paramValue',
  function(data, textStatus, jqXHR) {
    console.log(data.status);
  }
});
```

## The Chat Client/jQuery Application

We have the backend script (chat.php from Listing 23.3) all ready, so now we need to build a jQuery-based front end to display a meaningful user interface to the end user—one that allows both input and retrieval of messages. For these purposes we will start by building a simple HTML interface using the Bootstrap CSS framework for its layout and a little customized CSS to render the popular "chat bubble" style of widget for each chat message we display (see Listing 23.4).

Note

> For the CSS styling used to render the fancy-looking chat bubbles we used a great online tool by John Clifford called "Bubbler," which can be found at http://likepixels.co.uk/drop/bubbler/.
