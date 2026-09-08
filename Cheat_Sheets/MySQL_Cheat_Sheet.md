# MySQL Cheat Sheet

## Connect to MySQL

```bash
mysql -h localhost -u root -p
```

---

# Create Database

```sql
CREATE DATABASE employeedb;
```

---

# Use Database

```sql
USE employeedb;
```

---

# Create Table

```sql
CREATE TABLE employee (
  id INT,
  FirstName VARCHAR(255),
  LastName VARCHAR(255)
);
```

---

# View Tables

```sql
SHOW TABLES;
```

---

# View Data

```sql
SELECT *
FROM employee;
```

---

# Insert Record

```sql
INSERT INTO employee
VALUES (
  1,
  'John',
  'Doe'
);
```

---

# Update Record

```sql
UPDATE employee
SET FirstName='Mary'
WHERE id=1;
```

---

# Delete Record

```sql
DELETE
FROM employee
WHERE id=1;
```

---

# Drop Table

```sql
DROP TABLE employee;
```

---

# SQL CRUD

Create

```sql
INSERT
```

Read

```sql
SELECT
```

Update

```sql
UPDATE
```

Delete

```sql
DELETE
```

---

# MySQL with Docker

Build:

```bash
docker build -t mysqlimg .
```

Run:

```bash
docker run \
--name mysqlserver \
-p 3306:3306 \
mysqlimg
```

---

# MySQL Binlogs

MySQL records:

```text
INSERT
UPDATE
DELETE
```

inside binary logs.

Debezium reads these logs.

---

# Module 14 Example

```sql
INSERT INTO employeedb.employee
VALUES (
    2,
    'Mary',
    'Doe',
    '4351234354',
    'mary@doe.com'
);
```

Debezium captured this event automatically.

---

# Key Terms

- Database
- Table
- Primary Key
- Binlog
- Schema
- Query
- CRUD

---

# Module 14 Takeaway

MySQL served as the source database for CDC operations using Debezium.