```
if (mysql_result($result,0) > 0)
{
    print "<h2>sorry - your domain has been blocked from this page</h2>\n";
    exit;
}
```

This preceding code contains information you're going to need before working with the heart of the application. The includes are clear enough. The includes have been put inside an if statement as a precaution. There is no need to reload the header once it has been loaded once. We can make sure that doesn't happen by creating a constant named LOADED_HEADER. If by chance, this page were loaded a second time, you wouldn't have to worry that includes would be imported more than once.

![](bbox=[0.14, 0.42, 0.24, 0.51])

> Remember that PHP 4 has the include_once construct, which will ensure that no files are included multiple time.

As we mentioned earlier, there is a facility here to block domains, and this application will be doing that off the $REMOTE_HOST variable. This is hardly necessary, and it is easy enough to comment out this code. In order to understand this code, look more closely at the query, particularly the like predicate. When we dial in to the net from my ISP (att.net), my REMOTE_HOST is something like this: 119.san-francisco-18-19rs.ca.dial-access.att.net. When you block domains, you'll be doing it on the top-level domain—in this case, att.net. And this top-level domain is what will reside in the database. So the query will have checked on any number of wildcard characters prior to the top-level domain name.

To achieve this you will need to concatenate the domain names with the % wildcard character. So, for instance, the query will work against %att.net. This may seem somewhat different from your typical like predicate. It's another powerful technique to use with your SQL.

Also note that the start of the select statement doesn't contain a select count(*), instead opting for select 1. This is a good way of testing if any rows meet the condition of the where clause. If the where clause matches any number of rows, the query will return a single column with the value of 1, which in the programming world means TRUE. If there are no rows returned you know the where portion of the query had no matches.

**WEEKSTART()** This function creates a MySQL function to grab the day that starts the week. You use this in the application to pick a winner for the current week.