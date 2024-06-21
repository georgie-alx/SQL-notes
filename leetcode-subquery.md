# LeetCode Sub-Queries

## [Rising Temperature](https://leetcode.com/problems/rising-temperature/description/?envType=study-plan-v2&envId=top-sql-50)
```
SELECT b.id FROM Weather As a
JOIN Weather As b
ON b.recordDate = DATE_ADD(a.recordDate, INTERVAL 1 day)
WHERE b.temperature > a.temperature
```

## [Managers with at Least 5 Direct Reports](https://leetcode.com/problems/managers-with-at-least-5-direct-reports/?envType=study-plan-v2&envId=top-sql-50)
```
SELECT name FROM Employee
WHERE id in (select managerId from employee group by managerId having count(id) >= 5);
```

## [Students and Examinations](https://leetcode.com/problems/students-and-examinations/description/?envType=study-plan-v2&envId=top-sql-50)
```
SELECT s.student_id, s.student_name, sub.subject_name, COUNT(e.student_id) AS attended_exams
FROM Students s
CROSS JOIN Subjects sub
LEFT JOIN Examinations e ON s.student_id = e.student_id AND sub.subject_name = e.subject_name
GROUP BY s.student_id, s.student_name, sub.subject_name
ORDER BY s.student_id, sub.subject_name;
```

## [Confirmation Rate](https://leetcode.com/problems/confirmation-rate/description/?envType=study-plan-v2&envId=top-sql-50)
```
select signups.user_id, round(avg(if(Confirmations.action="confirmed",1,0)),2) as confirmation_rate
from signups 
left join confirmations on signups.user_id=confirmations.user_id
group by user_id
```

## [Product Price at a Given Date](https://leetcode.com/problems/product-price-at-a-given-date/description/?envType=study-plan-v2&envId=top-sql-50)
```
WITH sub AS  (SELECT product_id, new_price AS price,change_date,
ROW_NUMBER() OVER (PARTITION BY product_id ORDER BY change_date desc) rn
FROM Products WHERE change_date<='2019-08-16' )
SELECT product_id, price FROM sub WHERE rn = 1
UNION
SELECT distinct(product_id),10 AS price FROM Products WHERE product_id NOT IN
(SELECT product_id FROM sub WHERE rn = 1)
```

## [Product Sales Analysis III](https://leetcode.com/problems/product-sales-analysis-iii/description/?envType=study-plan-v2&envId=top-sql-50)
```
# Write your MySQL query statement below
SELECT product_id, year AS first_year, quantity, price
FROM Sales
WHERE (product_id , year) IN (
    SELECT product_id, min(year) FROM Sales GROUP BY product_id
)
```

## [Game Play Analysis IV](https://leetcode.com/problems/game-play-analysis-iv/description/?envType=study-plan-v2&envId=top-sql-50)
```
SELECT ROUND(COUNT(DISTINCT player_id)/(SELECT COUNT(DISTINCT player_id) FROM Activity),2) As fraction 
FROM Activity 
WHERE (player_id, event_date) IN 
(
    SELECT player_id, DATE_ADD(MIN(event_date) , INTERVAL 1 day) AS event_date 
    FROM Activity
    GROUP BY player_id
)
```


