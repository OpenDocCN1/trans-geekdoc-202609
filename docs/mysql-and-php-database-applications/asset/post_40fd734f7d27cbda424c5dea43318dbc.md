
# Part III: Simple Applications

will always be an opportunity for the shrewd and persistent to submit multiple entries. But in all likelihood your survey will not pass muster with the Federal Elections Commission. A small step to weed out those ruining your survey should do the trick, and you will see one way to accomplish this later on.

## Necessary Pages

Entering and viewing information will require three pages. The first is where the questions will be presented and where the user will enter name, address, and geographic demographic information. A second page will show the basic survey results. A third will give a detailed breakdown. Figures 9-1, 9-2, and 9-3 show these pages respectively.

![](img/245156cc770929860a3ede93c01f9981_246_0.png)

Figure 9-1: Page for filling out

Note that for this application you will use a .gif file for your chart. The script will change the size attributes of the `<img>` tag to give a representation of the information. This works, but isn't necessarily ideal. You could install the libraries and compile PHP with --with-gd flag. These functions are beyond the scope of this book.

This application, like all others, needs some administrative tools. For starters, you will need to be able to add, delete, and edit questions. Additionally, there is a page that selects a winner random from the database. Figures 9-4 and 9-5 show the administrative page and the select winner page, respectively.

# Chapter 9: Survey

![](img/245156cc770929860a3ede93c01f9981_247_0.png)

Figure 9-2: Basic survey results

![](img/245156cc770929860a3ede93c01f9981_247_1.png)

Figure 9-3: Detailed results *

# Part III: Simple Applications

![](img/245156cc770929860a3ede93c01f9981_248_0.png)

Figure 9-4: Survey administration page

![](img/245156cc770929860a3ede93c01f9981_248_1.png)

# Survey Admin: Weekly Random Drawing

Draw a winner for the week of 2000-05-28

fred programmer fred@fred.com WINNER! Notify Winner

- Past Weeks:
- 2000-05-28
- 2000-06-04
- 2000-07-02
- 2000-10-29
- 2000-11-05

Admin Page

Figure 9-5: Select winner page

# Chapter 9: Survey

Winners will be notified via e-mail and sent a URL that they will need to travel to in order to claim their prize. This page will look like the one in 9-6. Once they will need to confirm who they are, just so you have an extra level of security.

![](img/245156cc770929860a3ede93c01f9981_249_0.png)

Figure 9-6: Claim prize page

# What do we need to prevent?

In the previous chapter we discussed methods for removing junk information that people attempt to send through the form elements. We will continue to use these functions here. This application will also do e-mail address validation.

> Want to see what it really takes to verify that an e-mail is in the proper format? It takes a lot of work. Take a look at the CheckEmail.php file in /functions directory on the CD. You can see that it takes multiple regular expressions to make sure the e-mail is just right. Given that regular expressions are fairly slow, you may be wondering if it is even worth running a script like that, especially if you are running a site with very heavy traffic. You will need to decide that for yourself. You do need to make e-mails perfect, or will a simpler, less-robust form of validation be good enough? Even if you make the address is in the proper format, there's almost no way to know if the address is attached to an actual mailbox.

This application will provide you with a simple means for blocking some people from entering information at your site. It's nothing terribly sophisticated; a savvy Internet user would be able to work around it in a minute. Using the form shown in 9-6 you will be able to enter a domain of origin that will be blocked from the. All users will have their REMOTE_HOST variable checked against a table in the database. If host is found, the application will refuse that user access. Again, this isn't perfect. Depending on the ISP used, some clients won't identify the REMOTE_HOST in the HTTP header. If you really have sensitive information and need effective means of blocking users, you should work with sort of logic scheme. This is just an example of what you could do with database and HTTP header information.

You'll also need to take some steps to make sure that the wrong people won't claiming prizes. You'll need to make sure that the people coming to claim prizes are who they say are.

# Designing the Database

This survey application allows for any number of questions. Each question can have any number of answers. To create this relationship you'll need two tables, one named questions and one named responses, that have a one-to-many relationship. (Each (1) question can have (n) any number of answers).

User information is best represented with multiple tables as well. A table named users will store the relevant user information. Two tables, named states and count-tries, serve as lookup tables and have one-to-many relationships with the users table.

Finally, there are two tables with relationships to no others. They store other information application needs to track. They are aptly named blocked_domains and survey_admin.

9-7 shows a visual representation of the structure of the database. The create statements for making these tables are shown in Listing 9-1. Note that these table definitions were copied from the mysqldump utility. If you're not aware of mysqldump, or the other mysql utilities, make sure to check up on Appendix C.

# Chapter 9: Survey

9-7 shows a visual representation of the structure of the database. The create statements for making these tables are shown in Listing 9-1. Note that these table definitions were copied from the mysqldump utility. If you're not aware of mysqldump, or the other mysql utilities, make sure to check up on Appendix C.

| questions | blocked_domains |
| :--- | :--- |
| responses | survey_admin |
| users | states |
| | count-tries |

# Code Overview

If you already read the section by the same name in Chapter 8, the structure we use here should be familiar to you. Items in the /functions folder are included and ready for reuse. In the following sections you will see several functions that make life, in the long run at least, a lot easier. The functions in the coming sections will make a lot more sense if you see what they accomplish first. Here's some code that will work just if you used with the following functions.

```
print start_table()
print table_row(
    table_cell("Cell text")
)
print end_table();
```

This will create a table with one cell. You could build on the complexity of this by adding additional table_cell() calls within the table_row function call. You
