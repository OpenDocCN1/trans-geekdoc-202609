
# Start with the Right Mindset

Security is not a feature. When you are writing a web application and deciding the list of features you want to include, security is not something that you casually include in the list and assign a developer to work on for a couple of days. It must be constantly part of the design of the application, and it is a never-ending effort, even after the application is deployed and development has slowed, if not outright ceased.

By thinking of and planning for it, from the beginning, the various ways in which our system could be abused or through which attackers might try to compromise it, we can design our code to reduce the likelihood of these problems occurring. This also saves having to retrofit every later when we finally turn our attention to the problem (when we are almost certain with many more potential problems).

# Balancing Security and Usability

One of the greatest concerns we have when designing a system is user passwords. Users will often choose passwords that are not particularly difficult to crack with software, especially when they use readily words in dictionaries. We would like to reduce the risk of a user's password being guessed and our system compromised through this.

One possible solution is to require each user to go through four login dialogs, each with a separate password. We also require that the user change these four passwords at least once a month and make sure the user never uses the password she has used in the past. We would require these to be long, and include many different character classes (uppercase, lowercase, punctuation, and numbers, for example). This would make our system much more secure, and crackers would have to spend significantly more time getting through the login process and into the compromised system.

Unfortunately, our system would be so secure that nobody would bother to use it—at some point they would decide that it is not worth it. This illustrates the point that security is as important as it is also important to worry about how this affects usability. An easy-to-use system with little security might appear attractive to users, but will also result in a higher probability of security-related problems and possible business interruptions. Similarly, a system that is so robust as to be borderline unusable will attract few users and very negatively affect our business.

As web designers, we must look for ways to improve our security without disproportionately affecting the usability of the system. With all things related to the user interface, there are no hard and fast rules to follow, so instead we must rely on some personal judgment, usability testing, and focus groups to see how users react to our prototypes and designs.

# Monitoring Security

After we developing our web application and deploy it to production for people to begin using, our job is not complete. Part of security is monitoring the system as it operates, looking at logs and other files to see the system is performing and being used. Only by keeping a close eye on the operation of the system (or by writing and running tools to portions of this for us), we can see whether ongoing security problems exist and find areas where we might need to spend some time developing more secure solutions.

Security is, unfortunately, an ongoing battle and, in a certain hyperbolic sense, a battle that can never be won. Constant vigilance, improvements to our system, and rapid reaction to any problems are the price to be paid for a smoothly operating web application.

# Our Basic Approach

To give ourselves the most security solution possible for reasonable effort and time, we describe in this book twofold approach to security. The first part follows along the lines of what we have discussed thus far: how to plan for securing our application and designing features into it that will keep it safe. We were compulsive labelers, we might call this a top-down approach.

In contrast, we might call the second part of our security approach bottom-up approach. This is what we will cover in this chapter. In this phase we look at all the individual components in our application, as the database server, the server itself, and the network on which it resides. We try to ensure that not only are our interactions with these components safe, but that the installation and configuration of these components is safe. Many products install with default configurations that leave us open to attack, and we would do well to learn about these holes and plug them.

# Securing Your Code

Making a effort at securing your code requires you to think at a granular level, inspecting each of the components individually and looking at how to improve their security. We begin in this section by investigating the things we can do to keep our code safe. Although we cannot know everything you might want to do to cover all possible security threats (entire to have been devoted to these subjects), we can at least give some general guidelines and point you in the right direction.

# Filtering User Input

One of the most important things we can do in our web applications to make them more secure is to filter all user input.

Application developers must filter all input that comes from external sources. This does not mean that we should design a system with the assumption that all our users are crooks. We still want them to feel welcome and encourage them to use our web application. We just want to be sure that we are prepared at any point for misuse of our system.

If we do this filtering effectively, we can reduce the number of external threats substantially and massively improve the robustness of our system. Even if we are pretty sure that we trust the users, we cannot be certain that they do not have some type of spyware program or other such thing that is modifying or sending new requests to our server. So really, never trust the users.

Given the importance of filtering the input we get from external customers, we should take a look at the ways in which we might do this.

# Double-Checking Expected Values

At times we will present the user with a range of possible values from which to choose, things such as shipping (ground, express, overnight), state or province, and so on. Now, if we have to follow the following simple form, as shown in Listing 15.1:

Listing 15.1 simple_form.html—Just a Simple Form

```
<!DOCTYPE html>
<html
<head>
<title>What be ye laddie?</title>
</head>
<body>
<h1>What be ye laddie?</h1>
<form action="submit_form.php" method="post">
<p>
<input type="radio" name="gender" id="gender_m" value="male" />
<label for="gender_m">male</label><br>
<input type="radio" name="gender" id="gender_f" value="female" />
<label for="gender_f">female</label><br>
<input type="radio" name="gender" id="gender_o" value="other" />
<label for="gender_o">other</label><br>
</p>
<button type="submit" name="submit">Submit Form</button>
</form>
</body>
</html>
```

This form could look like in Figure 15.1. Given this form, we might assume that whenever we query the value of $_POST['gender'] in submit_form.php, we are going to get one of the values 'male', 'female', or 'other'—and we would be completely wrong.

![](img/654520c37415debd4290b9b4aa2c03f2_376_0.png)

Figure 15.1 A Trivial Little Form

As we mentioned previously, the web operates using HTTP, a simple text protocol. The preceding form submission will be sent to our server as a text message with a structure similar to the following:

```
POST /submit_form.php HTTP/1.1
Host: www.yourdomain.com
User-Agent: Mozilla/5.0 (Windows NT 10.0; WOW64; rv:40.0) Gecko/20100101 Firefox/40.0
Content-Type: application/x-www-form-urlencoded
Content-Length: 11
gender=male
```

However, there is absolutely nothing stopping somebody from connecting to our web server and sending whatever values they want. Thus, somebody can send us the following:

```
POST /submit_form.php HTTP/1.1
Host: www.yourdomain.com
User-Agent: Mozilla/5.0 (Windows NT 10.0; WOW64; rv:40.0) Gecko/20100101 Firefox/40.0
Content-Type: application/x-www-form-urlencoded
Content-Length: 22
gender=I-like-cookies.
```

we want to write the following code:

```
<?php
echo "<h1
  The user's gender is: " .$_POST['gender'] . ".
</h1>";
?>
```
