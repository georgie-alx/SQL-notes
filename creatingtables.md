# Temporary Tables
## SELECT-INTO - Temporary Tables

```
SELECT *
INTO #table3
FROM table1
UNION ALL
SELECT *
FROM table2
```
* For the INTO: use hex before table name (to specify that it's a temporary table)
* For the UNION ALL: Must make sure that the columns of both tables are exactly the same


## CREATE TABLE - Permanent Tables
```
CREATE TABLE db.Products
  (ProductID            int PRIMARY KEY NOT NULL,
   ProductName          varchar(25) NOT NULL,
   Price                money NULL,
   ProductDescription   text NULL)
```

## Populate Tables

Standard Syntax
```
INSERT db.Products (ProductID, ProductName, Price, ProductDescription)
  VALUES(20, 'Screwdriver', 5.20, 'Flat head')
```

Changing Order of Columns
```
INSERT db.Products (ProductName, ProductID, Price, ProductDescription)
  VALUES('Screwdriver', 20, 5.20, 'Flat head')
```

Skip column list but keep values in order
```
INSERT db.Products
  VALUES(20, 'Screwdriver', 5.20, 'Flat head')
```

