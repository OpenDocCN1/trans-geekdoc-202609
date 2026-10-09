# There's more...

**PHP Standards Recommendations (PSR-7)** precisely defines request and response objects to be used when making requests between PHP applications. This is covered extensively in Appendix, Defining PSR-7 Classes.

# See also

For more information on Streams, see this PHP documentation page http://php.net/manual/en/book.stream.php. An often asked question is "what is the difference between HTTP PUT and POST?" for an excellent discussion on this topic please refer to http://stackoverflow.com/questions/107390/whats-the-difference-between-a-post-and-a-put-http-request. For more information on obtaining an API key from Google, please refer to these web pages:

https://developers.google.com/maps/documentation/directions/get-api-key

https://developers.google.com/maps/documentation/directions/intro#Introduction

# Creating a simple REST server

There are several considerations when implementing a REST server. The answers to these three questions will then let you define your REST service:

+   > How is the raw Request captured?

+   > What **Application Programming Interface (API)** do you want to publish?

+   > How do you plan to map HTTP verbs (for example, GET, PUT, POST, and DELETE) to API methods?

# How to do it...

+   1. We will implement our REST server by building onto the request and response classes defined in the previous recipe, *Creating a simple REST client*. Review the classes discussed in the previous recipe, including the following:

+   - `Application\Web\AbstractHttp`

+   - `Application\Web\Request`

+   - `Application\Web\Received`