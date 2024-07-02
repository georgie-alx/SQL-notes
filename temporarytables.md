# Temporary Tables
## SELECT-INTO Statements

```
SELECT *
INTO #table3
FROM table1
UNION ALL
SELECT *
FROM table2
```
* For the INTO: use hex before table name
* For the UNION ALL: Must make sure that the columns of both tables are exactly the same
