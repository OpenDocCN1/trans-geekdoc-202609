
```
</head>
<body>
<?php
if (isset($_POST["quantity"]) &&
(int)$_POST["quantity"] > 0 &&
isset($_POST["articleId"])) {
file_put_contents(
"orders.txt",
sprintf("%d x article %s - %s\n",
(int)$_POST["quantity"],
$_POST["articleId"],
date("Y-m-d H:i:s")),
FILE_APPEND);
echo "Order submitted!";
}
?>
<form method="post" action="">
Quantity: <input type="text" name="quantity" /><br />
<input type="hidden" name="articleId" value="123" />
<input type="submit" value="Order" />
</form>
</body>
</html>
```

# Listing 32.8 At First Glance, a Harmless Form ("order.php")

To execute the code, the script requires write access to the current directory (more precisely, to the *orders.txt* file). As a general rule, whenever the text "Order submitted!" appears, an order has been placed; for better traceability, this fact is also written to *orders.txt*.

The application now trusts that a POST request to the *order.php* script will always be sent as intended by the user. We have already explained that this does not always have to be the case. For example, consider the following HTML file (with a little JavaScript code):

```
<form method="POST" action="http://victim.xy/php/order.php">
<input type="hidden" name="articleId" value="123" />
<input type="hidden" name="quantity" value="10" />
</form>
<script>
window.onload = function() {
document.forms[0].submit();
}
</script>
```

If you adapt the value of the `action` attribute to your system, you can also use it to place orders unintentionally: Anyone who calls up the HTML file will then place an order with the victim site.

> **Note**
> You will then immediately see the page with the order confirmation in the browser. A "real" attacker would place the hidden form in an iframe, for example, to prevent this effect.

There are numerous approaches to protect yourself from such an attack. These include general security measures such as logging in again before placing an order and short session timeouts. However, there are also frequently suggested measures such as checking the HTTP referrer and checking the IP address, which unfortunately do not always have the desired success in practice.

One protective measure that is currently recognized as secure is the following: The main problem is that an attacker can guess exactly what a corresponding order’s HTTP request looks like. To prevent this, we insert an additional hidden form field that contains a random value. To do so, we let the `random_bytes()` function to determine a corresponding unpredictable string:

```
<?php
$token = random_bytes(32);
?>
...
<input type="hidden" name="token" value="<?php echo $token; ?>" />
```

We save this random value in the session at the same time:

```
$_SESSION["token"] = $token;
```

If the form is now sent, we check whether the value sent with the form is identical to the value in the session. This prevents CSRF attack attempts as an attacker can neither influence the user’s session nor guess in advance what the secret token is, as it is different every time.

In this way, we can use the form from Listing 32.8 with the integration and verification of the token and thus improve it in the next listing.

```
<?php
session_start();
?>
<html>
<head>
<title>Order Form<title>
</head>
```

```
<body>
<?php
$token = "";

if (isset($_POST["quantity"]) &&
(int)$_POST["quantity"] > 0 &&
isset($_POST["articleId"]) &&
isset($_SESSION["token"]) &&
isset($_POST["token"]) &&
$_SESSION["token"] == $_POST["token"]) {
file_put_contents(
"orders.txt",
sprintf("%d x article %s - %s\n",
(int)$_POST["quantity"],
$_POST["articleId"],
date("Y-m-d H:i:s")),
FILE_APPEND);
echo "Order submitted!";
unset($_SESSION["token"]);
} else {
$token = random_bytes(32);
$_SESSION["token"] = $token;
}
?>

<form method="post" action="">
Quantity: <input type="text" name="quantity" /><br />
<input type="hidden" name="articleId" value="123" />
<input type="hidden" name="token" value="<?php echo $token; ?>" />
<input type="submit" value="Order" />
</form>
</body>
</html>
```

# Listing 32.9 The Improved Order Form ("order-token.php")

Try it out: You can still place orders by calling up the form directly. However, if you use the HTML file (for which you must adjust the form dispatch destination), you will land on the "normal" order page, but an order will not be sent automatically or entered in the text file.

> **Note**
> Another additional protective measure against CSRF is the use of SameSite cookies, which have already been discussed in Chapter 14. The following php.ini setting activates a specific SameSite mode for all PHP sessions:

```
session.cookie_samesite = "Lax"
```

Modern web browsers will gradually treat cookies as SameSite=Lax by default, which can make it much more difficult to exploit CSRF gaps.

## 32.7 Screen Scraping and Captchas

The crowning glory: To round off this brief insight into the mindset of attackers, we present a particularly perfidious attack. Imagine you want to offer a page with the current stock market prices, but don't want to pay any fees for the prices yourself. No problem: Simply call up a stock exchange website with PHP in the background, read out the prices (e.g., with regular expressions), and display them on your page—naturally, in your own layout. This sounds good, is also very effective—and is illegal.

> **Note**
> Incidentally, this process is called screen scraping.

Another example: Suppose you want to send as much spam as possible. Freemail providers are suitable for this within certain limits. You could create new accounts there and send advertising emails until the account is blocked and people in uniform are standing outside your door. But it would be much more convenient to use the technique from the previous section, save the registration form locally, analyze it, and then send it back to the server in a modified form—preferably with all of this automated. This would allow you to create several accounts at the touch of a button. Don't laugh: There is software on obscure websites that does exactly that.

These two scenarios have one thing in common: They are very unpleasant for a website because it cannot tell whether a human or a machine is on the other end of the line. Back in the 1950s, the English mathematician Alan Turing defined a test that would make it possible to decide whether a communication partner was a human or a machine. In the year 2000, 50 years later, four researchers joined forces and implemented this concept for the web. They called their creation Completely Automated Public Turing test to tell Computers and Humans Apart (CAPTCHA). In contrast to conventional Turing tests, a captcha runs completely automatically, so no human is needed to check it.

Captchas are now used on many websites. Figure 32.9 shows a captcha that randomly appears and must be solved when accessing the Amazon site.

In this case, a captcha is a graphic that contains a combination of letters and numbers (often just letters) that the user has to type in. The individual characters are distorted in such a way that a computer program has difficulty recognizing the text.

![](img/ae7820c36e8f24c1623d26668b28e80e_885_0.png)

Figure 32.9 A Captcha at "amazon.com"

> **Note**
> The official, but no longer maintained homepage of the CAPTCHA project can be found at www.captcha.net. Additional information on the currently best-known captcha system, reCAPTCHA, can be found at http://s-prs.co/v602290.

However, captchas are not the philosopher's stone but merely a new antidote, which in turn calls for corresponding countermeasures. For example, some scientists have been able to crack the widespread Gimpy captcha relatively reliably.³ Nevertheless, a captcha makes it at least a little more difficult to send a form automatically.

> **Note**
> Certain disadvantages should not be concealed. Graphical captchas require the user to display graphics in their web browser or that the browser can display them at all; users of the Lynx text browser are therefore excluded here. The same applies to visually impaired web surfers. There must therefore be alternatives for this; Yahoo!, for example, provides a hotline.

3 See http://s-prs.co/v602291.
