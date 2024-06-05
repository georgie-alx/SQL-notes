# JOIN Statements

## INNER JOIN
An inner join results in the set of records that match in both tables.

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
