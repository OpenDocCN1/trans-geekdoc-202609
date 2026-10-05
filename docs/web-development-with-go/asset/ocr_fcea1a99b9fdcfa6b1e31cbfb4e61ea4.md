While we won’t be using the standard library’s database/sql package, and will instead be opting for GORM, the code in this book is set up in a way that you could easily replace all of the GORM code with the database/sql package with relative ease, so don’t be discouraged if you were hoping to use more raw SQL. You still can, but I advice waiting until you have a working application to do so.

# ##8.2 Setting up PostgreSQL

Before we can get started using PostgreSQL with Go you are going to do a little bit of work outside of this book.

While I hope to eventually add all of the content required for getting started with SQL and Postgres as either an appendix or additional chapter to this book, I am opting to refer you to an external resource (my blog) for now. You can see the articles here: http://www.calhoun.io/using-postgresql-with-golang/

Before heading to the next chapter, you will need to have a basic understanding of everything covered in the following four subsections.

# ##8.2.1 Install PostgreSQL

How you do will vary based on your operating system, but you will want to find a guide for your OS and follow along with to get Postgres installed.

While installing Postgres, try to keep an eye out for the information in Table 8.1, as you will need this later in the book.

The guides on my blog should keep all this information pretty consistent regardless of your OS, but if you use a different guide it might not have you setup the postgres role.