Here’s the scenario: you’ve received a dataset of the emails that have gone through one of two email sequences. An email sequence is a series of emails automatically sent to someone on an email list, often with an inducement to purchase a product. In this dataset, the demographic data makes up the first few columns. The last two columns tell you which email sequence a particular contact was sent into. The vendor has handed you this dataset, and your management has provided the following instruction:

+   - They’re interested only in United States customers.
+   - They would like you to turn the email sequences into one column reporting which sequence a person was in. This will make it easier to summarize with a PivotTable.
+   - Management would like you to clean out any blank cities as this will create issues when this data is merged with checkout and sales data. As well, if there are any other column blanks, they would like you to remove them too.
+   - They would like to understand the series of steps required so they can simply run it again in the future.

Armed with Power Query, you are up to the task!

# Starting Power Query

To start Power Query, click the Data tab on the ribbon. The leftmost side of the Data tab will contain Power Query.

Now this is where things might get confusing. In my version of Excel (see Figure 2.2), the words _Power Query_ are not mentioned. In fact, Excel sometimes refers to Power Query as “Get & Transform.” (See the following sidebar for an explanation of this.) Yours might have a button that says “New Query.” Though the buttons may be a different configuration on your machine, they’re all there. So make sure to click around!

![](bbox=[0.135, 0.695, 0.7, 0.79])

**Figure 2.2:** Power Query can be found in the leftmost buttons of the Data ribbon tab. Some versions will label the group “New Query,” and others will say “Get & Transform.” This all depends on the version and build of Excel you have.

In this case, we’ll want to use Power Query on the data already in the spreadsheet. We don’t need to connect to an external data source (although Power Query can do this).