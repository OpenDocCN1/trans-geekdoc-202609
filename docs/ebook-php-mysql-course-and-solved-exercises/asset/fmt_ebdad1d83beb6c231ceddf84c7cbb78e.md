
# Checking the existence of files in PHP

Checking the existence of files in PHP can be performed using the `file_exists()` function. This function checks whether a file or directory exists at the specified location. Here's an example of how to use the `file_exists()` function to check the existence of a file:

```php
<?php

// File path
$filename = "new_folder/poem1.txt";

// Check file existence
if (file_exists($filename)) {
    echo "The file exists";
} else {
    echo "The file does not exist";
}

?>
```

In this example, the `file_exists()` function is used to check whether the file specified by the `$filename` path exists. If the file exists, a message indicating that the file exists is displayed. Otherwise, a message indicating that the file does not exist is displayed.

## Conclusion

In this chapter dedicated to image and file manipulation in PHP, we've taken a deep dive into the powerful features offered by this programming language. We've explored in detail the various steps involved in loading, displaying, reading and writing files, as well as advanced methods for moving and deleting them. By acquiring these essential skills, you are now armed to create dynamic, interactive web applications that fully exploit the potential of images and files. With your in-depth understanding of these concepts and your mastery of PHP tools, you're ready to take on the most demanding web development challenges.

# Chapter 9: Session and cookie management

Sessions and cookies are essential elements in the development of interactive and dynamic web applications. They store and maintain information about the server and the client, making it easier to personalize the user experience and track browsing activities.

Sessions and cookies are widely used in web development for various functionalities, including:

*   **Authentication and authorization management**: sessions and cookies are used to maintain user login status and restrict access to certain parts of the site.
*   **Temporary data storage**: sessions are used to store temporary data needed to perform certain functions, such as shopping carts in online stores.
*   **Personalizing the user experience**: by storing user preferences such as language, theme, etc., cookies enable you to personalize your browsing experience.
*   **Tracking browsing activity**: cookies are used to collect data on users' interactions with the site, enabling us to analyze trends and personalize content.

In this chapter, we'll explore in detail the management of cookies and sessions in PHP, as well as the best practices and security considerations associated with their use.

## Cookie management

Cookies are small text files stored on users' computers by web browsers. They play an essential role in the operation and personalization of modern websites. Cookies enable websites to remember users' preferences, track their activity and provide a personalized experience.

In this section, we'll explore cookie management in PHP in detail, including the creation, reading, modification and deletion of cookies, as well as good security practices associated with the use of cookies in web development.

Generally speaking, the process of exchanging cookies between the web browser and the web server, stored on the client side, and accessed and manipulated on the server side for various functionalities can be summarized as follows:

1.  The process begins when the web browser sends an HTTP request to the web server to access a page or perform a specific action.
2.  The web server responds to this request by sending HTTP headers, including cookies, to the browser. Cookies are small pieces of data stored in the browser that make it possible to track and identify users as they interact with the site.
3.  The browser stores these cookies on the client side, associating them with the domain and path specified by the server.
4.  The web server sends an HTTP response to the browser, which may contain additional data to be displayed or processed.
5.  When the browser sends new HTTP requests to the server (for example, to access other pages on the site), it automatically includes the cookies associated with the site's domain and path.
6.  The server retrieves these server-side cookies using the `$_COOKIE` superglobal in PHP, allowing them to be accessed and manipulated in the server-side script as required.
7.  Cookies can be manipulated on the server side for various functionalities such as user authentication tracking, content personalization, preference tracking, etc.
8.  With each subsequent request sent by the browser, the associated cookies are automatically included, enabling the server to continue using them to personalize the user's experience.

The following illustration summarizes the cookie exchange process between the client's web browser and the web server:

![Image](images/image-135.png)

In short, cookies are used to store client-side information and transmit it to the server with each request, enabling the server to maintain application state and personalize the user experience.

### Creating and Sending Cookies

To create a cookie in PHP, use the `setcookie()` function. This function takes several parameters, including the cookie name, value, validity time (optional), path (optional) and domain (optional).

![Image](images/image-136.png)

*   **name**: the name of the cookie.
*   **value**: the value associated with the cookie.
*   **expire**: optional, specifies the cookie expiry date as a Unix timestamp. If not specified, the cookie will expire at the end of the session.
*   **path**: optional, specifies the path on the server for which the cookie is available. By default, it is available throughout the site.
*   **domain**: optional, specifies the domain for which the cookie is available. By default, it is available for the current domain.
*   **secure**: optional, specifies whether the cookie should be transmitted via HTTPS only. By default, it is set to false.
*   **httponly**: optional, specifies whether the cookie is accessible via HTTP only and not via JavaScript. By default, it is set to false.

A cookie can store various types of information, such as session identifiers, user preferences, language settings, tracking data and so on. Here's a practical example of what can be stored in a cookie:

Suppose a website allows the user to choose their favorite theme from a selection of themes. Once the user has chosen a theme, the site can store this information in a cookie so that the next time they visit the site, they will see the same theme they had previously selected.

Example of code to store the preferred theme in a cookie:

```php
<?php

// Setting cookie name and value
$name = "user";
$theme_value = "Alice Dupont";

// Set cookie lifetime (1 hour)
$expiration = time() + 3600; // current timestamp + 3600 seconds (1 hour)

// Set the path for which the cookie is valid (the whole site)
$path = "/";

// Set the domain for which the cookie is valid (current domain)
$domain = "";

// Create cookie with setcookie()
setcookie($name, $theme_value, $expiration, $path, $domain);

// Display a confirmation message
echo "The cookie has been created successfully";

?>
```

In this example:

*   The cookie name is set to "user" and its value to "Alice Dupont".
*   The cookie expires after 1 hour (3600 seconds) from the time it is created.
*   The path is defined as "/" to indicate that the cookie is valid throughout the site.
*   The domain is left empty, which means that the cookie is valid for the current domain.
*   Finally, the `setcookie()` function is used to create the cookie with the specified parameters.
*   After executing this code, a cookie named "user" with the value "Alice Dupont" will be created, valid for one hour.

Result:

![Image](images/image-137.png)

### Reading Cookies
