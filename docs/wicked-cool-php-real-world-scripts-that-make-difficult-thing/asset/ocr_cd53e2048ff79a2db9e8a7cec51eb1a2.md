All web browsers understand this, but automatic page crawlers sometimes do not. In addition, this intermediate page will show up in the user’s browser history.

# #60: Forcing a User to Use SSL-Encrypted Pages

When handling credit card information, you want to guarantee that all card information always goes through an SSL (Secure Socket Layer) connection.

If a user types www.example.com in his web browser, he gets http://www .example.com/, not https://www.example.com/. This isn’t a problem if all of your forms specifically refer to pages under https://www.example.com/, but it’s difficult to ensure that and to maintain it if your hostname happens to change.

Here is a simple function to see if a user is connecting via SSL or not:

```
function is_SSL() {
/* Checks to see whether the page is in secure mode */
if ($_SERVER['SERVER_PORT'] == "443") {
return true;
} else {
return false;
}
}
```

This function works by checking the port through which the client connected to the server (SSL is port 443). If the access is not secure and it should be, you can use $_SERVER[’PHP_SELF’] and the header() function described in the preceding section to redirect to a secure version of the page.

# #61: Extracting Client Information

Webservers can extract information about their connecting clients by looking at TCP/IP status and HTTP headers. You can access the client’s IP address and browser version fairly easily through PHP variables. However, like almost anything the client sends you, this information is completely useless for session tracking. IP addresses aren’t unique because of proxies and Network Address Translation (NAT), and browser versions can be completely bogus.

This information is, however, good for finding basic statistics about your users. A few bogus headers here and there aren’t going to matter if you’re looking at 100,000 accesses.

The following function extracts an IP address. The first part is relatively simple, because it looks into what the server thinks it knows about the client:

```
function get_ip() {
/* First, look for an IP address from the server. */
if (!empty($_SERVER["REMOTE_ADDR"])) {
$client_ip = $_SERVER["REMOTE_ADDR"];
}
```