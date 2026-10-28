# The SQL script that creates the my_guitar_shop2 database
Page 2

```
CREATE TABLE orderItems (
    itemID          INT             NOT NULL        AUTO_INCREMENT,
    orderID         INT             NOT NULL,
    productID       INT             NOT NULL,
    itemPrice       DECIMAL(10,2)   NOT NULL,
    discountAmount  DECIMAL(10,2)   NOT NULL,
    quantity        INT NOT NULL,
    PRIMARY KEY (itemID),
    INDEX orderID (orderID),
    INDEX productID (productID)
);

CREATE TABLE products (
    productID       INT             NOT NULL        AUTO_INCREMENT,
    categoryID      INT             NOT NULL,
    productCode     VARCHAR(10)     NOT NULL,
    productName     VARCHAR(255)    NOT NULL,
    description     TEXT            NOT NULL,
    listPrice       DECIMAL(10,2)   NOT NULL,
    discountPercent DECIMAL(10,2)   NOT NULL        DEFAULT 0.00,
    dateAdded       DATETIME        NOT NULL,
    PRIMARY KEY (productID),
    INDEX categoryID (categoryID),
    UNIQUE INDEX productCode (productCode)
);

CREATE TABLE categories (
    categoryID      INT             NOT NULL        AUTO_INCREMENT,
    categoryName    VARCHAR(255)    NOT NULL,
    PRIMARY KEY (categoryID)
);

CREATE TABLE administrators (
    adminID         INT             NOT NULL        AUTO_INCREMENT,
    emailAddress    VARCHAR(255)    NOT NULL,
    password        VARCHAR(255)    NOT NULL,
    firstName       VARCHAR(255)    NOT NULL,
    lastName        VARCHAR(255)    NOT NULL,
    PRIMARY KEY (adminID)
);

-- Create a user and grant privileges to that user
GRANT SELECT, INSERT, UPDATE, DELETE
ON *
TO mgs_user@localhost
IDENTIFIED BY 'pa55word';
```