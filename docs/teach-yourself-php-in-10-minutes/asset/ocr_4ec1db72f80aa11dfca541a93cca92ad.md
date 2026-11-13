# Submitting a Form to PHP

In case you are not familiar with HTML forms at all, let's begin by looking over what is involved in creating a web page that can collect information from a user and submit it to a web script.

# The <FORM> Tag

The HTML <FORM> tag indicates an area of a web page that, when it contains text-entry fields or other form input elements, submits the values entered by a user to a particular URL.

The ACTION attribute in a <FORM> tag indicates the location of the script that the values are to be passed to. It can be a location relative to the current page or a full URL that begins with http://.

The METHOD attribute indicates the way in which the user's web browser will bundle up the data to be sent. Two methods, GET and POST , vary visibly only slightly. Form data submitted using the GET method is tagged on to the end of the URL, whereas the POST method sends the data to the web server without its being visible.

> The GET Method You have probably seen URLs with GET method data attached, even if you didn't know that's what was going on. If you've ever use the search box at a website and the page address has come back with ?search=yourword , it submitted the form by using the GET method.

In most situations where you are using an HTML form, the POST method is preferable. It is not only better aesthetically because the submitted values are not revealed in the script URL but there is no limit on the amount of data that can be submitted in this way. The amount of data that can be submitted by using the GET method is limited by the maximum URL length that a web browser can handle (the limit in Internet Explorer is 2,048 characters) and the HTTP version on the server (HTTP/1.0 must allow at least 256 characters, whereas HTTP/1.1 must allow at least 2,048).

# The <INPUT> Tag

The <INPUT> tag is used to add one of several types of form input to a web page. The type of input item is specified in the TYPE attribute, and the simplest type is a TEXT input item.

To create a TEXT input item that is suitable for entering a user's email address, you could use the following HTML:

```
<INPUT TYPE="TEXT" NAME="name" SIZE="30" VALUE="">
```