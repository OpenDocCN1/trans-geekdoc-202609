# Guestbook 2003, the (Semi-)Bulletproof Guestbook

# IN THIS CHAPTER

+   - Learning the power of Guestbook 2003
+   - Organizing your code in a reasonable way
+   - Writing good, reusable functions

IN THIS CHAPTER WE DEVELOP the first of our applications – a guestbook. Guestbooks aren’t complex and they aren’t very exciting. However, this application does give us the chance to introduce some concepts, such as validation, and put many of the practices discussed earlier in this book to work.

In the introduction of this book we provided some code that could be used for the most basic guestbook possible. However, using that code for your guestbook is not a good idea: It’s got all kinds of holes that will allow malicious people out there to mess with your pages. The ultra-basic guestbook has another problem: Given the way the code is just dumped into one page, there’s not a line that’s reusable. One of the main goals of developing any application is to create chunks of reusable code.

# Determining the Scope and Goals of the Application

The easiest way to get yourself into trouble when coming at an application is not to know exactly what you are trying to achieve. A vital part of the developer’s job is to figure out exactly what is needed in the application. Usually doing this will involve extensive discussion with the people for whom the application is being developed. During these discussions, it is important to think a step ahead and ask questions that may not have been asked before. What if the scope increases in a certain way? What if additional but related information needs to be tracked?