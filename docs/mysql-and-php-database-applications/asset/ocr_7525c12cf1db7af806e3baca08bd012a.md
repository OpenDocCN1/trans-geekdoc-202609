# 236 Part III: Simple Applications

```
if (mysql_result($result,0) > 0)
{
    print "<h2>sorry - your domain has been blocked from this\npage</h2>\nn";
    exit;
}
```

This preceding code contains information you need to know before working with the heart of the application. The includes are clear enough. The includes have been put inside an statement as a precaution. There is no need to reload the header once it has been loaded. We can make sure that it doesn't happen by creating a constant named LOADED_HEADER. If by chance, this page were loaded a second time, you would not have to worry that includes would imported more than once.

![](bbox=[0.166, 0.409, 0.236, 0.473])

Remember that PHP 4 has the include_once construct, which will ensure that no files are included multiple times.

As we mentioned earlier, there is a facility to block domains, and this application will be doing off the $REMOTE_HOST variable. This is hardly necessary, and it is easy to comment out this code. In order to understand this code, look more closely at the query, particularly the Like predicate. When we dial in the net from my ISP (att.net), my REMOTE_HOST is something like this: 119.sanfrancisco-19yrs.ca.dial-access.att.net. When you block domains, you will be doing it on the top-level domain—in this case, att.net. And this top-level domain will reside in the database. So the query will check on any wildcard characters prior to the top-level domain name.

To achieve this you will need to concatenate the domain names with the % wildcard character. So, the query will work against %att.net. This may seem somewhat different from your typical like predicate. It is another powerful technique to use with SQL.
If the where clause matches any number of rows, the query will return a single column with the value of 1, which in the programming world means TRUE. If there are no rows returned you know where the portion of the query had no matches.

WEEKSTART() This function creates a MySQL function to grab the days of the week. Use this in the application to pick a winner for the current week.