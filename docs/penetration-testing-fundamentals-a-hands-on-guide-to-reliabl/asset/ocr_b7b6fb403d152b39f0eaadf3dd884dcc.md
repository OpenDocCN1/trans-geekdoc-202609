An alert is another popular and simple JavaScript function:

```
<script>
alert("You are vulnerable to XSS!");
</script>
```

JavaScript can be used to redirect the browser. In fact, there are several ways to do this:

```
<SCRIPT>
window.navigate("someurl");
</SCRIPT>
```

This one only works in some browsers. You may wish to try one of these two instead:

window.location.href = 'someurl' ; works in all browsers.

window.location.replace ('someurl'); is even better because it does not show in the ‘back’ for history.

You can also use JavaScript to see the browser’s history:

```
history
<SCRIPT>
Window.History
</SCRIPT>
Length: how much is in history
back()
forward()
```

You can loop through the entire history using the length property.

# Things to Do with XSS

A common XSS attack for penetration testers is to just pop up an alert. This lets the person know the site is vulnerable, without actually doing anything. As you can see, you can cause the site to redirect. This is a powerful method for phishing scams.

Consider a website where users can shop and leave reviews of products. The attacker sets up a fake version of the site. If a user navigates to that site, they are prompted to log in, then informed the service is “temporarily unavailable, try again later.” The attacker just got that person’s username and password. But how do you get people to go to the fake website? You could try a phishing email campaign, and you would probably have some success. However, if you can perform XSS on the real website, it can direct the users to the fake website.

As was also mentioned, you can navigate to the history of the browser. Recall the discussion of the difference between GET and POST earlier in this chapter. Imagine you visit a website that is mostly secure, except it uses GET commands. You provide a lot of sensitive information. Then, when you