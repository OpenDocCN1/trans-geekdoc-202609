Only options named in that table can be set or retrieved.

+   - Returns the value of the *option* or DB_Error if the *option* parameter is not one of the valid options.
+   - See Code Listing 13 on page 32 for a usage example.

# DB_common::prepare

```
resource prepare( string $query )
```

The **prepare()** method prepares a specially-formatted query string for use in the prepare/execute methodology of querying. Typically this is used when multiple similar queries will be run simultaneously.

The *query* parameter is specially formatted to include placeholder characters that will represent real data when the execute() method is called. The placeholder characters and their meanings are shown in Table 6.

| Placeholder Character | Definition |
|---|---|
| ? | A quoted scalar value such as a string or integer. |
| & | Replaced data must be a file name. The contents of the file will be the actual data. |
| ! | Scalar value inserted AS IS. |

**Table 6:** Placeholder characters for use in query() method

The example shown in Code Listing 25 illustrates how the **prepare()** statement can be used to facilitate inserting several similar rows of data into the *Paychecks*.