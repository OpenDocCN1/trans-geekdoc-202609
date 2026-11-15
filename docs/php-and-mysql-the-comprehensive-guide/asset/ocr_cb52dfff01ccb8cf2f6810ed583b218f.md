# Chapter 21
Microsoft SQL Server

Microsoft has been committed to open source for a long time—and recently, efforts have intensified even further. Microsoft’s database management system, SQL Server, is not yet open source (but perhaps at some point in the future!). Nevertheless, you can access it with PHP.

The battle of the individual database manufacturers is in full swing. Microsoft lagged behind for a long time and did not even have its own product. But then a pattern emerged that had already been crowned with success in many other places. First, a competing product was bought up—in this case, by Sybase. The intermediate goal was to gain market presence. Then the company from Redmond hired some of the brightest minds in the industry and rebuilt and expanded the existing product. Microsoft SQL Server (MSSQL) is now a respectable product and plays in the big league.

In the past, it was even possible to access an MSSQL installation from Linux. However, current versions of Microsoft SQL Server no longer support this approach, which is why we are not describing it here. If you have such a heterogeneous network that Apache runs on Linux, but the SQL Server (inevitably) runs on Windows, then you will have to find a workaround by implementing a type of API for the database on the Windows platform and then accessing it via PHP (and HTTP, for example). Or, even better—use the SQL Server under Linux right away!¹

Under Windows, it is of course possible to access Microsoft SQL Server either way. Depending on the version of SQL Server, however, there are some detailed changes in the control.

# 21.1 Preparations

Microsoft SQL Server Developer Edition is a free version that may not be used on production systems but works without restriction for development and testing. Alternatively, you can also use the other free version, Microsoft SQL Server Express Edition. This is a version of MSSQL that has been released for productive use but is somewhat slimmed down in terms of functionality. For example, all graphical administration tools are

1 For further information, visit http://s-prs.co/v60224.