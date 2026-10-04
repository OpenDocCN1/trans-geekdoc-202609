# Chapter 14: Shopping Cart

they will be able to see what you've written to the database. Keep in mind there is no requirement that you store the credit-card numbers anywhere. You can simply validate the number and drop it from memory. If it is never written to a disk, it will be very hard to steal.

Notice that user and address information is separated. This is so you can enable a single user (who will identify him—or herself by an e-mail address) to supply two addresses—may work and home.
The shipping table will store options for moving your goods. It might have options for UPS, USPS, and Fed Ex, if you choose. I'll talk a little more about these options in the "Code Overview".
The status table will enable you to know if the order is backordered, shipped, cancelled, and the cc_types table store credit cards that you're willing to accept.

```
# Table structure for table 'addresses'
#
```

```
CREATE TABLE addresses (
address_id int(11) NOT NULL auto_increment,
user_id int(11) NOT NULL,
address varchar(40),
address2 varchar(40),
city varchar(40),
state char(2),
zip varchar(10),
phone varchar(20),
PRIMARY KEY (address_id),
KEY address_user_key (user_id);
```

```
);
#
```

```
# Table structure for table 'cc_types'
#
```

```
CREATE TABLE cc_types (
cc_type_code char(3) NOT NULL,
cc_type varchar(30) NOT NULL
```

```
);
#
```

```
# Table structure for table 'orders'
#
```