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




