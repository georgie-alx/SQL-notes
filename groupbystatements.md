# AGGREGATION FUNCTIONS

## MIN() and MAX()

```
SELECT MIN(replacement_cost), MAX(replacement_cost) FROM film
```

|**MIN(replacement cost)** |**MAX(replacement cost)**|
|----------|----------|
| xx    | xx    |
<br>

## COUNT()
`COUNT(col_name) FROM film` or `COUNT(*) FROM film`

## AVG()
`SELECT AVG(col_name) FROM film`

## ROUND()
`SELECT ROUND(AVG(col_name),2) FROM film`

## SUM()
`SELECT SUM(col_name) FROM film`


# GROUP BY

`SELECT category_col, AGG(data_col) FROM table (WHERE) GROUP BY category_col (ORDER BY col, LIMIT x)`
- the `GROUP BY` must be after a `FROM` or `WHERE` (pre-filter the data before grouping)
- in the `SELECT` statement, columns must either have an aggregate functino or be in the `GROUP BY` call
- usually the order of the columns in `SELECT` statement will be the same in `GROUP BY`

```
SELECT company, division, SUM(sales)
FROM finance_table
WHERE division IN ('marketing', 'transport')
GROUP BY company, division
```

```
SELECT company, SUM(sales)
FROM finance_table
WHERE division IN ('marketing', 'transport')
GROUP BY company,
ORDER BY SUM(sales) DESC
LIMIT 5
```

## WHERE(criteria)
- `WHERE` statements should not refer to the aggregation result, it is the filter _before_ the GROUP BY

```
SELECT customer_id, SUM(amount) FROM payment
WHERE customer_id != 148
GROUP BY customer_id
HAVING sum(amount)>200
ORDER BY SUM(amount) DESC
LIMIT 5
```
`customer_id` col selected 

## GROUP BY date_col

`SELECT DATE(date_col) FROM table`
- timestamp columns will have time information, which will be disregarded using `DATE()`


## HAVING(criteria)
- `HAVING` allows use of aggregate result as filter

```
SELECT store_id, COUNT(*) FROM customer
WHERE staff_id = 2
GROUP BY store_id
HAVING COUNT(*)>300
```
Note: `WHERE` should come before `GROUP BY`

