You should only look for a framework that uses a proprietary templating system if you are absolutely certain you are happy sticking with that framework for life, given that individual template portability is likely to be impossible. That's a decision you should make in the context of understanding that certain PHP frameworks are labors of love rather than money, and are not necessarily going to be maintained or supported forever.

# Validation

Validation of user input against pre-defined constraints is vital for any application, big or small. Certain requirements are undeniably straightforward to implement yourself — such as checking that an e-mail address is valid. Others are more complex — perhaps guarding against creating a duplicate record in a database table.

Whatever the requirement, a consistent and easily maintainable approach to validating user input is a must. Rather than roll your own, many frameworks provide their own implementation, covering constraint class definitions, erroneous input reporting, fault stacks, and constraint polymorphism.

In a simple project, most will never be used, but that uniform approach provides a degree of scalability and maintainability that simply “hacking something in yourself” just won’t do.

Naturally, if you have your own suite of validation classes to which you are heavily wedded, most frameworks will not shirk at their usage in lieu of those that come in the box.

# URL Rewriting

There’s no doubt that as Web applications have become more sophisticated, so, too, have the URLs that comprise all HTTP GET requests become more bloated, long, and unattractive.

It’s not just aesthetic. There are genuine issues with long and complex URLs. Users copying and pasting URLs to friends and colleagues using IM, e-mail, or Facebook often make errors when URLs are too long. Memorability becomes an issue when URLs need to be cited only from recall. Search engines prefer short, human-readable URLs that relate to the content contained therein. In addition, complex “techie” URLs help expose the inner workings of your application — a temptation for hackers.

Therefore, many frameworks provide some mechanism for URL rewriting — either static (such that, as a developer, you may specify that, for example, /Home, in fact, represents /home.php) or dynamic (as mentioned in the earlier discussion of MVC).

This is normally achieved through close cooperation with the Web server. It is, after all, the Web server that first intercepts HTTP requests before handing them over to PHP. It is therefore nearly impossible to achieve the effects discussed previously without changes at the server level. Normally, with Apache, this is accomplished with mod_rewrite.

Thankfully, as a developer, you don’t have to think about it too much. Most frameworks that provide URL rewriting will either configure your Web server for you or provide simple step-by-step instructions for you to follow. You do need to consider what implications this might have when deploying to your production environment, though — a topic we’ll return to later.