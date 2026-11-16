# TWO APPROACHES TO FORMATTING CONTENT STORED IN A DATABASE

Now that you have a basic framework for the admin section, you can start building its functionality. In this task, you will create a form that enables users to input new Traveler's Journal entries, which take effect immediately. The form outputs to tbl_Journal, which is the same table whose contents index.asp retrieves to display the Traveler's Journal.

![](bbox=[0.066, 0.215, 0.323, 0.515])

But if you look at the 'Traveler's Journal, you'll notice that its contents are formatted. The title is in a heading (<h3>, to be specific), the author line is in a <p> tag with the author class applied, and each subsequent paragraph is in its own set of <p> tags.

How can you capture content so that it can be marked up and formatted? You can take two approaches:

+   Separate each of the elements. With this approach, you create a field for the title in the form and in the database table. Then you dynamically populate an <h3> element with the contents of that record. You then add another pair of fields for the author, and so on. This is how the country profiles and tour descriptions were formatted so precisely.

+   Embed HTML markup in the database table. With this approach, part of the text stored in the database is HTML markup. When the record is retrieved, so is the markup. Since the server inserts this text as a part of the page, the browser doesn't know that it is dynamically generated HTML, and it renders just like it would any other HTML.