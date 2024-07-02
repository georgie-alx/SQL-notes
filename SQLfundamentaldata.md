# SQL Data Types

[PostgreSQL Documentation](https://www.w3resource.com/PostgreSQL/data-type-formatting-functions.php)

## String
Always use single quotes `' '` to represent a string.

## Date
Format: `YYYY-MM-DD` <br>
If no time is specified, assumed to be 00:00. Note for filter ranges!

### Changing Date to String
```
SELECT TO_CHAR(payment_date, 'MM-DD-YYYY')
FROM payment
```

## Timestamps and EXTRACT
`SHOW TIMEZOME` -> Asia/Singapore <br>
`SELECT NOW()` -> "2024-06-06 11:08:00.811796+08" <br>
`SELECT TIMEOFDAY()` -> "Thu Jun 06 11:08:32.782107 2024 +08"<br>
`SELECT CURRENT_TIME` -> "11:09:38.836122+08:00"<br>
`SELECT CURRENT_DATE` -> "2024-06-06"<br>

### EXTRACT()
`EXTRACT(YEAR FROM date_col)` -> e.g. "2024"
- Can be used for YEAR, MONTH, QUARTER, DAY etc.<br>
e.g.
``` SELECT EXTRACT(YEAR FROM payment_date) AS year FROM payment```
returns `year` column with only the year info of the payment date

### AGE()
`AGE(date_col)` -> e.g. 13 years 1 mon 5 days 01:34:13.004334
Returns current age from the given datetime-stamp




