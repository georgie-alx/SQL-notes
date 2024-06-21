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
WITH sub as  (select product_id,new_price  as price,change_date,
ROW_NUMBER() over (partition by product_id order by change_date desc)  rn
from Products where change_date<='2019-08-16' )
select product_id, price from sub where rn = 1
union
select distinct(product_id),10 as price from Products where product_id not in 
(select product_id from sub where rn = 1)
```



