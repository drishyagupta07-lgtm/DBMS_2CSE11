#  Experiment No. 12

---

### 1. Display employees whose salary is less than their manager but more than salary of any manager

```sql
SELECT E.ENAME
FROM EMPLOYEE E
JOIN EMPLOYEE M ON E.MGR = M.EMPNO
WHERE E.SAL < M.SAL
AND E.SAL > ANY (
    SELECT SAL FROM EMPLOYEE WHERE JOB = 'MANAGER'
);
```

---

### 2. Find number of employees whose salary is greater than their manager salary

```sql id="q1a2ws"
SELECT COUNT(*) AS TOTAL
FROM EMPLOYEE E
JOIN EMPLOYEE M ON E.MGR = M.EMPNO
WHERE E.SAL > M.SAL;
```

---

### 3. Display managers not working under president but under another manager

```sql id="z8l9mx"
SELECT E.ENAME
FROM EMPLOYEE E
JOIN EMPLOYEE M ON E.MGR = M.EMPNO
WHERE E.JOB = 'MANAGER'
AND M.JOB <> 'PRESIDENT';
```

---

### 4. Delete departments where no employee is working

```sql id="t6p4nv"
DELETE FROM DEPARTMENT
WHERE DEPTNO NOT IN (
    SELECT DISTINCT DEPTNO FROM EMPLOYEE
);
```

---

### 5. Delete employees whose department number is not present in department table

```sql id="f0k2dl"
DELETE FROM EMPLOYEE
WHERE DEPTNO NOT IN (
    SELECT DEPTNO FROM DEPARTMENT
);
```

---

### 6. Display employees whose salary is outside all salary grades

```sql id="y4r7gh"
SELECT ENAME, SAL
FROM EMPLOYEE
WHERE SAL NOT BETWEEN 
    (SELECT MIN(LOSAL) FROM SALGRADE)
AND 
    (SELECT MAX(HISAL) FROM SALGRADE);
```

---

### 7. Display employee name, salary, commission, and net pay greater than any salary in company

```sql id="b3w9xe"
SELECT ENAME, SAL, COMM,
       (SAL + IFNULL(COMM,0)) AS NET_PAY
FROM EMPLOYEE
WHERE (SAL + IFNULL(COMM,0)) >= ANY (
    SELECT SAL FROM EMPLOYEE
);
```

---

### 8. Display employees working in SALES or RESEARCH department

```sql id="k7n3pz"
SELECT E.ENAME
FROM EMPLOYEE E
JOIN DEPARTMENT D ON E.DEPTNO = D.DEPTNO
WHERE D.DNAME IN ('SALES', 'RESEARCH');
```

---

### 9. Display the grade of JONES

```sql id="h5c2rt"
SELECT S.GRADE
FROM EMPLOYEE E
JOIN SALGRADE S 
ON E.SAL BETWEEN S.LOSAL AND S.HISAL
WHERE E.ENAME = 'JONES';
```

---

### 10. Display department names where number of characters equals number of employees in any department

```sql id="n2v8sx"
SELECT D.DNAME
FROM DEPARTMENT D
WHERE LENGTH(D.DNAME) IN (
    SELECT COUNT(*)
    FROM EMPLOYEE
    GROUP BY DEPTNO
);
```

---
