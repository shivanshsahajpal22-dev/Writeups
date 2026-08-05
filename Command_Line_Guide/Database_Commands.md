## Database Commands 

**SQLite (`sqlite3`)**
```bash
sqlite3 database.db
```
```
.tables                 -- list tables
.schema                 -- full schema
.schema tablename       -- schema for one table
.headers on             -- show column headers
.mode column            -- pretty column output
.mode csv               -- csv output
.dump                   -- dump entire db as SQL
.quit
```
```sql
SELECT name FROM sqlite_master WHERE type='table';
SELECT sql FROM sqlite_master WHERE type='table' AND name='tablename';
PRAGMA table_info(tablename);
SELECT * FROM tablename LIMIT 10;
SELECT COUNT(*) FROM tablename;             -- always check this before trusting a manual dump
```

---

**MySQL**
```bash
mysql -u user -p
mysql -u user -p -h host -P port dbname
```
```sql
SHOW DATABASES;
USE dbname;
SHOW TABLES;
DESCRIBE tablename;
SELECT table_name FROM information_schema.tables WHERE table_schema=DATABASE();
SELECT column_name FROM information_schema.columns WHERE table_name='tablename';
SELECT * FROM tablename LIMIT 10;
SELECT @@version;
```

---

**PostgreSQL**
```bash
psql -U user -d dbname -h host -p port
```
```
\l                 -- list databases
\c dbname          -- connect to a database
\dt                -- list tables
\d tablename       -- describe a table
\du                -- list roles/users
```
```sql
SELECT table_name FROM information_schema.tables WHERE table_schema='public';
SELECT column_name FROM information_schema.columns WHERE table_name='tablename';
SELECT version();
```

---

**Microsoft SQL Server (`sqlcmd`)**
```bash
sqlcmd -S server -U user -P password
```
```sql
SELECT name FROM sys.databases;
USE dbname;
SELECT name FROM sys.tables;
SELECT column_name FROM information_schema.columns WHERE table_name='tablename';
SELECT @@version;
```

---

**MongoDB (NoSQL, bonus)**
```bash
mongosh "mongodb://host:port"
```
```js
show dbs
use dbname
show collections
db.collectionName.find().pretty()
db.collectionName.findOne()
```

---

**General SQL syntax**
```sql
SELECT col1, col2 FROM table WHERE condition;
SELECT * FROM table ORDER BY col DESC LIMIT 10;
SELECT * FROM table1 JOIN table2 ON table1.id = table2.id;
SELECT col, COUNT(*) FROM table GROUP BY col HAVING COUNT(*) > 1;
INSERT INTO table (col1, col2) VALUES (val1, val2);
UPDATE table SET col1 = val1 WHERE condition;
DELETE FROM table WHERE condition;
```
