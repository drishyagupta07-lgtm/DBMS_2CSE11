# Experiment_4

## 🔹 1. Employees who joined before 30 June 1980 or after 31 Dec 1981

```sql id="q1a"}
SELECT * 
FROM EMPLOYEE
WHERE HIREDATE < '1980-06-30'
   OR HIREDATE > '1981-12-31';
```

### Alternative using NOT BETWEEN

```sql id="q1b"}
SELECT *
FROM EMPLOYEE
WHERE HIREDATE NOT BETWEEN '1980-06-30' AND '1981-12-31';
```

---

## 🔹 2. Names of employees whose second letter is 'A'

```sql id="q2"}
SELECT ENAME
FROM EMPLOYEE
WHERE ENAME LIKE '_A%';
```

---

## 🔹 3. Names of employees with exactly five characters

```sql id="q3"}
SELECT ENAME
FROM EMPLOYEE
WHERE ENAME LIKE '_____';
```

---

## 🔹 4. (Duplicate) Names of employees whose second letter is 'A'

```sql id="q4"}
SELECT ENAME
FROM EMPLOYEE
WHERE ENAME LIKE '_A%';
```

---

## 🔹 5. Employees who are NOT salesman, clerk, or analyst

```sql id="q5"}
SELECT ENAME
FROM EMPLOYEE
WHERE JOB NOT IN ('SALESMAN', 'CLERK', 'ANALYST');
```

---

## 🔹 6. Employee name with annual salary (highest first)

```sql id="q6"}
SELECT ENAME, (SAL * 12) AS ANNUAL_SALARY
FROM EMPLOYEE
ORDER BY ANNUAL_SALARY DESC;
```

---

## 🔹 7. Display salary details (HRA, DA, PF, Total Salary)

```sql id="q7"}
SELECT 
    ENAME,
    SAL,
    SAL * 0.15 AS HRA,
    SAL * 0.10 AS DA,
    SAL * 0.05 AS PF,
    (SAL + (SAL * 0.15) + (SAL * 0.10) - (SAL * 0.05)) AS TOTALSAL
FROM EMPLOYEE
ORDER BY TOTALSAL, HRA, DA, PF;
```

---

## 🔹 8. Increase salary by 10% for employees with no commission

```sql id="q8"}
UPDATE EMPLOYEE
SET SAL = SAL + (SAL * 0.10)
WHERE COMM IS NULL;
```

---

## 🔹 9. Employees whose salary exceeds 3000 after 20% increment

```sql id="q9"}
SELECT ENAME, SAL, (SAL * 1.20) AS INCREMENTED_SAL
FROM EMPLOYEE
WHERE (SAL * 1.20) > 3000;
```

---

## 🔹 10. Employees whose salary has at least 3 digits

```sql id="q10"}
SELECT ENAME, SAL
FROM EMPLOYEE
WHERE SAL >= 100;
```

