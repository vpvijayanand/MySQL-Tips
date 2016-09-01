---
Title: Avoid SELECT
Tip-number: 4
Tip-username: Vijayanand
Tip-username-profile: https://github.com/vpvijayanand
Tip-description: MySQL datatype use for store an IP address
---

To store IP address in mysql database then don’t make a mistake of using varchar datatype because you can use INT UNSIGNED 4(BYTE) datatype. 
Using integer datatype can save you more space in database.

Use INET_ATON() insert query  and INET_NTOA() in select query  as below.

Create Table :
```php
CREATE TABLE IF NOT EXISTS `ip_addresses` (
  `id` int(10) unsigned NOT NULL AUTO_INCREMENT,
  `ip_address` INT(4) UNSIGNED NOT NULL,
  PRIMARY KEY (`id`)
);
```

Insert Data :
```php
INSERT INTO `ip_addresses` (`ip_address`) VALUES (INET_ATON("255.255.255.255"));
```

Select Data : 
```php
SELECT id, INET_NTOA(`ip_address`) as ip FROM `ip_addresses`;
```
