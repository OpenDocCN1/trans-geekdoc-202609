3) In the Bindings panel, click the New Binding (+) button, and choose Recordset (Query) from the menu.

At this point, you have connected your site to a data source, which means you have made it possible for Dreamweaver to write code for you that retrieves data from your database. However, you have not actually retrieved any data yet. In this and the next two steps, you'll create a recordset, which as you'll recall from the beginning of this lesson, is a collection of data that meets certain criteria and that is retrieved from a database using SQL.

![](bbox=[0.265, 0.245, 0.46, 0.425])

Your goal is to display the journal entry, but you don't want to display all the journal entries, only the most recent. In order to facilitate this, each journal entry has been given an unique ID (a primary key). These IDs are numbered incrementally, as the records are added. Therefore the record with the highest journalID is the most recent. You'll need to sort the data, and then retrieve the contents of the latest journal entry in order to display it. You'll take the first steps toward doing this in the next step.

4) In the Recordset dialog, enter rs_journal as the Name. Choose conn_newland (or newland for ColdFusion users) from the Connection drop-down. Select tbl_journal from the Table drop-down. In the Columns section, choose the Selected radio button, and Ctrl-select (Windows) or Command-select (Macintosh) journalID and journal_entry.

In this dialog, you are creating a recordset, named rs_journal. The data in this recordset is retrieved using criteria specified in SQL. You may not realize it, but you have already begun the SQL statement.

Specifically, you have specified data in the data source stored in conn_newland (that connection specifies the newland DSN). Within that data source, you are specifying that the data is in a table named tbl_journal. Going a step further, you are specifying that you only want to retrieve the journalID and journal_entry fields from that table.