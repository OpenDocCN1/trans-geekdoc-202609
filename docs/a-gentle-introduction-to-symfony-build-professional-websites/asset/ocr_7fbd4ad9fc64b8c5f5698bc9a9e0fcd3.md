| Name | Function | Sample Output |
| :--- | :--- | :--- |
| isXmlHttpRequest()\* | Is it an Ajax request? | true |
| isSecure() | Is it an SSL request? | true |
| **Request Parameters** | | |
| hasParameter('foo') | Is a parameter present in the request? | true |
| getParameter('foo') | Value of a named parameter | 'bar' |
| getParameterHolder()->getAll() | Array of all request parameters | |
| **URI-Related Information** | | |
| getUri() | Full URI | 'http://localhost/frontend_dev.php/mymodule/myaction' |
| getPathInfo() | Path info | '/mymodule/myaction' |
| getReferer()\*\* | Referrer | 'http://localhost/frontend_dev.php/' |
| getHost() | Host name | 'localhost' |
| getScriptName() | Front controller path and name | 'frontend_dev.php' |
| **Client Browser Information** | | |
| getLanguages() | Array of accepted languages | Array( [0] => fr [1] => fr_FR [2] => en_US [3] => en ) |
| getCharsets() | Array of accepted charsets | Array( [0] => ISO-8859-1 [1] => UTF-8 [2] => * ) |
| getAcceptableContentTypes() | Array of accepted content types | Array( [0] => text/xml [1] => text/html |

* Works with prototype, Prototype, Mootools, and jQuery
** Sometimes blocked by proxies

You don't have to worry about whether your server supports the $_SERVER or the $ENV variables, or about default values or server-compatibility issues—the sfWebRequest methods do it all for you. Besides, their names are so evident that you will no longer need to browse the PHP documentation to find out how to get information from the request.

# # User Session

Symfony automatically manages user sessions and is able to keep persistent data between requests for users. It uses the built-in PHP session-handling mechanisms and enhances them to make them more configurable and easier to use.

# ## Accessing the User Session

The session object for the current user is accessed in the action with the getUser() method and is an instance of the sfUser class. This class contains a parameter holder that allows you