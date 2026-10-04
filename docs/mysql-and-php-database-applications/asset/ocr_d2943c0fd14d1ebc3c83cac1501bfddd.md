# # Appendix A

# # HTML Forms

IF YOU WANT YOUR APPLICATIONS to take user data, you are going to need a place for them to enter the information. That requires HTML forms. HTML forms are easy enough to work with. There are several commonly used input types, and in browsers that make use of HTML 4.0 and Cascading Style Sheet there are some techniques that you can use to make your forms bit fancier. A full discussion of everything you can do with forms is beyond the scope of this book. If you need more information on forms and how they can work with CSS or JavaScript, or some of the newer-browser specific form types, check out the documentation at http://microsoft.com or http://mozilla.org.

# # Form Basics

Each form is delimited by opening and closing `<form>` tags. The `<form>` tag has the following attributes:

+   - action—This attribute specifies the URL of the page that a form will be sent to processing. It can contain a relative URL (e.g., "myscript.php") or a complete URL (e.g., http://www.mydomain/myscript.php/).
- method—This attribute indicates the HTTP request type the browser will send to the server. It must be set to either GET or POST. If you set it to GET, the name=value pairs will appear in the browser location bar (e.g., http://mypage.com?name=value&name2=value2). The advantage of using GET is that results can be bookmarked. The disadvantage is that the variables will be more transparent. If you set this attribute to POST the name=value pairs will not be visible. The default value is GET.
- name—This attribute is most useful for addressing portions of a form through JavaScript. The form name is not sent to the server when the form is submitted.
- enctype—The default is "application-x-www-form-urlencoded", and this will normally be fine. But if you are uploading files (using `<input type="file">`), you should use "multipart/form-data".