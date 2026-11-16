
(as opposed to a number or an expression) is placed within single quotes. The individual pieces of data are separated by commas. The values at the bottom are matched in order to the fields listed at the top, so not only do the number of fields and the number of values have to match, but also you have to make sure you list them in the correct order.

> **TIP** _One of the most common typos when building INSERT INTO SQL statements is to add a comma after the last field name or the last value. The last value should not be followed by a comma, and if it is, you will see an error message._

- 1) Click to select the Submit button, and begin the process of adding an Insert Record server behavior.

This server behavior will be used to input the text area (journal_entry) and the hidden field (author) into tbl_journal's journal_entry and author fields.

- 2) In the Insert Record dialog, specify conn_newland as the connection, tbl_journal as the Insert Into Table, and index.asp as the After Inserting, Go To. Verify that the lower half of the dialog provides Dreamweaver with the instructions it needs to insert journal_entry into journal_entry and author into author.

This is the matching exercise part, where you specify which field of which database table is populated with which field of the form. Since you gave the form elements the same names as their destination table field names, Dreamweaver correctly matches everything for you.

You specify index.asp as the redirection page, so that users can verify that what they entered is now showing on the homepage.

Again, ColdFusion and PHP users will note that the dialog they see, though functionally the same, varies cosmetically from the one shown in the screenshot.

![](img/43fd0127a958864ab2d93e28efe683e7_430_0.png)

- 3) Test the new functionality, making sure to log in as an administrator.

![](img/43fd0127a958864ab2d93e28efe683e7_431_0.png)

The homepage now contains whatever you entered, formatted using the specified HTML.

![](img/43fd0127a958864ab2d93e28efe683e7_431_1.png)

If you look in the tbl_journal table of the database, you will see both the first line of the text you entered (text entered after line breaks is not displayed in Access' table view) and the account you used to log in, which was stored as a session variable and passed through the form to the database.

![](img/43fd0127a958864ab2d93e28efe683e7_432_0.png)

## WHAT YOU HAVE LEARNED

In this lesson, you have:

- Created an admin section that makes administrative tasks conveniently accessible to users (pages 409–412)
- Repurposed generic_template.asp into a special template for the admin section (pages 409–410)
- Built a form using a text area element with HTML-formatted default text (pages 413–418)
- Designed a system to capture the identity of users updating the ‘Traveler’s Journal’ (pages 418–420)
- Inserted the data using the Insert Record server behavior (pages 420–423)

## Building update pages

## LESSON 15

In this lesson, you will build an interface that lets employees change a registered user from one user group to another (from visitor to admin, or vice versa). This implies a certain workflow: To add an employee to the admin group, the employee must first register at the site, and then another employee must go in and change her or his user group. Likewise, if an employee leaves Newland Tours, another employee can easily change the former employee's user profile back to visitor. The interface will use two pages—one where the employee selects the user whose profile will be changed, and one to actually update the profile.

![](img/43fd0127a958864ab2d93e28efe683e7_433_0.png)

You'll enable users to update database data using a Web form, SQL's UPDATE statement, and Dreamweaver's Update Record server behavior.

Two-page applications that use this structure are referred to as master-detail page sets.
A master-detail page structure is one of the most common—and useful—structures
that you will master as a Web developer. The first page is the master page, because it
lists many records in a summary format. Users browse this summary, and then select
the record they want to learn more about or modify/delete. The second page is the
detail page, because it contains detailed information about the selected record. On
this page, users can learn more about a product or modify/delete a record. To
summarize, the master page lists a small sampling of fields from multiple records
within a database, while the detail page displays many fields from a single record.

You've already built two master-detail page sets in the course of the book: The country
profile pages perfectly fit this description, and the tour description page set is a
variation on the theme. But in both cases, the detail page only displayed data. In this
lesson, you'll use the detail page to update data.

Updating data is slightly more complex than inserting new data, which you did in
Lessons 13 and 14. When you insert new data, you identify a table and specify which
data to write to which fields in that table. When updating data, you have to do the
same thing to a particular, existing record; you can't just append information as a new
record at the end of the table. SQL has a command—UPDATE—that you can use to
accomplish this task, and Dreamweaver has an Update Record server behavior that
makes it even easier.

In this lesson, you will combine the master-detail page structure with the update-
record page structure. You will use several Dreamweaver behaviors to make it happen.
It is vital in this lesson that you understand the big picture about what is happening:
Dreamweaver behaviors sometimes make it easy for us to not worry too much about
the mechanics of what's going on, but in the next lesson, you are going to replicate
this structure using a more ambitious hands-on approach, so it's best now if you nail
down the concepts.

## WHAT YOU WILL LEARN

In this lesson, you will:

- Plan for a master-detail set, by analyzing the data needed for the application
- Create a master-detail page set, using the admin template created in the previous lesson
- Learn about SQL's UPDATE statement
- Convert the detail page to a dynamically populated form capable of updating, rather than merely displaying, contents in the database

## APPROXIMATE TIME

This lesson takes approximately one hour to complete.

## LESSON FILES

Starting Files:
Lesson15\Start\newland\admin_template.asp

Completed Files:
Lesson15\Complete\newland\admin_addUser_master.asp
Lesson15\Complete\newland\admin_addUser_detail.asp

## PREPARING THE PAGES

To insert a master-detail page object, you must open the page that will become the master. In the course of completing the dialog that creates the page set, you specify the name of the detail page as well. If you haven’t yet created the detail page, Dreamweaver can create one for you. But it’s hard to go back and apply your template to that page. Thus, in this task, you will create the master and detail pages used in this set.

- 1) Open admin_template.asp, title the page Newland Tours Admin: Add User to Admin Group, change the heading to Add User to Admin Group, and save the file as admin_addUser_master.asp.

This page will be the master page, holding summary information about each of the registered users.

- 2) Replace the placeholder body text with the following. To add a registered user to the Admin group, select her or his name from the list, and change the permission group to admin on the following page. Save the file.

Again, providing directions now enhances the efficacy of the site and reduces tech-support calls and frustration later.

![](img/43fd0127a958864ab2d93e28efe683e7_436_0.png)

- 3) Open admin_template.asp, title the page Newland Tours Admin: Add User to Admin Group, change the heading to Add User to Admin Group, and save the file as admin_addUser_detail.asp.

This page will be the detail page, which will contain the form that employees can use to actually change a user’s permission group.
