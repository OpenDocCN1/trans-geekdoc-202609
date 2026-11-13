```
mysql_query("LOCK TABLES inventory WRITE, shipping
WRITE");

// Perform the operation...

mysql_query("UNLOCK TABLES");
```

Many high-end database servers (e.g. Oracle, MS SQL Server, etc.) support a feature called **transactions**, which lets you define complex operations like those above so they may be performed in a single, uninterrupted step.

Consider what would happen if your server were struck by a power failure halfway through an update of the tables in response to a client order. For example, the server might have crashed after it updated your shipping table, but before it updated your inventory table, in response to a customer's order.

Transactions allow a group of table updates such as this to be defined so that updates will occur either to all of them, or none of them. As of this writing, support for transactions in MySQL is available in beta form. Check the MySQL Website for the latest information.

# # Column and Table Name Aliases

In some situations, it may be more convenient to be able to refer to MySQL columns and tables using different names. Let's take the example of a database used by an airline's online booking system (this example actually came up in the SitePoint.com forums). To represent the flights offered by the airline, the database contains two tables: **Flights** and **Cities**. Each entry in the **Flights** table represents an actual flight between two cities -- the origin and destination of the flight. Obviously, **Origin** and **Destination** are columns in the **Flights** table, with other columns for things like the date and time of the flight, the type of aircraft, the flight numbers, and the various fares.

The **Cities** table contains a list of all the cities to which the airline flies. Thus, both the **Origin** and **Destination** columns in the **Flights** table will just contain ID's referring to entries in the **Cities** table. Now, consider these queries. To retrieve a list of flights with their origins:

```
mysql> SELECT Flights.Number, Cities.Name
    -> FROM Flights, Cities
    -> WHERE Flights.Origin = Cities.ID;
```

| Number | Name |
| :--- | :--- |
| CP110 | Montreal |
| CP226 | Sydney |
| QF2026 | Melbourne |
| ... | ... |