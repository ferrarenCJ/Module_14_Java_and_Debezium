# Coding Activity 14.4: Connecting MySQL to Debezium

## Activity Information

### Module

Module 14: Java and Debezium

### Activity

Required Coding Activity 14.4: Connecting MySQL to Debezium

### Learning Outcome

- Connect a database to Debezium.

---

# Objective

Learn how to connect a MySQL database container to a Debezium application and use Change Data Capture (CDC) to automatically detect database changes.

---

# Why This Activity Matters

Traditional CDC approaches often rely on scheduled queries.

Example:

```text
Query Database
      ↓
Check for Changes
      ↓
Process Changes
```

This approach increases:

- Database load
- Resource consumption
- Processing latency

Debezium uses an event-driven architecture:

```text
Database Change
      ↓
Debezium Detects Event
      ↓
CDC Event Generated
      ↓
Consumer Receives Event
```

This provides near real-time processing.

---

# Step 1: Verify MySQL Container

Verified:

```text
mysqlserver
```

container was running inside Docker Desktop.

Purpose:

- Ensure a database source exists.
- Allow Debezium to connect.
- Provide access to the customer database.

---

# Step 2: Verify Docker Network

Command:

```bash
docker network ls
```

Verified:

```text
myCDCNetwork
```

exists.

Purpose:

- Enables communication between containers.
- Allows Debezium to connect to MySQL.

---

# Step 3: Extract Debezium Project

Downloaded:

```text
debeziumActivity14_4.zip
```

Extracted to:

```text
debeziumActivity14_4
```

Contents included:

```text
Dockerfile
README.md
pom.xml
src
```

Purpose:

- Provides the Debezium Spring Boot application.
- Contains CDC configuration.

---

# Step 4: Build Debezium Image

Command:

```bash
docker build -t debeziumactivity14_4 .
```

Purpose:

- Create a custom Docker image.
- Package the application and dependencies.

Result:

```text
debeziumactivity14_4
```

image successfully created.

---

# Step 5: Create Debezium Container

Command:

```bash
docker run -it --rm \
--name debeziumserver \
--network myCDCNetwork \
debeziumactivity14_4 bash
```

Purpose:

- Start the Debezium environment.
- Connect to the Docker network.
- Enable communication with MySQL.

---

# Step 6: Verify Containers

Verified both containers running:

```text
mysqlserver
debeziumserver
```

Purpose:

```text
MySQL
↕
Debezium
```

communication path established.

---

# Step 7: Start Debezium

Command:

```bash
mvn spring-boot:run
```

Application startup displayed:

```text
Started TvApplication
```

Debezium connected to:

```text
database.hostname = mysqlserver
database.dbname = customerdb
```

Verified snapshot processing:

```text
customerdb.customer
```

table detected.

---

# Initial CDC Event

Debezium identified the existing record:

```text
id = 1
fullname = John Doe
email = jd@example.com
```

Output:

```text
Key = Struct{id=1}
```

Purpose:

- Confirm Debezium is reading data.
- Validate CDC configuration.

---

# MySQL Workbench Connection

Connected using:

```text
Hostname: 127.0.0.1
Port: 3306
Username: root
Password: MyNewPass
```

Database:

```text
customerdb
```

Table:

```text
customer
```

---

# Step 8: Insert New Record

Query executed:

```sql
INSERT INTO customerdb.customer
VALUES (
    2,
    'Peter Parker',
    'pp@example.com'
);
```

Result:

```text
1 row(s) affected
```

Purpose:

- Generate a CDC event.
- Test Debezium monitoring.

---

# Step 9: Verify CDC Event

Debezium automatically detected:

```text
id = 2
fullname = Peter Parker
email = pp@example.com
```

Output