This also works for many-to-many relationships, where two classes are related through a third class. For instance, an `Article` can have many `Authors`, and an `Author` can have many `Articles`. You usually use an `ArticleAuthor` class for that, corresponding to an `article_author` table with an `article_id` and an `author_id` columns. Listing 16-17 shows how to write a fixture file to define many-to-many relationships with this model. Notice the plural table name used here--this is what triggers the search for a middle class.

```
Listing 16-17 - Adding a Record to a Table Related by a Many-to-Many relationship, in data/ fixtures/import_data.yml

Author:
  first_author:
    name: John Doe
    article_authors: [first_post, second_post]
```

One data file can contain declarations of several classes. But if you need to insert a lot of data for many different tables, your fixture file might get too long to be easily manipulated.

The `propel:data-load` task parses all the files it finds in the `fixtures/` directory, so nothing prevents you from splitting a YAML fixture file into smaller pieces. The important thing to keep in mind is that foreign keys impose a processing order for the tables. To make sure that they are parsed in the correct order, prefix the files with an ordinal number.

+   100_article_import_data.yml
+   200_comment_import_data.yml
+   300_rating_import_data.yml

> Doctrine does not need specific file names as it automatically takes care of executing the SQL statements in the right order.

# # Deploying Applications

Symfony offers shorthand commands to synchronize two versions of a website. These commands are mostly used to deploy a website from a development server to a final host, connected to the Internet.

# ## Using rsync for Incremental File Transfer

Sending the root project directory by FTP is fine for the first transfer, but when you need to upload an update of your application, where only a few files have changed, FTP is not ideal. You need to either transfer the whole project again, which is a waste of time and bandwidth, or browse to the directories where you know that some files changed, and transfer only the ones with different modification dates. That's a time-consuming job, and it is prone to error. In addition, the website can be unavailable or buggy during the time of the transfer.

The solution that is supported by symfony is rsync synchronization through an SSH layer. Rsync<sup>57</sup> is a command-line utility that provides fast incremental file transfer, and it's open source. With incremental transfer, only the modified data will be sent. If a file didn't change, it won't be sent to the host. If a file changed only partially, just the differential will be sent. The major advantage is that rsync synchronizations transfer only a small amount of data and are very fast.