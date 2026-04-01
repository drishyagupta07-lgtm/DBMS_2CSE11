#  Experiment_7

## 🔹 1. Number of days remaining in the current year

```sql id="q1a"}
SELECT 
DATEDIFF(
    MAKEDATE(YEAR(CURDATE()) + 1, 1),
    CURDATE()
) AS DAYS_REMAINING;
```

### Alternative approach

```sql id="q1b"}
SELECT DATEDIFF(
    CONCAT(YEAR(CURDATE()), '-12-31'),
    CURDATE()
) AS DAYS_REMAINING;
```

---

## 🔹 2. Highest salary, lowest salary, and their difference

```sql id="q2"}
SELECT 
MAX(SAL) AS HIGHEST_SALARY,
MIN(SAL) AS LOWEST_SALARY,
MAX(SAL) - MIN(SAL) AS DIFFERENCE
FROM EMPLOYEE;
```

---

## 🔹 3. Employees whose commission is more than 25% of salary

```sql id="q3"}
SELECT ENAME, SAL, COMM
FROM EMPLOYEE
WHERE IFNULL(COMM,0) > SAL * 0.25;
```

---

## 🔹 4. Display salary in dollar format

```sql id="q4a"}
SELECT ENAME,
CONCAT('$', FORMAT(SAL, 2)) AS SALARY_IN_DOLLAR
FROM EMPLOYEE;
```

### ➤ Convert INR to USD (assuming ₹83 = $1)

```sql id="q4b"}
SELECT 
ENAME,
CONCAT('$ ', FORMAT(SAL / 83, 2)) AS SALARY_IN_DOLLAR
FROM EMPLOYEE;
```

---

## 🔹 5. Matrix query (Salary by job and department)

```sql id="q5"}
SELECT 
JOB,
SUM(CASE WHEN DEPTNO = 10 THEN SAL ELSE 0 END) AS DEPT10,
SUM(CASE WHEN DEPTNO = 20 THEN SAL ELSE 0 END) AS DEPT20,
SUM(CASE WHEN DEPTNO = 30 THEN SAL ELSE 0 END) AS DEPT30,
SUM(CASE WHEN DEPTNO = 40 THEN SAL ELSE 0 END) AS DEPT40,
SUM(SAL) AS TOTAL_SALARY
FROM EMPLOYEE
GROUP BY JOB;
```

---

## 🔹 6. Total employees and count hired each year

```sql id="q6"}
SELECT
COUNT(*) AS TOTAL_EMPLOYEES,
SUM(YEAR(HIREDATE)=1980) AS HIRED_1980,
SUM(YEAR(HIREDATE)=1981) AS HIRED_1981,
SUM(YEAR(HIREDATE)=1982) AS HIRED_1982,
SUM(YEAR(HIREDATE)=1983) AS HIRED_1983
FROM EMPLOYEE;
```

---

## 🔹 7. Find last Sunday of a given month

```sql id="q7"}
SELECT 
DATE_SUB(
    LAST_DAY('2026-02-01'),
    INTERVAL (WEEKDAY(LAST_DAY('2026-02-01')) + 1) DAY
) AS LAST_SUNDAY;
```

---

## 🔹 8. Total employees in each department

```sql id="q8"}
SELECT DEPTNO, COUNT(*) AS TOTAL_EMPLOYEES
FROM EMPLOYEE
GROUP BY DEPTNO;
```

---

## 🔹 9. Total employees in each job role

```sql id="q9"}
SELECT JOB, COUNT(*) AS TOTAL_EMPLOYEES
FROM EMPLOYEE
GROUP BY JOB;
```

---

## 🔹 10. Total salary for each department

```sql id="q10"}
SELECT DEPTNO, SUM(SAL) AS TOTAL_SALARY
FROM EMPLOYEE
GROUP BY DEPTNO;
```

