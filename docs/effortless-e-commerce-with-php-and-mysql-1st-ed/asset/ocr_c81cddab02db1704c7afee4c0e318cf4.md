```
```sql
) ENGINE=InnoDB DEFAULT CHARSET=utf8;
CREATE TABLE `sales` (
  `id` INT UNSIGNED NOT NULL AUTO_INCREMENT,
  `product_type` ENUM('coffee','other') DEFAULT NULL,
  `product_id` MEDIUMINT UNSIGNED NOT NULL,
  `price` DECIMAL(5,2) UNSIGNED NOT NULL,
  `start_date` date NOT NULL,
  `end_date` date DEFAULT NULL,
  PRIMARY KEY (`id`),
  KEY `start_date` (`start_date`),
  KEY `product_type` (`product_type`,`product_id`)
) ENGINE=MyISAM DEFAULT CHARSET=utf8;
```
```

```
```sql
CREATE TABLE `sizes` (
  `id` TINYINT UNSIGNED NOT NULL AUTO_INCREMENT,
  `size` VARCHAR(40) NOT NULL,
  PRIMARY KEY (`id`),
  UNIQUE KEY `size` (`size`)
) ENGINE=MyISAM DEFAULT CHARSET=utf8;
```
```

```
```sql
CREATE TABLE `specific_coffees` (
  `id` MEDIUMINT UNSIGNED NOT NULL AUTO_INCREMENT,
  `general_coffee_id` TINYINT UNSIGNED NOT NULL,
  `size_id` TINYINT UNSIGNED NOT NULL,
  `caf_decaf` ENUM('caf','decaf') DEFAULT NULL,
  `ground_whole` ENUM('ground','whole') DEFAULT NULL,
  `price` DECIMAL(5,2) UNSIGNED NOT NULL,
  `stock` MEDIUMINT UNSIGNED NOT NULL DEFAULT '0',
  `date_created` TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
  PRIMARY KEY (`id`),
  KEY `general_coffee_id` (`general_coffee_id`),
  KEY `size` (`size_id`)
) ENGINE=MyISAM DEFAULT CHARSET=utf8;
```
```

```
```sql
CREATE TABLE `transactions` (
  `id` INT UNSIGNED NOT NULL AUTO_INCREMENT,
  `order_id` INT UNSIGNED NOT NULL,
  `type` VARCHAR(18) NOT NULL,
  `amount` DECIMAL(7,2) NOT NULL,
  `response_code` TINYINT(1) UNSIGNED NOT NULL,
  `response_reason` TINYTEXT,
  `transaction_id` BIGINT(20) UNSIGNED NOT NULL,
  `response` text NOT NULL,
  `date_created` TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
  PRIMARY KEY (`id`),
```
```