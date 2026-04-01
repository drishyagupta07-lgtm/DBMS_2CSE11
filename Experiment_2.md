#  Experiment_2 


## 🔹 1. List all distinct jobs in Employee

```sql id="q1sql"}
SELECT DISTINCT JOB 
FROM EMPLOYEE;
```

---

## 🔹 2. List all information about employees in Department Number 30

```sql id="q2sql"}
SELECT * FROM EMPLOYEE
WHERE DEPTNO = 30;
```

---

## 🔹 3. Find all departments with department number greater than 20

```sql id="q3sql"}
SELECT * FROM DEPARTMENT
WHERE DEPTNO > 20;
```

---

## 🔹 4. Find all managers as well as clerks in department 30

```sql id="q4sql"}
SELECT * FROM EMPLOYEE
WHERE DEPTNO = 30
AND JOB IN ('MANAGER','CLERK');
```

---

## 🔹 5. List employee name, employee number, and department of all clerks

```sql id="q5sql"}
SELECT ENAME, EMPNO, DEPTNO
FROM EMPLOYEE
WHERE JOB = 'CLERK';
```

---

## 🔹 6. Find all managers not in department 30

```sql id="q6sql"}
SELECT * FROM EMPLOYEE
WHERE JOB = 'MANAGER'
AND DEPTNO <> 30;
```

---

## 🔹 7. List employees in department 10 who are not managers or clerks

```sql id="q7sql"}
SELECT * FROM EMPLOYEE
WHERE DEPTNO = 10
AND JOB NOT IN ('MANAGER','CLERK');
```

---

## 🔹 8. Find employees and jobs earning between 1200 and 1400

```sql id="q8sql"}
SELECT ENAME, JOB, SAL
FROM EMPLOYEE
WHERE SAL BETWEEN 1200 AND 1400;
```

---

## 🔹 9. List name and department number of employees who are clerks, analysts, or salesmen

```sql id="q9sql"}
SELECT ENAME, DEPTNO
FROM EMPLOYEE
WHERE JOB IN ('CLERK','ANALYST','SALESMAN');
```

---

## 🔹 10. List name and department number of employees whose names begin with 'M'

```sql id="q10sql"}
SELECT ENAME, DEPTNO
FROM EMPLOYEE
WHERE ENAME LIKE 'M%';
```

---

