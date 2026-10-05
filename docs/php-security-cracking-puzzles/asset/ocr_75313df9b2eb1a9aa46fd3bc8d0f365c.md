# I.4.12. Saving Images in a Database

In the previous task, it was suggested that you save MP3 files in a database. There is a more important storage task — saving images in a database. In contrast to the previous script, it is necessary to organize the storage of images, for example, three images per page, instead of the links pointing to them (Fig. I.4.13). The image must not be saved in a temporary file on the server. On the contrary, it must be transmitted directly from the database to the client.

![](bbox=[0.125, 0.319, 0.875, 0.582])

Fig. I.4.13. Downloading images from the database

# I.4.13. Downloading Data from a Database Dump

When moving data from server to server, so-called database dumps are often used. Database dumps are text files containing sequential SQL instructions that, when executed allow you to reproduce the database on every SQL server (Listing I.4.7).

> NOTE The dump file shown in Listing I.4.7 can be found in the /scripts/4/catalog.sql file on the accompanying CD-ROM.