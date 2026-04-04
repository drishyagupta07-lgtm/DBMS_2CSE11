```sql
## Experiment No. 8

-- 1. Display all employees with their dept name
SELECT E.EMPNO, E.ENAME, D.DNAME
FROM EMPLOYEE E
JOIN DEPARTMENT D ON E.DEPTNO = D.DEPTNO;

SELECT E.ENAME, D.DNAME
FROM EMPLOYEE E, DEPARTMENT D
WHERE E.DEPTNO = D.DEPTNO;


-- 2. Employees whose manager is JONES
SELECT E.ENAME AS EMPLOYEE, M.ENAME AS MANAGER
FROM EMPLOYEE E
JOIN EMPLOYEE M ON E.MGR = M.EMPNO
WHERE M.ENAME = 'JONES';

SELECT A.ENAME AS EMPLOYEE_NAME, B.ENAME AS MANAGER_NAME
FROM EMPLOYEE A, EMPLOYEE B
WHERE A.MGR = B.EMPNO
AND B.ENAME = 'JONES';


-- 3. Employee details with manager and grade (department-wise)
SELECT e.ENAME, e.JOB, d.DNAME, m.ENAME AS MANAGER, s.GRADE
FROM EMPLOYEE e
JOIN DEPARTMENT d ON e.DEPTNO = d.DEPTNO
LEFT JOIN EMPLOYEE m ON e.MGR = m.EMPNO
JOIN SALGRADE s ON e.SAL BETWEEN s.LOSAL AND s.HISAL
ORDER BY d.DNAME;


-- 4. Employees except clerk, sorted by highest salary
SELECT e.ENAME, e.JOB, e.SAL, s.GRADE, d.DNAME
FROM EMPLOYEE e
JOIN DEPARTMENT d ON e.DEPTNO = d.DEPTNO
JOIN SALGRADE s ON e.SAL BETWEEN s.LOSAL AND s.HISAL
WHERE e.JOB <> 'CLERK'
ORDER BY e.SAL DESC;


-- 5. Employees with/without manager
SELECT e.ENAME, e.JOB, m.ENAME AS MANAGER
FROM EMPLOYEE e
LEFT JOIN EMPLOYEE m ON e.MGR = m.EMPNO;


-- 6. Employees earning >= 36000 annually OR not clerks
SELECT e.ENAME, e.JOB, (e.SAL * 12) AS ANNUAL_SAL,
       e.DEPTNO, d.DNAME, s.GRADE
FROM EMPLOYEE e
JOIN DEPARTMENT d ON e.DEPTNO = d.DEPTNO
JOIN SALGRADE s ON e.SAL BETWEEN s.LOSAL AND s.HISAL
WHERE (e.SAL * 12) >= 36000
   OR e.JOB <> 'CLERK';


-- 7. Employees earning exactly 30000 annually and not clerks
SELECT e.ENAME, e.JOB, (e.SAL * 12) AS ANNUAL_SAL,
       e.DEPTNO, d.DNAME, s.GRADE
FROM EMPLOYEE e
JOIN DEPARTMENT d ON e.DEPTNO = d.DEPTNO
JOIN SALGRADE s ON e.SAL BETWEEN s.LOSAL AND s.HISAL
WHERE (e.SAL * 12) = 30000
  AND e.JOB <> 'CLERK';


-- 8. Employees with manager info (including no manager)
SELECT e.EMPNO, e.ENAME,
       IFNULL(CAST(m.EMPNO AS CHAR), 'No Manager') AS MGR_NO,
       IFNULL(m.ENAME, 'No Manager') AS MGR_NAME
FROM EMPLOYEE e
LEFT JOIN EMPLOYEE m ON e.MGR = m.EMPNO;


-- 9. Department-wise total salary
SELECT d.DEPTNO, d.DNAME, SUM(e.SAL) AS TOTAL_SAL
FROM EMPLOYEE e
JOIN DEPARTMENT d ON e.DEPTNO = d.DEPTNO
GROUP BY d.DEPTNO, d.DNAME;


-- 10. Employee number, name and department location
-- Replace LOCATION with your actual column name if different
SELECT e.EMPNO, e.ENAME, d.LOCATION
FROM EMPLOYEE e
JOIN DEPARTMENT d ON e.DEPTNO = d.DEPTNO;


-- 11. Employee name and department name
SELECT e.ENAME, d.DNAME
FROM EMPLOYEE e
JOIN DEPARTMENT d ON e.DEPTNO = d.DEPTNO;

---sql