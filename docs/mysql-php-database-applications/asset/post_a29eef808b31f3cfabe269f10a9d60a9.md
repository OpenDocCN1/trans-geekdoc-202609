
company but not an individual. For the most part, you'll have to wait to have a specific contact to add to the database before you can add company information. This is a ridiculous restriction. The solution is to store contact information in one table and company information in another. By storing company information in its own table, you can add a new company there even if you (as yet) have no contacts to go with it. Ditto for contacts with no matching companies.

## Normalization

Now that we've shown you some of the problems you might encounter, you need to learn the ways to find and eliminate these anomalies. This process is known as normalization. Understanding normalization is vital to working with relational databases. But to anyone who has database experience normalization is not the be-all and end-all of data design. Experience and instinct also play a part in the creation of a good database. The examples in this book will usually be normalized. However, in some cases, a denormalized structure is preferable, for performance reasons, code simplification, or so on.

One other quick caveat. The normalization process consists of several normal forms. Normal forms are standards of database regulation that promote efficiency, predictability of results, and unambiguousness.

In this chapter we cover first, second, and third normal forms. In addition to these, the normalization process can involve four other (progressively more rigorous) normal forms. (For the curious, these are called Boyce-Codd normal form, fourth normal form, fifth normal form, and Domain/Key normal form.) We know about these because we read about them in a book. In the real world, where real people actually develop database applications, these normal forms aren't discussed. If you get your data into third normal form that's about good enough — mainly because data in the third normal form meets the requirements of the first and second normal forms, by definition. Yes, a possibility exists that anomalies will exist in third normal form, but if you get this far you should be OK.

## First normal form

Getting data into first normal form is fairly easy. Data need to be in a table structure and to meet the following criteria:

- * Each column must have a unique name and define a single attribute of the table as a whole.
- * Each row in the table must have a set of values that uniquely identifies the row (this is known as the primary key of the table).
- * No two rows can be identical.

Each cell must contain an *atomic* value, meaning that each cell contains only one value. No arrays or any other manner of representing more than one value can exist in any cell.

No repeating groups of data are allowed.

The final item here is the only one that may require some explanation. Take a look at Table 1-7.

As you've already seen with these data, row 1 and row 2 contain two columns that contain identical information. This is a repeating group of data. Only when you remove these columns and place them in their own table will these data be in first normal form. The separation of tables that we did in Tables 1-3 and 1-4 will move this data into first normal form.

Before we move on to chat about second and third normal form, you're going to need a couple of quick definitions. The first is of the term *primary key*. The primary key is a column or set of columns by which each row can be uniquely identified.

Primary keys, while very important, are difficult to understand both in theory and in practice. The theory is straightforward: Each row in the column designated as the primary key must have a unique value. In practice, the easiest way to get a series of unique numbers is to use a series of sequential numbers, in which the value of the primary key column in each row increments the previous row's primary key value by one. Because this is such a popular solution to the primary key problem, all database servers of any consequence create the incremental values for you as records are created. MySQL has such a mechanism; you use it by designating your primary key column as type *auto_increment*.

Depending on your data, all kinds of values will work for a primary key. Social Security numbers work great, as do email addresses and URLs. The data just need to be unique. In some cases, two or more columns may comprise your primary key. For instance, to continue with the address-book example, if contact information needs to be stored for a company with many locations, it is probably best to store the switchboard number and mailing address information in a table that has the *company_id* and *company_location* as its primary key.

Next, we need to define the word *dependency*, which means pretty much what you think it means. A dependent column is one that is inexorably tied to the primary key. It can't exist in the table if the primary key is removed.

With that under your belt, you are ready to tackle second normal form.

## Second normal form

This part of the process only comes into play when you end up with one of those multi-column primary keys that we just discussed. Assume that in the course of dividing up your address tables you end up with Table 1-8. Here, the *company_name* and *company_location* columns comprise the multi-column primary key.

### TABLE 1-7 TABLE WITH REPEATING GROUPS OF DATA

| company_id | company_name | company_address | contact_name | contact_title | phone | email |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| 1 | BigCo Company | 1121 43rd St. | Jay Greenspan | Vice President | 4155551212 | jay@not.real |
| 2 | BigCo Company | 1121 43rd St. | Brad Bulger | President | 4155552222 | brad@not.real |
| 3 | LittleCo Company | 4444 44th St. | John Doe | Lackey | 2125556666 | nobody@hotmail.com |

You should be able to see pretty quickly that an insertion anomaly would work its way in here if you were to add another location for BigCo Company. You'd end up with the CEO name, Bill Hurt, repeated in an additional row, and that's no good.

You can get this table into second normal form by removing rows that are only partially dependent on the primary key. Here, the CEO is dependent only on the company_name column. It is not dependent on the company_location column. To get into second normal form, you move rows that are only partially dependent on a multi-field primary key into their own table (see Tables 1-9 and 1-10). Second normal form does not apply to tables that have a single-column primary key.

### TABLE 1-8 TABLE NOT IN SECOND NORMAL FORM

| company_name | company_location | company_ceo | company_address |
|---|---|---|---|
| BigCo Company | San Francisco | Bill Hurt | 1121 43rd St. |
| LittleCo Company | Los Angeles | Bob Ouch | 4444 44th St. |

### TABLE 1-9 TABLE IN SECOND NORMAL FORM

| company_id | company_name | company_ceo |
|---|---|---|
| 1 | BigCo Company | Bill Hurt |
| 2 | LittleCo Company | Bob Ouch |

### TABLE 1-10 TABLE IN SECOND NORMAL FORM

| company_id | company_location | company_address |
|---|---|---|
| 1 | San Francisco | 1121 43rd St. |
| 2 | Los Angeles | 4444 44th St. |

## Third normal form

Finishing up the normalization process, third normal form is concerned with transitive dependencies. A transitive dependency describes a situation in which a column exists that is not directly reliant on the primary key. Instead, the field is reliant on some other field, which in turn is dependent on the primary key. A quick way to get into third normal form is to look at all the fields in a table and ask if they all describe the primary key. If they don't, you're not there.

If your address book needs to store more information on your contacts, you might find yourself with a table like Table 1-11.

### TABLE 1-11 TABLE NOT IN THIRD NORMAL FORM

| contact_id | contact_name | contact_phone | assistant_name | assistant_phone |
|---|---|---|---|---|
| 1 | Bill Jones | 4155555555 | John Bills | 2025554444 |
| 2 | Carol Shaw | 2015556666 | Shawn Carlo | 6505556666 |

You might think we're doing OK here. But look at the assistant_phone column and ask if that really describes the primary key (and the focus of this table), which is your contact. It's possible, even likely, that one assistant will serve many people, in which case it's possible that an assistant name and phone will end up listed in the table more than once. That would be a repeating group of data, which you already know you don't want. Tables 1-12 and 1-13 are in third normal form.

### TABLE 1-12 TABLE IN THIRD NORMAL FORM

| assistant_id | assistant_name | assistant_phone |
|---|---|---|
| 1 | John Bills | 2025554444 |
| 2 | Shawn Carlo | 6505556666 |

### TABLE 1-13 TABLE IN THIRD NORMAL FORM

| contact_id | contact_name | contact_phone | assistant_id |
|---|---|---|---|
| 1 | Bill Jones | 4155555555 | 1 |
| 2 | Carol Shaw | 2015556666 | 2 |
