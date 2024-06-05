# SQL Fundamental STATEMENTS

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

```
SELECT COUNT(*) FROM tbl
WHERE col1 <= 50;
```
|**Count** |
|----------|
| 37 |
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
- `SELECT WHERE` + `JOIN` + `ORDER BY` + `LIMIT` - First 10 payments from joined table
```
SELECT * 
FROM customer
LEFT JOIN payment
ON customer.customer_id = payment.customer_id
WHERE payment.amount != 0.0
ORDER BY payment.payment_date ASC
LIMIT 10;
```
<br>


## ORDER BY

To sort rows

`SELECT column_name1, column_name2 FROM table_name ORDER BY col1 ASC`
<br>
`SELECT column_name1, column_name2 FROM table_name ORDER BY col1 DESC`
<br>

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

## BETWEEN

`SELECT * FROM tbl WHERE column_name BETWEEN xx AND xx`
<br>
`SELECT * FROM tbl WHERE column_name NOT BETWEEN xx AND xx`
<br>
`SELECT * FROM tbl WHERE date NOT BETWEEN '2024-04-30' AND '2025-04-30'`
<br><br>
Notes: 
- Date format is YYYY-MM-DD
- Days start at 00:00, which means BETWEEN date1 AND date2 = BETWEEN date1 00:00 AND date2 00:00 (i.e. date2 is excluded from the range)

## IN

`SELECT column_name FROM table_name WHERE column_name IN ('xxx','xxx')`
<br>

```
SELECT col1, col2, col3 FROM payment
WHERE col1 IN (0.99,1.98,1.99);
```
|**Col 1**|**Col 2**|**Col 3**|
|----------|----------|----------|
| 0.99    | xxx    | xxx    |
| 1.99    | xxx    | xxx    |

<br>

```
SELECT col1, col2, col3 FROM payment
WHERE col1 NOT IN (0.99,1.98,1.99);
```
|**Col 1**|**Col 2**|**Col 3**|
|----------|----------|----------|
| 3.99    | xxx    | xxx    |
| 8.99    | xxx    | xxx    |



## LIKE / ILIKE

`LIKE` is case sensitive, `ILIKE` is case-insensitive.

### Wildcards (%) and (_)
_% matches any sequence of characters_ <br>
`SELECT * WHERE column_name LIKE '%a'` - string ends with 'a'
<br>
`SELECT * WHERE column_name ILIKE 'a%'` - string starts with 'a' or 'A'
<br>

_\_ matches any single character_ <br>
`SELECT * WHERE column_name LIKE 'Mission Impossible _'` - e.g. Mission Impossible 2
`SELECT * WHERE column_name LIKE 'Version#__ - %` - e.g. Version#A7
<br> 

_Combine them for more advanced matching_ <br>
`SELECT * WHERE column_name LIKE '_her%` - e.g. C _her_ yl, T _her_ esa, S _her_ ri
<br><br>
For more information on pattern matching and regular expressions in PostgreSQL, refer to this [Medium article](https://towardsdatascience.com/pattern-matching-and-regular-expressions-in-postgresql-cd1fa76e5f3f) or [postgreSQL documentation](https://www.postgresql.org/docs/current/functions-matching.html).


## LENGTH
`LENGTH(col)`


