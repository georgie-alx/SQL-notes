# JOIN Statements

![SQL Joins](https://github.com/georgie-alx/SQL-notes/blob/main/images/SQLJoins.PNG)

## INNER JOIN
An inner join results in the set of records that match in both tables.
- Table order does not matter
- using JOIN without the INNER: PostgreSQL will treat it as INNER JOIN
  
```
SELECT * FROM TableA
INNER JOIN TableB
ON TableA.col_match = TableB.col_match
```

e.g. Registrations for an Event vs Actual Login for the Event

|**Registration ID** |**Name**|
|----------|----------|
| 1    | Andrew    |
| 2    | Bob    |
| 3    | Charlie    |
| 4    | David    |
<br>

|**Login ID** |**Name**|
|----------|----------|
| 1    | Xavier    |
| 2    | Andrew    |
| 3    | Yolanda    |
| 4    | Bob    |
<br>

```
SELECT * FROM Registrations
INNER JOIN Logins
ON Registrations.Name = Logins.Name
```

|**Registration ID** |**Name**|**Login ID**|**Name**|
|----------|----------|----------|----------|
| 1    | Andrew    | 2    | Andrew    |
| 2    | Bob    | 4    | Bob    |

### _Inner Join - Specifying wanted columns:_
```
SELECT reg_id, Logins.Name, log_id
FROM Registrations INNER JOIN Logins
ON Registrations.Name = Logins.Name
```
_Note: for columns that are present in both original tables, to specify which table to extract the column from._

|**Registration ID** |**Name**|**Login ID**|
|----------|----------|----------|
| 1    | Andrew    | 2    |
| 2    | Bob    | 4    |

## FULL OUTER JOIN
- Results entire set of records
- Table order does not matter

```
SELECT * FROM TableA
FULL OUTER JOIN TableB
ON TableA.col_match = TableB.col_match 
```
|**Registration ID** |**Name**|**Login ID**|**Name**|
|----------|----------|----------|----------|
| 1    | Andrew    | 2    | Andrew    |
| 2    | Bob    | 4    | Bob    |
| 3    | Charlie    |  _null_   |  _null_   |
| 4    | David    |  _null_   |  _null_   |
| _null_    | _null_    | 1    | Xavier    |
| _null_    | _null_    | 3    | Yolanda    |


## "OUTER JOIN" - FULL OUTER JOIN + WHERE
- Results in records that only appear in 1 table

```
SELECT * FROM TableA
FULL OUTER JOIN TableB
ON TableA.col_match = TableB.col_match
WHERE TableA.id IS null OR TableB.id IS NULL
```

e.g.
```
SELECT * FROM Registrations
FULL OUTER JOIN Logins
ON Registrations.Name = Logins.Name
WHERE Registrations.reg_id is null
OR Login_id is null
```
|**Registration ID** |**Name**|**Login ID**|**Name**|
|----------|----------|----------|----------|
| 3    | Charlie    |  _null_   |  _null_   |
| 4    | David    |  _null_   |  _null_   |
| _null_    | _null_    | 1    | Xavier    |
| _null_    | _null_    | 3    | Yolanda    |

## LEFT OUTER JOIN - Full Left Table Records
- results in the set of records in the left table + any **matched** records from the right table
- table order matters

```
SELECT * FROM TableA --Left Table
LEFT OUTER JOIN TableB --Right Table
ON TableA.col_match = TableB.col_match
```

e.g.
```
SELECT * FROM Registrations
LEFT OUTER JOIN Logins
ON Registrations.Name = Logins.Name
```
|**Registration ID** |**Name**|**Login ID**|**Name**|
|----------|----------|----------|----------|
| 1    | Andrew    | 2    | Andrew    |
| 2    | Bob    | 4    | Bob    |
| 3    | Charlie    |  _null_   |  _null_   |
| 4    | David    |  _null_   |  _null_   |

## LEFT OUTER JOIN - Unmatched Left Table Records
```
SELECT * FROM Registrations
LEFT OUTER JOIN Logins
ON Registrations.Name = Logins.Name
WHERE login_id IS null
```

|**Registration ID** |**Name**|**Login ID**|**Name**|
|----------|----------|----------|----------|
| 3    | Charlie    |  _null_   |  _null_   |
| 4    | David    |  _null_   |  _null_   |
<br>


## Additional Challenges
### Multiple Joins
```
SELECT title, first_name, last_name FROM film
INNER JOIN film_actor
ON film.film_id = film_actor.film_id
INNER JOIN actor
ON film_actor.actor_id = actor.actor_id
WHERE first_name = 'Nick' AND last_name = 'Wahlberg'
```



