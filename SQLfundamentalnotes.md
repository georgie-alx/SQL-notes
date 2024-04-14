# SQL Fundamentals

## SELECT

Selection of Columns

`SELECT column_name FROM table_name`
<br><br>


```
SELECT * FROM tbl;
```
|**Col 1** |**...**|**Col n**|
|----------|----------|----------|
| xx    | ...    | xx    |
| xx    | ...    | xx    |
<br>

```
SELECT col1, col2 FROM tbl;
```
|**Col 1** |**Col 2**|
|----------|----------|
| xx    | xx    |
| xx    | xx    |
<br>

## SELECT DISTINCT

`SELECT DISTINCT column_name FROM table_name`
<br><br>

```
SELECT DISTINCT first_name FROM tbl;
```
|**First Name** |
|----------|
| Anne    |
| Sally    |
<br>


```
SELECT DISTINCT first_name, last_name FROM tbl;
```
|**First Name** |**Last Name**|
|----------|----------|
| Anne    | Carter    |
| Anne    | Peterson    |
| Sally    | Green    |
<br>


## COUNT

Total no. of rows in Query result

`SELECT COUNT(column_name/query) FROM table_name;`
<br><br>

```
SELECT COUNT(DISTINCT first_name, last_name) FROM tbl;
```
|**Count** |
|----------|
| 3    |
<br>


## SELECT WHERE 

`SELECT column_name1, columne_name2 FROM table_name WHERE (conditions);`
<br><br>
_Filtering of rows using the following operators:_
|**Operator** |**Description**|
|:----------:|:----------:|
| =    | Equal    |
| >    | Greater Than    |
| <    | Less Than    |
| >=    | Greater Than or Equal to    |
| <=    | Less Than or Equal to    |
| <> or != | Not Equal to    |
<br>

```
SELECT * from tbl
WHERE col1 > 4;
```
|**Col 1** |**...**|**Col n**|
|----------|----------|----------|
| 5    | ...    | xx    |
| 7    | ...    | xx    |
<br>

```
SELECT * from tbl 
WHERE col1 = 4 OR col2 = 'a';
```
|**Col 1** |**Col 2**|**...**|**Col n**|
|----------|----------|----------|----------|
| 5    | a | ...    | xx    |
| 4    | b | ...    | xx    |
<br>

More complicated SELECT WHERE statements:
- `SELECT WHERE` + `JOIN` - querying from a joined table
```
SELECT *
FROM customer
LEFT JOIN address ON address.address_id = customer.address_id
WHERE address.address = '259 Ipoh Drive';
```
- `SELECT WHERE` + `ORDER BY` + `LIMIT` - Top 5 most recent payments
```
SELECT * FROM payment
WHERE amount != 0.0
ORDER BY payment_date DESC
LIMIT 5;
```

<br>


## ORDER BY

To sort rows

`SELECT column_name1, column_name2 FROM table_name ORDER BY col1 ASC`
`SELECT column_name1, column_name2 FROM table_name ORDER BY col1 DESC`

```
SELECT col1, col2, col3 from tbl 
ORDER BY col1 ASC, col3 ASC;
```
|**Col 1**|**Col 2**|**Col 3**|
|----------|----------|----------|
| A    | xxx    | 100    |
| A    | xxx    | 400    |
| B    | xxx    | 200    |
| B    | xxx    | 300    |
<br>

_Note: It is possible to order by a column in the table but not select it._
```
SELECT col2, col3 from tbl 
ORDER BY col1 ASC;
```
|**Col 2**|**Col 3**|
|----------|----------|
| xxx    | 100    |
| xxx    | 400    |
| xxx    | 200    |
| xxx    | 300    |
<br>

## LIMIT

To limit the number of rows returned. Coupled with `ORDER BY`, this will return the Top X results.

```
SELECT col1, col2, col3 from tbl 
ORDER BY col1 ASC, col3 ASC
LIMIT 2;
```
|**Col 1**|**Col 2**|**Col 3**|
|----------|----------|----------|
| A    | xxx    | 100    |
| A    | xxx    | 400    |
<br>



