
won't be tripping over each other. It would be even spiffier if the program provided a simple and elegant way to extract information from a table such as this. There should be a quick way to find all of the people from California that doesn't involve parsing and sorting the file. Furthermore, this wondrous program should be able to accept statements that describe what you want in a language very similar to English. That way you can just say: "Give me all rows where the contents of the state column equal CA."

Yes, this program is great, but it isn't enough. Major problems still need to be dealt with. These problems, which we'll discuss in the following pages, are the same ones that made Dr. Codd write his famous paper, and the same ones that made Larry Ellison a billionaire.

## Blasted Anomalies

Dr. Codd's goal was to have a model of information that was dependable. All of the data-storage methods available to him had inherent problems. He referred to these problems as *anomalies*. There are three types of anomalies: update, delete, and insert.

### The update anomaly

Now that you can assume that a table structure can quickly and easily handle multiple requests, you need to see what happens when the information gets more complex. Adding some more information to the previous table introduces some serious problems (Table 1-2).

Table 1-2 is meant to store information for an entire office, not just a single person. Since this company deals with other large companies, there will be times when more than one contact will be at a single office location. For example, in Table 1-2 two contacts are present at 1121 43rd St. At first this may appear to be okay; you can still get at all the information available relatively easily. The problem comes when the BigCo Company decides to up and move to another address. In that case, you'd have to update the address for BigCo in two different rows. This may not sound like such an onerous task, but consider the trouble if this table has 3,000 rows instead of 3 – or 300,000 for that matter. Someone, or some program, has to make sure the data are changed in every appropriate place.

Another concern is the potential for error. It's very possible that one of these rows could be altered while the other one remained the same. Or, if changes are keyed in one row at a time, it's likely that somebody will introduce a typo. Then you'd be left wondering if the correct address is 1121 or 1211.

The better way to handle this data is to take the company name and address and put that information in its own table. This process of separating a table out into multiple new tables is usually called *decomposition*. The two resulting tables will resemble Table 1-3 and Table 1-4.

Now the information pertinent to BigCo is in its own table, Companies. If you look at the next table (Table 1-4), Contacts, you’ll see that we’ve inserted another

| name | addr1 | addr2 | city | state | zip | phone | email |
|---|---|---|---|---|---|---|---|
| Jay Greenspan | 211 Some St. | Apt. 2 | San Francisco | CA | 94107 | 4155558888 | jay@not.real |
| Brad Bulger | 411 Some St. | Apt. 6 | San Francisco | CA | 94109 | 4155552222 | brad@not.real |
| John Doe | 444 Madison Ave. | | New York | NY | 11234 | 2125556666 | nobody@mysql.phpapps.com |

| id | company_name | company_address | contact_name | contact_title | phone | email |
|---|---|---|---|---|---|---|
| 1 | BigCo Company | 1121 43rd St. | Jay Greenspan | Vice President | 4155551212 | jay@not.real |
| 2 | BigCo Company | 1121 43rd St. | Brad Bulger | President | 4155552222 | brad@not.real |
| 3 | LittleCo Company | 4444 44th St. | John Doe | Lackey | 2125556666 | nobody@hotmail.com |

### TABLE 1-3 COMPANIES

| company_id | company_name | company_address |
|---|---|---|
| 1 | BigCo Company | 1121 43rd St. |
| 2 | LittleCo Company | 4444 44th St. |

### TABLE 1-4 CONTACTS

| contact_id | company_id | contact_name | contact_title | phone | email |
|---|---|---|---|---|---|
| 1 | 1 | Jay Greenspan | Vice President | 4155551212 | jay@not.real |
| 2 | 1 | Brad Bulger | President | 4155552222 | brad@not.real |
| 3 | 2 | John Doe | Lackey | 2125556666 | nobody@mysql.phpapps.com |

column, company_id. This column references the company_id column of the Companies table. In Brad's row, you see that the company_id (the second column) equals 1. You can then go to the Companies table, look at the information for company_id 1, and see all the relevant address information. What's happened here is that you've created a relationship between these two tables – hence the name relational database.

You still have all the information you had in the previous setup, you've just segmented it. In this setup you can change the address for both Jay and Brad by altering only a single row. That's the kind of convenience you want to be after.

Perhaps this leaves you wondering how you get this information un-segmented. Relational databases give you the ability to merge, or join, tables. Consider the following statement, which is intended to give all the available information for Brad: "Give me all the columns from the contacts table where contact_id is equal to 1, and while you're at it throw in all the columns from the Companies table where the company_id field equals the value shown in Brad's company_id column."

In other words, in this statement, you are asking to join these two tables where the company_id fields are the same. The result of this request, or query, looks something like Table 1-5.

In the course of a couple of pages, you've learned how to solve a data-integrity problem by segmenting information and creating additional tables. But we have yet to give this problem a name.

When we learned the vocabulary associated with relational databases from a very thick and expensive book, this sort of problem was called an update anomaly. There may or may not be people using this term in the real world; if there are, we haven't met them (people in the real world call it "breach of contract" when addressing their consultants). However, we think this term is pretty apt. In Tables 1-1 and 1-2, if you were to update one row in the table, other rows containing the same information would not be affected.

### The delete anomaly

Now take a look at Table 1-6, focusing on row 3.

Consider what happens if Mr. Doe is deleted from the database. This may seem like a simple change but suppose someone accessing the database wants a list of all the companies contacted over the previous year. In the current setup, when you remove row 3, you take out not only the information about John Doe, you remove information about the company as well. This problem is called a delete anomaly.

If the company information is moved to its own table, as you saw in the previous section, this delete anomaly won't be a problem. You can remove Mr. Doe and then decide independently if you want to remove the company he's associated with.

### The insert anomaly

Our final area of concern is problems that will be introduced during an insert. Looking again at the Table 1-6, you can see that the purpose of this table is to store information on contacts, not companies. This becomes a drag if you want to add a

### TABLE 1-5 QUERY RESULTS

| company_id | company_name | company_address | contact_id | contact_name | contact_title | phone | email |
|---|---|---|---|---|---|---|---|
| 1 | BigCo Company | 1121 43rd St. | 2 | Brad Bulger | President | 4155552222 | brad@not.real |

### TABLE 1-6 TABLE WITH DELETE ANOMALY

| company_id | company_name | company_address | contact_id | contact_name | contact_title | phone | email |
|---|---|---|---|---|---|---|---|
| 1 | BigCo Company | 1121 43rd St. | | Jay Greenspan | Vice President | 4155551212 | jay@not.real |
| 2 | BigCo Company | 1121 43rd St. | | Brad Bulger | President | 4155552222 | brad@not.real |
| 3 | LittleCo Company | 4444 44th St. | | John Doe | Lackey | 2125556666 | nobody@mysql.phpapps.com |
