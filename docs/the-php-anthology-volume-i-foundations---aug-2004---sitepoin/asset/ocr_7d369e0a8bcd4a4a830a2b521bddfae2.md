Each of these URLs is the root of an application. If a site is well constructed, these will be integrated so that, for example, if downloading a file requires a user name and password, the same user name and password is used for the forum.

Within each application, there are *views* that correspond to the different page types your site’s visitors will see. For example:

`http://www.example.com/forums/discussion/php`
a view of the PHP discussion forum

`http://www.example.com/forums/discussion/php/34`
a view of a message in the PHP forum

Each view has a default appearance but may be able to accept additional *parameters*. For example:

`http://www.site.com/forums/discussion/php/?sort=popularity`
orders the posts in terms of their popularity

`http://www.site.com/forums/discussion/php/?sort=date&numposts=10`
shows the latest ten posts on the forum

See what I’m suggesting here? Applications and views are identified by a URL suffix, while parameters used by that view are identified by standard query string variables.

Making this division between views and parameters can really help in structuring the PHP that powers the site. Determining which application and view a visitor to your site has requested requires a fixed number of variables that can be identified by their relative position within the URL. By contrast, a particular view will often make use of a number of parameters, not all of which will be present at the same time. Parameters, therefore, are best identified with name/value pairs, which a query string makes possible.

Using URL suffix values in your code requires a little planning. Consider again this URL:

`http://www.site.com/forums/discussion/php/`

You can only access the variables by their index—the position in which they appear in the URL. With the above URL you might use **PathVars** to retrieve an array containing the variables: