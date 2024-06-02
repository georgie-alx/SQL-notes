# AGGREGATION FUNCTIONS

## MIN() and MAX()
```SELECT MIN(replacement_cost) FROM film``` and ```SELECT MAX(replacement_cost) FROM film```
Combining the 2 above: 
```SELECT MIN(replacement_cost), MAX(replacement_cost) FROM film```
|**MIN(replacement cost)** |**MAX(replacement cost)**|
|----------|----------|
| xx    | xx    |
<br>

## COUNT()
```COUNT(film_id) FROM film``` is the same as ```COUNT(*) FROM film```

## AVG()
```SELECT AVG(replacement_cost) FROM film```

## ROUND()
```SELECT ROUND(AVG(replacement_cost),2) FROM film```

## SUM()
```SELECT SUM(replacement_cost) FROM film```

#GROUP BY

`SELECT category_col, AGG(data_col) FROM table GROUP BY category_col`

