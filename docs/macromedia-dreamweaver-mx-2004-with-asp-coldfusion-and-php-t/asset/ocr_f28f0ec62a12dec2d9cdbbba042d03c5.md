such as which model fits their needs better than another. I certainly have rarely had that opportunity. In reality, the choice is usually driven by the available technology, your budget, the technologies used in an existing site, and the skills and experience of the available human resources. Going a step further, unless you develop for one organization and one organization only, and you intend to stay there for a very long time, you probably don't have the luxury of learning just one. I initially learned ColdFusion and ASP simultaneously, because both were required for different projects I was working on.

# SIDE BY SIDE WITH ASP, COLDFUSION, AND PHP: A STRATEGY FOR LEARNING

Don't be alarmed at the prospect of learning all three at the same time. The truth is, in the vast majority of situations, if you need to add a block of ASP to handle some functionality, then you would also need to add an equivalent block of ColdFusion or PHP to handle the same functionality. And the hardest part is not the syntax of one or the other type of code, but rather understanding what data is available, where it is available, and deciding how to get it to do what you want. If you know that much, the syntax isn't that hard.

For this reason, this book uses ASP, ColdFusion, and PHP side by side. While you don't need to develop the same site three times so you can use all three server models, you should make an effort to understand all three sets of code. That is, if you decide to develop in ColdFusion, don't just skip the ASP and PHP code. Take a moment to see how the ASP and PHP code accomplishes the same thing as the ColdFusion code. If you can understand how all three code blocks accomplish the same task, you will accelerate your mastery of Web programming.

For example, the following three code snippets perform the same function: They output (or display) a value that the user entered in an XHTML form field, called “firstName.”

```
In ASP:
<p>Thank you, <%= Response.Write(Request.Form("firstName")) %>, for your submission.</p>
```

```
In ColdFusion:
<p>Thank you, <cfoutput>#form.firstName#</cfoutput>, for your submission.</p>
```

```
In PHP:
<p>Thank you, <? php echo $_POST['firstName']; ?>, for your submission.</p>
```