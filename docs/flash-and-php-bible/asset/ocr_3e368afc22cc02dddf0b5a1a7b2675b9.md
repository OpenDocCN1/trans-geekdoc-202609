The next page allows you to customize the InnoDB storage system, but it is best to just leave it
with the default settings.

In some instances, you may want to choose a separate location, which you can do by clicking the
Browse button to the right of the installation box. Choosing a different location is only necessary
when the Drive Info notice at the bottom of the window reports a small amount of Free disk space,
which means your database could consume the remainder of your resources.

> Make sure you never choose a removable drive as the storage location because you
> could harm the database if that drive is not attached at all times.

As stated earlier, most often it is best to leave this option at its default choice, as shown in Figure
1.11, to ensure your database functions properly.

# FIGURE 1.11
InnoDB Tablespace settings

![](bbox=[0.1, 0.42, 0.48, 0.655])

The next option is an approximation of how many concurrent connections your MySQL database
will need to handle. Because this installation is being performed on a development server, an esti-
mate of no more than 25 is a realistic assumption. Actually, it would be rare to have more than 5,
but 25 is a good base number.

Select the Online Transaction Processing (OLTP) option under the “Decision Support” heading
when you are developing a Web application to which the public has access. This is because you
really have no idea how many people may attempt to access the system at any given time. As your
application continues to grow you may even need to chain multiple databases together to handle
the load, but for now one database is enough, especially considering this installation is being per-
formed on your local system.