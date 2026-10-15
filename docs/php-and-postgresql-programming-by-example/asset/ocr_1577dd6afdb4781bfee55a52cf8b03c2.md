# 3.1 CRUD Operations

CRUD (Create, Read, Update, Delete) operations are basic data manipulation for database. In this chapter we will develop PHP application to execute CRUD operations. We use existing database, postgres. Then, create a table, called **hrd_employee**. The following is a query for creating the table.

```
CREATE TABLE public.hrd_employee
(
  id SERIAL PRIMAY KEY,
  name character(30),
  department character(30),
  level character(10),
  created timestamp without time zone
)
WITH (
  OIDS=FALSE
);
ALTER TABLE public.hrd_employee
  OWNER TO postgres;
```

You can run it using pgAdmin. You also can run itu using other tool, for instance, DataGrip from Jetbrains, https://www.jetbrains.com/datagrip/ .