# Two column attributes for working with a primary key

| Attribute | Description |
|---|---|
| `PRIMARY KEY` | Specifies that the column is the primary key for the table. |
| `AUTO_INCREMENT` | Automatically generates an integer value for the column. By default, this value starts at 0 and increments by a value of 1. |

# A table with a column-level primary key

```
CREATE TABLE customers (
    customerID       INT             NOT NULL    PRIMARY KEY AUTO_INCREMENT,
    emailAddress     VARCHAR(255)    NOT NULL    UNIQUE
);
```

# A table with a table-level primary key

```
CREATE TABLE customers (
    customerID       INT             NOT NULL    AUTO_INCREMENT,
    emailAddress     VARCHAR(255)    NOT NULL    UNIQUE,

    PRIMARY KEY (customerID)
);
```

# A table with a two-column primary key

```
CREATE TABLE orderItems (
    orderID          INT             NOT NULL,
    productID        INT             NOT NULL,
    itemPrice        DECIMAL(10,2)   NOT NULL,
    discountAmount   DECIMAL(10,2)   NOT NULL,
    quantity         INT             NOT NULL,

    PRIMARY KEY (orderID, productID)
);
```

# Description

+   - A *primary key* requires that each row has unique values for the column or columns that are used for the primary key, and it does not allow NULL values.
+   - You code a *column-level primary key* as part of the definition of the column definition. You code a *table-level primary key* as if it is a separate column definition, and you name its column or columns within that definition.

Figure 17-4 — How to code a primary key