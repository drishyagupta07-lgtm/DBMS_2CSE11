#  Experiment No. 11

---

### 1. Delete employees who joined before 31-Dec-82 and whose department location is NEW YORK or CHICAGO

```sql
DELETE FROM EMPLOYEE
WHERE HIREDATE < '1982-12-31'
AND DEPTNO IN (
    SELECT DEPTNO
    FROM DEPARTMENT
    WHERE LOC IN ('NEW YORK', 'CHICAGO')
);
```

---

### 2. Display employee name, job, department name, and location for managers

```sql id="3e6n8m"
SELECT 
    E.ENAME,
    E.JOB,
    D.DNAME,
    D.LOC
FROM EMPLOYEE E
JOIN DEPARTMENT D 
ON E.DEPTNO = D.DEPTNO
WHERE E.JOB = 'MANAGER';
```

---

### 3. Display name and salary of FORD if his salary equals highest salary in his grade

```sql id="v5xg2j"
SELECT E.ENAME, E.SAL
FROM EMPLOYEE E
JOIN SALGRADE S 
ON E.SAL BETWEEN S.LOSAL AND S.HISAL
WHERE E.ENAME = 'FORD'
AND E.SAL = (
    SELECT MAX(E2.SAL)
    FROM EMPLOYEE E2
    JOIN SALGRADE S2 
    ON E2.SAL BETWEEN S2.LOSAL AND S2.HISAL
    WHERE S2.GRADE = S.GRADE
);
```

---

### 4. Find top 5 earners of the company

```sql id="m5g2d0"
SELECT ENAME, SAL
FROM EMPLOYEE
ORDER BY SAL DESC
LIMIT 5;
```

---

### 5. Display employees who are getting highest salary

```sql id="6g6u2q"
SELECT ENAME
FROM EMPLOYEE
WHERE SAL = (SELECT MAX(SAL) FROM EMPLOYEE);
```

---

### 6. Display employees whose salary equals average of maximum and minimum salary

```sql id="a3w6tf"
SELECT ENAME, SAL
FROM EMPLOYEE
WHERE SAL = (
    (SELECT MAX(SAL) FROM EMPLOYEE) +
    (SELECT MIN(SAL) FROM EMPLOYEE)
) / 2;
```

---

### 7. Display department names where at least 3 employees are working

```sql id="p4dn5o"
SELECT D.DNAME
FROM DEPARTMENT D
JOIN EMPLOYEE E ON D.DEPTNO = E.DEPTNO
GROUP BY D.DNAME
HAVING COUNT(*) >= 3;
```

---

### 8. Display manager names whose salary is more than company average salary

```sql id="1u0j6g"
SELECT ENAME
FROM EMPLOYEE
WHERE JOB = 'MANAGER'
AND SAL > (SELECT AVG(SAL) FROM EMPLOYEE);
```

---

### 9. Display manager names whose salary is more than average salary of their employees

```sql id="e9p2sz"
SELECT M.ENAME
FROM EMPLOYEE M
WHERE M.JOB = 'MANAGER'
AND M.SAL > (
    SELECT AVG(E.SAL)
    FROM EMPLOYEE E
    WHERE E.MGR = M.EMPNO
);
```

---

### 10. Display employee name, salary, commission and net pay where net pay is greater than or equal to any employee salary

```sql id="w3t2m1"
SELECT ENAME, SAL, COMM,
       (SAL + IFNULL(COMM, 0)) AS NET_PAY
FROM EMPLOYEE
WHERE (SAL + IFNULL(COMM, 0)) >= ANY (
    SELECT SAL FROM EMPLOYEE
);
```

---
