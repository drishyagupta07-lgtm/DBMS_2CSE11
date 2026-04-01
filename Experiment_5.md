# Experiment_5


## 🔹 1. Total number of employees in the company

```sql id="q1"}
SELECT COUNT(*) AS TOTAL_EMPLOYEES
FROM EMPLOYEE;
```

---

## 🔹 2. Total salary paid to all employees

```sql id="q2"}
SELECT SUM(SAL) AS TOTAL_SALARY
FROM EMPLOYEE;
```

---

## 🔹 3. Maximum salary in the company

```sql id="q3"}
SELECT MAX(SAL) AS MAX_SALARY
FROM EMPLOYEE;
```

---

## 🔹 4. Minimum salary in the company

```sql id="q4"}
SELECT MIN(SAL) AS MIN_SALARY
FROM EMPLOYEE;
```

---

## 🔹 5. Average salary of employees

```sql id="q5"}
SELECT AVG(SAL) AS AVERAGE_SALARY
FROM EMPLOYEE;
```

---

## 🔹 6. Maximum salary of clerks

```sql id="q6"}
SELECT MAX(SAL) AS MAX_CLERK_SALARY
FROM EMPLOYEE
WHERE JOB = 'CLERK';
```

---

## 🔹 7. Maximum salary in department 20

```sql id="q7"}
SELECT MAX(SAL) AS MAX_SALARY_DEPT20
FROM EMPLOYEE
WHERE DEPTNO = 20;
```

---

## 🔹 8. Minimum salary of salesmen

```sql id="q8"}
SELECT MIN(SAL) AS MIN_SALESMAN_SALARY
FROM EMPLOYEE
WHERE JOB = 'SALESMAN';
```

---

## 🔹 9. Average salary of managers

```sql id="q9"}
SELECT AVG(SAL) AS AVG_MANAGER_SALARY
FROM EMPLOYEE
WHERE JOB = 'MANAGER';
```

---

## 🔹 10. Total salary of analysts in department 40

```sql id="q10"}
SELECT SUM(SAL) AS TOTAL_ANALYST_SALARY
FROM EMPLOYEE
WHERE JOB = 'ANALYST'
AND DEPTNO = 40;
```

---

## 🔹 11. Display employee names in uppercase

```sql id="q11"}
SELECT UPPER(ENAME) AS EMPLOYEE_NAME
FROM EMPLOYEE;
```

---

## 🔹 12. Display employee names in lowercase

```sql id="q12"}
SELECT LOWER(ENAME) AS EMPLOYEE_NAME
FROM EMPLOYEE;
```

---

## 🔹 13. Display employee names in proper case

```sql id="q13"}
SELECT CONCAT(
       UPPER(LEFT(ENAME,1)),
       LOWER(SUBSTRING(ENAME,2))
) AS EMPLOYEE_NAME
FROM EMPLOYEE;
```

---

## 🔹 14. Display the length of a name (example: SANDEEP)

```sql id="q14"}
SELECT LENGTH('SANDEEP') AS NAME_LENGTH;
```

---

## 🔹 15. Display the length of all employee names

```sql id="q15"}
SELECT ENAME, LENGTH(ENAME) AS NAME_LENGTH
FROM EMPLOYEE;
```