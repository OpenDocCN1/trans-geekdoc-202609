
lessons. You will use these in your queries, rather than simple SELECT statements, to make content manageable.

The primary task remaining is to create form interfaces that serve as the front-end for the work going on in the background. Some of these, especially those for inserting data, are quite easy to create. In fact, by building the registration form, you've already created one. Updating and deleting data are a little trickier, because you have to retrieve data from the database and make it available to the user, so she or he can send the requisite queries back to the database to do the actual updating or deleting.

In this lesson, you will create the simplest portion of the CMS: the form that Newland Tours employees can use to update the Traveler's Journal on the homepage. This functionality requires only a single page, a single form, and a single server behavior (Insert Record).

## WHAT YOU WILL LEARN

In this lesson, you will:

- Empower nontechnical users to add formatted content to a Web page instantly
- Create an admin section for the site, including a new template
- Use and customize a text area form element
- Track user activity with session variables and hidden fields
- Learn about SQL's INSERT statement
- Use the Insert Record server behavior

## APPROXIMATE TIME

This lesson takes approximately 45 minutes to complete.

## LESSON FILES

Starting Files:
Lesson14/Start/newland/generic_template.asp
Lesson14/Start/newland/index.asp

Completed Files:
Lesson14/Complete/newland/admin_template.asp
Lesson14/Complete/newland/admin_index.asp
Lesson14/Complete/newland/admin_update_tj.asp
Lesson14/Complete/newland/index.asp

## CREATING THE ADMIN SECTION

By the time the site is complete, employees will be able to do a number of administrative tasks, which include inserting new 'Traveler's Journal' articles, maintaining the country profiles, and maintaining the tour descriptions. All of these activities will be limited to those in the admin user group. It is a nice touch to create an administrative homepage—a single page that links to all of the different tasks that administrators can accomplish with the site.

In addition, creating the CMS features will mean creating several new pages. Each of these pages needs to have the Restrict Access to User server behavior applied to it in such a way that only members of the admin user group can get in. That could get monotonous, so to avoid that, you'll create a special admin-only template, called admin_template.asp, which is nearly identical to generic_template.asp, except that it'll have the Restrict Access to User server behavior already applied.

- 1) Open generic_template.asp. Use the toolbar to change the title to Newland Tours: Admin, and save the file as admin_template.asp.

You know your template is useful when you use it to create other templates!

![](img/43fd0127a958864ab2d93e28efe683e7_418_0.png)

- 2) Use the Server Behaviors panel to add a Restrict Access to Page behavior. In the dialog, restrict based on Username, Password, and Access Level, and make sure that only admin is selected in the Select Level(s) area. Specify login.asp in the If access denied field, and click OK.

All of the admin pages should require that the user log in as a member of the admin user group, so you might as well attach the Restrict Access to User behavior directly to the template.

![](img/43fd0127a958864ab2d93e28efe683e7_419_0.png)

- 3) Choose File > Save.

You've made a change to the template, so you need to save it.

- 4) Choose File > Save As, and save the file as admin_index.asp. Change the page title to Newland Tours: Admin Home, and change main heading to Admin Home.

Employees will use this page as a starting point for administrative tasks. You'll also enable them to log in directly to this page.

![](img/43fd0127a958864ab2d93e28efe683e7_419_1.png)

- 5) In the body section, enter the following lines of text:
Choose an administrative task from the list below. If you have any questions or problems, please contact the webmaster.

- Update the Traveler's Journal
- Add or remove a registered user to/from the Admin group
- Add a new tour description
- Modify or remove an existing tour description
- Add a new country profile
- Modify or remove an existing country profile

This is the main menu for the page. You'll add actual links as you go, but now you have the framework.

![](img/43fd0127a958864ab2d93e28efe683e7_420_0.png)

- 6) Link the word webmaster to your own email (don't forget the mailto: prefix).

Save and close admin_index.asp.

Whenever you deploy a content management system, make sure you provide explicit directions and contact information, in case its users have any problems.

TIP Developers often put admin files in a separate folder, which has different permissions.
For the sake of simplicity, we'll keep everything in one place and prefix all admin pages with admin_. The topic of Web application security is beyond the scope of this book, but it is not a topic you should take lightly when you start developing dynamic applications in the real world.

- 7) Open index.asp, and just below the Log In link, add a new link called Admin, which links to admin_index.asp.

Now all users—visitors and employees alike—can access what they need through the site's front door.

![](img/43fd0127a958864ab2d93e28efe683e7_421_0.png)

- 8) Test the new link (including log-in functionality) by pressing F12 with index.asp open and attempting to access admin_index.asp. At the log-in screen, use the following credentials to access the admin section of your site.

Username: sfrome@starknet.com

Password: hypochondriac

Though you probably created one or more of your own registration accounts in Lesson 13. Remember, those are set to the visitor user group. You can't use them (yet) to access admin_index.asp. The credentials supplied above are already in the database (in tbl_users), with admin as the value in the userGroup column.

You might try logging in with your own username and password, just to verify that you don't get in. If you don't have a username and password, remember that you can use osiris@allectomedia.com as the username and osiris as the password, since this user account has the visitor status.

## TWO APPROACHES TO FORMATTING CONTENT STORED IN A DATABASE

Now that you have a basic framework for the admin section, you can start building its functionality. In this task, you will create a form that enables users to input new Traveler's Journal entries, which take effect immediately. The form outputs to tbl_Journal, which is the same table whose contents index.asp retrieves to display the Traveler's Journal.

![](img/43fd0127a958864ab2d93e28efe683e7_422_0.png)

But if you look at the 'Traveler's Journal, you'll notice that its contents are formatted. The title is in a heading (<h3>, to be specific), the author line is in a <p> tag with the author class applied, and each subsequent paragraph is in its own set of <p> tags.

How can you capture content so that it can be marked up and formatted? You can take two approaches:

- Separate each of the elements. With this approach, you create a field for the title in the form and in the database table. Then you dynamically populate an <h3> element with the contents of that record. You then add another pair of fields for the author, and so on. This is how the country profiles and tour descriptions were formatted so precisely.

- Embed HTML markup in the database table. With this approach, part of the text stored in the database is HTML markup. When the record is retrieved, so is the markup. Since the server inserts this text as a part of the page, the browser doesn't know that it is dynamically generated HTML, and it renders just like it would any other HTML.

Each approach has different advantages and disadvantages, and they are not exclusive, so you can use a hybrid approach if you like. The advantage to separating the elements is that HTML tags are hard-coded in the document, and they don’t appear in the database. One disadvantage of this approach is that it’s limited to paragraph-level styles. That is, it is easy to store the entire title and bind it to an <h3> element, but it would be hard to italicize one of the words in the title. Another disadvantage is that it requires more fields in both the database and the form. If someone typed the Traveler’s Journal in a word processor and wanted to transfer it to a form, they would have to transfer one piece at a time.

The embedded HTML approach has its own strengths and limitations. One strength is that you can format the content to your heart’s content. You can italicize words, make them bold, turn them pink, and magnify them to 100 pixels if you want. The weakness of this approach is that it requires users to hand-code HTML. One of the goals of a CMS is to make it possible for nontechnical people to maintain content, so requiring them to hand-code HTML defeats a key purpose of having a CMS.

Some commercial CMSs include basic formatting GUIs, which enable users to format using HTML without ever seeing it—they just highlight text and click a B button to make the selection bold. Such a feature set is again beyond the scope of this book, but it is possible.

> **NOTE** *The Traveler’s Journal is one element that would benefit from Macromedia Contribute: users could replace it directly and quickly, and format it as they please. We’ll go ahead and build a CMS for it, because doing so will give you exposure to concepts and techniques that you’ll use over and over again.*

In this task, you will take a compromise approach, in which users have to see some HTML markup, but they don’t actually have to write any. They just overwrite descriptive placeholders in an already marked-up block of text that you set up as the default in a text area.

## CREATING THE FORM INTERFACE

Most CMSs are form-based, so building them involves creating lots of forms. The key to developing forms is to analyze the structure of your data in the database, and make the forms match accordingly. In this case, you will be inserting a new record into a table that has only three fields, including one that’s a primary key. So this form will be easy, containing only two elements and a Submit button. In this task, you’ll mock up the visible part of the form.
