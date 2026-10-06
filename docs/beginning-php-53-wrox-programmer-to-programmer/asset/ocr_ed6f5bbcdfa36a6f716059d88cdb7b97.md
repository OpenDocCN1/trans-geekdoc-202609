# Part III: Using PHP Practice

Because you know that the start field will only ever contain digits, there's no need to URL-encode the values in this situation. However, if there's any chance your field values might contain reserved characters, you should use urlencode() or http_build_query() as discussed earlier in the chapter.

# Working with Cookies

So you've looked up query strings, and in the previous chapter, hidden form fields as ways to preserve an application's state between browser requests. Though perfectly adequate for small amounts of temporary data, these techniques become unwieldy when you need to store larger amounts of data for long periods of time. For example, you might want to allow each user to choose a font size for the text on your Web site. If the user has chosen the size, you'd need to pass this value — whether a hidden form field or in a query string — between every single page request on the Web site, so that your application can read the value and set the font size for each page. This would be arduous to implement.

Cookies are a somewhat sophisticated approach to this problem. A cookie lets you store a small amount of data — no more than 4KB — within the browser itself. Then, whenever the browser requests a page on your Web site, all the cookie is automatically sent to the server within the request. This means you can send the data to the cookie, and the data is automatically available to your script from moment onwards.

You can make a cookie for a fixed amount of time — from a few to several years if you like — or can set a cookie to expire once the browser application is closed. Modern browsers can store up to 30 cookies per Web domain.

Although cookies are somewhat more secure than using query strings — for example, a browser (by default) only sends cookies to the Web site that created them — they are still easy for attackers to tamper with. You shouldn't rely on cookies to identify or authenticate your users. Furthermore, it's easy to turn off cookie support in browsers, and many do so. This means that your Web site shouldn't rely on cookies for essential functionality — or, if it does, it should prompt you to enable cookies for your Web site if necessary.

However, if you need to store non-critical data, such as preferences, on an ongoing basis, then cookies are a useful tool.

> Here's a tip: most browsers let you view, as well as delete, any cookies stored by the browser. For example, in Firefox choose Edit -> Preferences (Firefox on the Mac), then choose Privacy and click the Cookies button.

# Cookie Components

A cookie is sent from the server to the browser as part of the HTTP headers. Here's an example of an HTTP header to create a cookie:

```
Set-Cookie: fontSize=3; expires=Tuesday, 6-Jan-2009 17:53:08 GMT; path=/; domain=.example.com; HttpOnly
```