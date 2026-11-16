
Of course, no such levels are defined in the Select Level(s) area, so you'll need to define some.

![](img/43fd0127a958864ab2d93e28efe683e7_411_0.png)

- 3) Click the Define button. In the Define Access Levels dialog, place the cursor in the Name field, type visitor, and press the + button. Repeat the process to add admin. Click OK.

Dreamweaver won't check to make sure these groups actually exist; it takes your word for it, so make sure you spell them correctly. These correspond to the available values in the userGroup field of tbl_users. Once it knows their names, Dreamweaver can grant access to pages to users in either or both groups, and deny access to users not in either.

![](img/43fd0127a958864ab2d93e28efe683e7_411_1.png)

- 4) Back in the Restrict Access to Page dialog, Ctrl-click (Windows) or Command-click (Mac) to select both visitor and admin from the Select Level(s) area. In the If Access Denied, Go To field, enter login.asp. Click OK.

You've done two things in this step. You've granted access to the page to users in either the visitor or admin group. Had you wanted to grant access to this page to only one of those groups, you would have selected only the one group. Once you've created the admin section of the site, you'll use this dialog and let in only members of the admin group.

The other thing you've done is redirect the user to login.asp if access is denied. This is how that interception described earlier happens. A user tries to access a restricted page without logging in, and she or he sees the log-in dialog. Once log-in is achieved, the restricted page she or he was trying to access appears.

![](img/43fd0127a958864ab2d93e28efe683e7_412_0.png)

- 5) Repeat steps 1 through 4 for each of the following files:
  - profiles_detail.asp
  - tourprice.asp
  - tourprice_processor.asp
  - tours.asp
  - tours_detail.asp

Each of these pages now requires authentication as well.

- 6) Save and upload all of the pages you have worked on in this lesson, and, starting from the homepage (index.asp), try accessing the tours and the country profiles.

The authentication framework is fully functional. If you try to access a protected page, the login screen should appear. If you've created a registration account, use it. Or, remember you can use username: osiris@allectomedia.com and password: osiris to test. Once you've logged in, you should automatically be redirected to the page you first requested.

![](img/43fd0127a958864ab2d93e28efe683e7_413_0.png)

**NOTE** PHP users with PHP 4.2 and higher will be disappointed to learn that instead of being redirected to the originally requested page after login, they are sent to the home page. The reason for this is that the server behavior that is supposed to cause the redirection to the originally requested page relies on a configuration setting, register_globals, to be on in order to work. Since PHP 4.2, the default setting for register_globals is off. You can go into your php.ini file and change it to on, and the site will work as expected. However, it was turned off for a reason—this setting creates a potential security hole in PHP. Thus, before you decide to go into php.ini and change the setting, I recommend that you go out on the Web and research the issue.

- 7) Open index.asp, and add links at the bottom of the left navigation bar connecting to the registration and log-in pages: Register (Free!) and Log In.

Since users will be intercepted if they attempt to enter restricted pages, and since you took the time to add a link from the log-in page to the registration page, users should find everything even without these links. Still, their presence here makes it that much easier for visitors and employees alike to use the site.

![](img/43fd0127a958864ab2d93e28efe683e7_414_0.png)

## WHAT YOU HAVE LEARNED

In this lesson, you have:

- * Learned about persistent data (pages 383–385)
- * Created a registration page, using the Insert Record and the Check New Username server behaviors (pages 385–392)
- * Built a log-in page, using the Log In User behavior (pages 393–397)
- * Created pages to handle registration and log-in failures (pages 394–397)
- * Applied Restrict Access to Page server behaviors to each secured page in the site (pages 401–405)

## managing content with forms

### LESSON 14

A content management system, as its name suggests, is an interface that facilitates the maintenance of content, including the addition of new content, the modification of existing content, and the removal of unwanted content. In this and the next two lessons, you will make steps toward building a content management system (CMS) for the Newland Tour's site. You won't build a fully comprehensive CMS, which is an ambitious and often redundant task, making it of limited value in this book. But you will build enough of it to get a sense of how they work, and the know-how to start building your own.

By inserting some HTML as the default text in a text area, you can provide users a template for creating formatted text.

![](img/43fd0127a958864ab2d93e28efe683e7_415_0.png)

By inserting some HTML as the default text in a text area, you can provide users a template for creating formatted text.

How do CMSs work? You can look at this question as a functional question (how can Web content be maintained over the Web?) or as a technical question (how do we use available technologies to make this possible?). Whenever you face a problem like this, answer the functional question first, and then worry about the technical answer.

In practice, CMSs typically include several pages with forms on them. When users fill out the forms, whatever they entered appears on the site. You don't want these forms to be accessible to the public, which is why you created the log-in framework first. You have probably guessed how this process from form to Web works: database connectivity. You know that the contents of a Web page can be populated by database data, and you know that you can capture user-entered information from a form and put it in a database. Put two and two together, and voila! A content management system.

In 2002, Macromedia released a revolutionary new approach to content management, called Contribute. Contribute, now in its second version, enables non-technical users to maintain site content in a friendly, office productivity tool-like environment. Contribute has both advantages and disadvantages compared to a CMS using a database and ASP, ColdFusion, or PHP. As a Web editor, Contribute enables users to format content much more robustly and easily than the best database-driven CMS. And unlike database-driven sites with ASP, ColdFusion, or PHP, Contribute doesn't require significant programming up-front to achieve the most basic functionality. Because it works mainly with static sites, Contribute is generally a less expensive solution. On the down side, Contribute doesn't work with live database content. In addition, whereas updating a database-driven Web site requires a browser and Internet access, updating a site with Contribute requires Internet access and a copy of Contribute, which, though inexpensive, is not free.

As a rule, use Contribute for text- and image-heavy static sites whose contents need occasional updating, and use dynamic pages and a database for highly structured or data-oriented sites whose contents change frequently, or on sites whose contents need to be searchable. Many enterprise sites make use of both databases and server-side scripting (such as ASP, ColdFusion, or PHP) and Contribute—using each according to its strengths.

Back to the CMS we'll begin in this lesson. Content maintenance implies three abilities: inserting content, modifying content, and deleting content. If you know any SQL, you are probably aware of the INSERT, UPDATE, and DELETE statements, which make it possible to insert, modify, and delete data from a database. If you don't know SQL, don't worry: you'll get practice with each of these statements in this and the next two
