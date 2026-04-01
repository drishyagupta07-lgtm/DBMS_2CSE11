# Experiment_1

## 🔹 1. Create `EMPLOYEE_MASTER` table using `EMPLOYEE`

```sql
CREATE TABLE EMPLOYEE_MASTER
AS
SELECT * FROM EMPLOYEE;
```

---

## 🔹 2. Delete records where `DEPTNO = 10`

```sql
DELETE FROM EMPLOYEE_MASTER
WHERE DEPTNO = 10;
```

---

## 🔹 3. Increase salary by 10% for employees in `DEPTNO = 20`

```sql
UPDATE EMPLOYEE_MASTER
SET SAL = SAL + (SAL * 0.10)
WHERE DEPTNO = 20;
```

---

## 🔹 4. Modify `SAL` column to `DECIMAL(10,2)`

```sql
ALTER TABLE EMPLOYEE_MASTER
MODIFY SAL DECIMAL(10,2);
```

---

## 🔹 5. Drop `EMPLOYEE_MASTER` table

```sql
DROP TABLE EMPLOYEE_MASTER;
```
