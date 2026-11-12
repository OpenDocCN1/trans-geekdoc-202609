code. What's more, it also guarantees enhanced security by preventing malicious users from altering the structure of the SQL query.

# Introduction to Cross-Site Scripting (XSS)

Cross-Site Scripting (XSS) is a common vulnerability that allows an attacker to inject malicious code (usually JavaScript) into web pages viewed by other users. This attack can occur when user-supplied data is not properly validated or escaped, enabling the attacker to execute code on another user's browser, thus compromising the application's security.

There are three main types of XSS: Reflected XSS, Stored XSS and DOM-based XSS. In the following section, we'll take a closer look at the first two types.

# Reflected XSS

In this type of attack, the malicious code is included in an HTTP request, which is then reflected by the web server in the HTML response. The attacker can then send a link containing the malicious code to the victim, who unwittingly executes it when the link is clicked.

Imagine a website with a search form that displays search results directly on the page. If the site doesn't properly escape special characters, an attacker could insert malicious JavaScript code into the search field. To illustrate this first type of XSS, in the "ebookphp" directory, let's create a new file called "form_search.php" in which we put a simple search form:

```
<!DOCTYPE html>
<html lang="en">
<head>
```