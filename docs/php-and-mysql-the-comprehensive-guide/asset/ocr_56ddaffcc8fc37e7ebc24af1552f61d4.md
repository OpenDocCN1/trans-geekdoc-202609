# Sample Test

The previous checks were rather trivial. Fields were mandatory, meaning that they had to contain something. Of course, this is only a small subset of what is actually possible. In the example form, there is an Email field, which should of course contain an email address. It is clear how the check takes place here: it is checked for a regular expression.² Depending on whether the user input matches the search pattern or not, the variable $ok is set to false or left as it is. Consider the following corresponding code snippet:

```
if (!isset($_POST["Email"]) ||
   trim($_POST["Email"]) == "" ||
   !preg_match(
      '/^[-a-zA-Z0-9\._-]+@[a-zA-Z0-9\.-]+\.[a-zA-Z]{2,6}$/',
      $_POST["Email"])) {
   $ok = false;
}
```

The regular expression looks wild, but only says this: There is a series of permitted characters, a bracket, then many permitted characters, including at least one dot, and after that two to six characters, the domain extension. Of course, there are much more detailed and probably better validation expressions for emails, but nobody goes to the trouble to rummage through the associated RFC (www.ietf.org/rfc/rfc2822.txt). In principle, it is only a matter of catching unintentional input errors, so strictly speaking, a check for an @ sign would almost suffice.³ With the increasing spread of international domain names, there is a problem anyway, as the regular expression does not recognize permitted special characters such as umlauts in the domain name; the \w expression may help here.

# Here are two more useful expressions:

+   * ^\((?w-)?\(\d{5}\))$ (for a US postal code)
+   * ^\(\d|1?\d\d|2[0-4]\d|25[0-5])\.\(\d|1?\d\d|2[0-4]\d|25[0-5])\.\(\d|1?\d\d|2[0-4]\d|25[0-5])\.\(\d|1?\d\d|2[0-4]\d|25[0-5])$ (for a valid IP address [IPv4])

2 In this case, it is advisable to go back to Chapter 10, where regular expressions are discussed in detail.

3 A little anecdote at this point: In a private project, the author of these lines wanted to implement a particularly strict syntax check of email addresses. But that didn't help: Two people mistyped and ended their email addresses with .ed instead of .de. The only thing that helps here is the use of two text fields for email addresses as the probability of someone mistyping the same email address twice is low. On the other hand, the probability that the email address will be typed once (incorrectly) and then copied and pasted into the second field is rather high.