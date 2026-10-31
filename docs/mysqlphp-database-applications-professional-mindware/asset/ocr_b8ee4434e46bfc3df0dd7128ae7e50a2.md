they will be able to see what you've written to the database. Keep in mind that there is no requirement that you store the credit-card numbers anywhere. You can simply validate the number and then drop it from memory. If it is never written to a disk, it will be very hard for anyone to steal.

Notice that user and address information is separated. This is so you can enable a single user (who will identify him- or herself by an e-mail address) to supply two addresses — maybe work and home.

The shipping table will store options you supply for moving your goods. It might have options for UPS, USPS, and Fed Ex, if you choose. I'll talk a little more about these options in the “Code Overview” section.

The status table will enable you to note if the order is backordered, shipped, or cancelled, or has any other status that might come up in your shop.

And the cc_types table stores credit cards that you're willing to accept.

```
# Table structure for table 'addresses'
#
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
  KEY address_user_key (user_id)
);
# ------------------------------------------------------------
#
# Table structure for table 'cc_types'
#
CREATE TABLE cc_types (
  cc_type_code char(3) NOT NULL,
  cc_type varchar(30) NOT NULL
);
#
# ------------------------------------------------------------
#
# Table structure for table 'orders'
#
```