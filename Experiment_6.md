# Experiment_6

## 🔹 1. Display EMPNO, ENAME with Department Name using CASE

```sql id="q1"}
SELECT 
    EMPNO,
    ENAME,
    CASE DEPTNO
        WHEN 10 THEN 'RESEARCH'
        WHEN 20 THEN 'ACCOUNTING'
        WHEN 30 THEN 'SALES'
        WHEN 40 THEN 'OPERATIONS'
    END AS DNAME
FROM EMPLOYEE;
```

---

## 🔹 2. Display your age in days

```sql id="q2"}
SELECT DATEDIFF(CURDATE(), '2000-01-01') AS AGE_IN_DAYS;
```

---

## 🔹 3. Display your age in months

```sql id="q3"}
SELECT TIMESTAMPDIFF(MONTH, '2000-01-01', CURDATE()) AS AGE_IN_MONTHS;
```

---

## 🔹 4. Display current date in formatted form

```sql id="q4"}
SELECT DATE_FORMAT(CURDATE(), '%D %M %W %Y') AS CURRENT_DATE;
```

---

## 🔹 5. Display formatted joining details of employee

```sql id="q5"}
SELECT 
CONCAT(
    ENAME,
    ' has joined the company on ',
    DATE_FORMAT(HIREDATE, '%W %D %M %Y')
) AS DETAILS
FROM EMPLOYEE
WHERE ENAME = 'SCOTT';
```

---

## 🔹 6. Find nearest Saturday after current date (correct logic)

```sql id="q6"}
SELECT DATE_ADD(
    CURDATE(),
    INTERVAL (6 - WEEKDAY(CURDATE()) + 7) % 7 DAY
) AS NEXT_SATURDAY;
```

---

## 🔹 7. Display current time

```sql id="q7"}
SELECT CURTIME() AS CURRENT_TIME;
```

---

## 🔹 8. Display date 3 months before current date

```sql id="q8"}
SELECT DATE_SUB(CURDATE(), INTERVAL 3 MONTH) AS DATE_BEFORE_3_MONTHS;
```

---

## 🔹 9. Employees who joined in December

```sql id="q9"}
SELECT ENAME, HIREDATE
FROM EMPLOYEE
WHERE MONTH(HIREDATE) = 12;
```

---

## 🔹 10. Employees whose last 2 digits of salary match last 2 digits of year

```sql id="q10"}
SELECT ENAME, HIREDATE, SAL
FROM EMPLOYEE
WHERE RIGHT(YEAR(HIREDATE),2) = RIGHT(SAL,2);
```

---

## 🔹 11. Employees whose 10% salary equals year of joining

```sql id="q11"}
SELECT ENAME, SAL, HIREDATE
FROM EMPLOYEE
WHERE (SAL * 0.10) = YEAR(HIREDATE);
```

---

## 🔹 12. Employees who joined before 15th of the month

```sql id="q12"}
SELECT ENAME, HIREDATE
FROM EMPLOYEE
WHERE DAY(HIREDATE) < 15;
```

---

## 🔹 13. Employees who joined after 15th of the month

```sql id="q13"}
SELECT ENAME, HIREDATE
FROM EMPLOYEE
WHERE DAY(HIREDATE) > 15;
```

---

## 🔹 14. Employees with valid joining date and department

```sql id="q14"}
SELECT ENAME, HIREDATE, DEPTNO
FROM EMPLOYEE
WHERE HIREDATE IS NOT NULL
AND DEPTNO IS NOT NULL;
```

---

## 🔹 15. Examples of DATE_ADD and DATE_SUB

### ➤ Add 7 days

```sql id="q15a"}
SELECT DATE_ADD('2025-01-01', INTERVAL 7 DAY);
```

### ➤ Subtract 3 hours

```sql id="q15b"}
SELECT DATE_SUB('2025-01-01 12:00:00', INTERVAL 3 HOUR);
```

