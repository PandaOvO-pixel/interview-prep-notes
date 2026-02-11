# MySQL Interview Questions & Answers

## 1. What is MySQL?

**Answer:** MySQL is an open-source relational database management system (RDBMS) based on SQL (Structured Query Language).

**Key Features:**
- **Open Source:** Free to use
- **Cross-Platform:** Windows, Linux, Mac
- **Reliable:** ACID compliant
- **Fast:** Optimized for read-heavy operations
- **Scalable:** Handle large databases
- **Secure:** Strong data security

**Why MySQL:**
- Most popular open-source database
- Large community support
- Easy to use
- Web application standard

---

## 2. What is the difference between MySQL and SQL?

**Answer:**

| Feature | SQL | MySQL |
|---------|-----|-------|
| Type | Language | Database system |
| Purpose | Query and manage databases | Store and manage data |
| Standard | ANSI standard | Implementation of SQL |
| Nature | Query language | RDBMS software |

**Analogy:** SQL is the language, MySQL is one of the systems that speaks it.

---

## 3. What are the different types of keys in MySQL?

**Answer:**

**Primary Key:**
- Uniquely identifies each record
- Cannot be NULL
- Only one per table

**Foreign Key:**
- Links two tables
- References primary key of another table
- Maintains referential integrity

**Unique Key:**
- Ensures unique values
- Can be NULL (only one NULL allowed)
- Multiple unique keys per table

**Composite Key:**
- Combination of columns as key
- Together identify unique record

**Candidate Key:**
- Can be chosen as primary key
- Minimal set of attributes

---

## 4. What is the difference between Primary Key and Unique Key?

**Answer:**

| Feature | Primary Key | Unique Key |
|---------|------------|------------|
| NULL values | Not allowed | One NULL allowed |
| Per table | Only one | Multiple allowed |
| Index | Clustered index | Non-clustered index |
| Purpose | Main identifier | Ensure uniqueness |

**Interview Tip:** Primary key = Unique + Not Null.

---

## 5. What are Joins in MySQL?

**Answer:** Joins combine rows from two or more tables based on related column.

**Types:**

**INNER JOIN:**
- Returns matching records from both tables
- Most common

**LEFT JOIN (LEFT OUTER JOIN):**
- All records from left table
- Matching records from right table
- NULL for non-matching right records

**RIGHT JOIN (RIGHT OUTER JOIN):**
- All records from right table
- Matching records from left table
- NULL for non-matching left records

**FULL JOIN (FULL OUTER JOIN):**
- All records from both tables
- NULL where no match

**CROSS JOIN:**
- Cartesian product of both tables
- Every row from first with every row from second

**SELF JOIN:**
- Table joined with itself

---

## 6. What is Normalization?

**Answer:** Normalization is organizing database to reduce redundancy and dependency.

**Normal Forms:**

**1NF (First Normal Form):**
- Atomic values (no repeating groups)
- Each column contains single value

**2NF (Second Normal Form):**
- Must be in 1NF
- No partial dependency
- All non-key attributes depend on entire primary key

**3NF (Third Normal Form):**
- Must be in 2NF
- No transitive dependency
- Non-key attributes depend only on primary key

**BCNF (Boyce-Codd Normal Form):**
- Stricter version of 3NF
- Every determinant is a candidate key

**Benefits:**
- Reduce data redundancy
- Improve data integrity
- Space optimization
- Easier maintenance

---

## 7. What is Denormalization?

**Answer:** Denormalization is intentionally adding redundancy to improve read performance.

**When to use:**
- Read-heavy applications
- Complex joins slow down queries
- Reporting and analytics
- Data warehousing

**Trade-off:**
- Faster reads
- Slower writes
- More storage
- Risk of inconsistency

---

## 8. What is the difference between DELETE, DROP, and TRUNCATE?

**Answer:**

| Feature | DELETE | TRUNCATE | DROP |
|---------|--------|----------|------|
| Type | DML | DDL | DDL |
| Removes | Rows (selective) | All rows | Table structure |
| WHERE clause | Yes | No | No |
| Rollback | Yes (with transaction) | No | No |
| Speed | Slower | Faster | Fastest |
| Auto-increment | Not reset | Reset | N/A |
| Triggers | Fires | Doesn't fire | N/A |

**Interview Tip:** DELETE removes data, TRUNCATE empties table, DROP removes table entirely.

---

## 9. What are Indexes and why use them?

**Answer:** Indexes are data structures that improve speed of data retrieval operations.

**Types:**

**Primary Index:** Automatically created on primary key
**Unique Index:** Ensures unique values
**Composite Index:** Multiple columns
**Full-Text Index:** Text searching
**Clustered Index:** Physical order of data
**Non-Clustered Index:** Logical order (pointer to data)

**Benefits:**
- Faster queries
- Quick sorting
- Efficient joins

**Drawbacks:**
- Slower INSERT/UPDATE/DELETE
- Extra storage space

**Interview Tip:** Don't over-index. Index columns used in WHERE, JOIN, ORDER BY clauses.

---

## 10. What is the difference between Clustered and Non-Clustered Index?

**Answer:**

| Feature | Clustered Index | Non-Clustered Index |
|---------|----------------|-------------------|
| Storage | Actual data | Separate structure with pointers |
| Per table | Only one | Multiple allowed |
| Speed | Faster | Slightly slower |
| Key | Primary key (default) | Any column |
| Space | Less | More (separate storage) |

**Interview Tip:** Clustered index determines physical storage order.

---

## 11. What are ACID properties?

**Answer:** ACID ensures reliable database transactions.

**Atomicity:**
- All or nothing
- Transaction fully completes or fully fails
- No partial transactions

**Consistency:**
- Data remains valid
- Constraints maintained
- Database moves from one valid state to another

**Isolation:**
- Concurrent transactions don't interfere
- Each transaction isolated from others

**Durability:**
- Committed changes are permanent
- Survive system failures

**Interview Tip:** ACID properties guarantee reliable transaction processing.

---

## 12. What are Database Transactions?

**Answer:** Transaction is a sequence of operations performed as a single logical unit of work.

**Commands:**

**BEGIN/START TRANSACTION:** Start transaction
**COMMIT:** Save changes permanently
**ROLLBACK:** Undo changes

**Properties:** Must follow ACID

**Use Cases:**
- Banking transactions
- E-commerce orders
- Multi-step operations
- Ensure data consistency

---

## 13. What is the difference between CHAR and VARCHAR?

**Answer:**

| Feature | CHAR | VARCHAR |
|---------|------|---------|
| Type | Fixed length | Variable length |
| Storage | Fixed (padded with spaces) | Actual length + 1-2 bytes |
| Performance | Faster | Slightly slower |
| Use Case | Fixed-size data (codes) | Variable-size data (names) |
| Max Length | 255 characters | 65,535 characters |

**Example:**
- CHAR(10): Always 10 bytes even if storing "Hi"
- VARCHAR(10): Uses 2 bytes for "Hi"

---

## 14. What are Constraints in MySQL?

**Answer:** Constraints enforce rules on data in tables.

**Types:**

**NOT NULL:** Column cannot be NULL
**UNIQUE:** All values must be unique
**PRIMARY KEY:** Unique identifier (NOT NULL + UNIQUE)
**FOREIGN KEY:** Link between tables
**CHECK:** Validates condition (MySQL 8.0.16+)
**DEFAULT:** Default value if not specified

**Benefits:**
- Data integrity
- Prevent invalid data
- Enforce business rules

---

## 15. What is a View?

**Answer:** View is a virtual table based on result of SQL query.

**Characteristics:**
- Doesn't store data (stores query)
- Updated automatically when base table changes
- Can be queried like regular table

**Benefits:**
- Simplify complex queries
- Security (hide sensitive columns)
- Data abstraction
- Consistent interface

**Syntax:** `CREATE VIEW  view_name AS SELECT ...`

**Interview Tip:** Views don't take up much space as they only store the query definition, not data.

---

## 16. What is the difference between View and Table?

**Answer:**

| Feature | Table | View |
|---------|-------|------|
| Storage | Physical data | Virtual (query) |
| Space | Uses storage | Minimal storage |
| Update | Direct | Through base tables |
| Speed | Faster | Depends on query |
| Indexed | Can be indexed | Cannot be indexed directly |

---

## 17. What are Stored Procedures?

**Answer:** Stored Procedures are prepared SQL code saved and reused.

**Benefits:**
- **Performance:** Precompiled, faster
- **Reusability:** Write once, use many times
- **Security:** Grant permissions without table access
- **Maintainability:** Centralized business logic
- **Network:** Less traffic (send procedure name, not entire query)

**Parameters:**
- IN: Input parameters
- OUT: Output parameters
- INOUT: Both

**Syntax:** `CREATE PROCEDURE procedure_name() BEGIN ... END`

---

## 18. What is the difference between Stored Procedure and Function?

**Answer:**

| Feature | Stored Procedure | Function |
|---------|-----------------|----------|
| Return | Can return 0 or more values | Must return one value |
| Call | CALL statement | SELECT statement |
| Transaction | Can manage | Cannot manage |
| Use in SELECT | No | Yes |
| Output | OUT parameters | RETURN statement |

**Interview Tip:** Use procedures for operations, functions for calculations/computations.

---

## 19. What are Triggers?

**Answer:** Triggers are automatic database actions executed in response to specific events.

**Events:**
- BEFORE INSERT
- AFTER INSERT
- BEFORE UPDATE
- AFTER UPDATE
- BEFORE DELETE
- AFTER DELETE

**Use Cases:**
- Audit trails
- Enforce business rules
- Data validation
- Maintain derived data
- Log changes

**Caution:** Can impact performance if complex or nested.

---

## 20. What is the difference between WHERE and HAVING?

**Answer:**

| Feature | WHERE | HAVING |
|---------|-------|--------|
| Use with | Rows | Groups |
| Applied | Before grouping | After grouping |
| Can use aggregate | No | Yes |
| Use with | SELECT, UPDATE, DELETE | GROUP BY |

**Example:**
- WHERE: Filter individual rows before grouping
- HAVING: Filter groups after aggregation

---

## 21. What are Aggregate Functions?

**Answer:** Aggregate functions perform calculations on multiple rows and return single value.

**Common Functions:**

**COUNT():** Count rows
**SUM():** Total sum
**AVG():** Average value
**MIN():** Minimum value
**MAX():** Maximum value
**GROUP_CONCAT():** Concatenate values

**Use with:** GROUP BY clause

**Interview Tip:** Aggregate functions ignore NULL values (except COUNT(*)).

---

## 22. What is GROUP BY clause?

**Answer:** GROUP BY groups rows with same values into summary rows.

**Purpose:**
- Aggregate data
- Create subtotals
- Data analysis

**Commonly used with:**
- Aggregate functions (COUNT, SUM, AVG)
- HAVING clause

**Rule:** Columns in SELECT must be in GROUP BY or aggregate functions.

---

## 23. What is the difference between UNION and UNION ALL?

**Answer:**

| Feature | UNION | UNION ALL |
|---------|-------|-----------|
| Duplicates | Removes | Keeps all |
| Performance | Slower (sorting/deduplication) | Faster |
| Result | Distinct rows | All rows |

**Requirements:**
- Same number of columns
- Compatible data types
- Same column order

**Interview Tip:** Use UNION ALL when you know there are no duplicates for better performance.

---

## 24. What is Subquery?

**Answer:** Subquery (inner query) is a query nested inside another query.

**Types:**

**Single Row:** Returns one row
**Multiple Row:** Returns multiple rows
**Correlated:** Depends on outer query

**Use Cases:**
- Complex filtering
- Calculations
- Existence checks (EXISTS)
- Comparison operations

**Alternative:** Often can be replaced with JOIN for better performance.

---

## 25. What is the difference between IN and EXISTS?

**Answer:**

**IN:**
- Compares value with list of values
- Evaluates subquery first
- Better for small datasets

**EXISTS:**
- Checks if subquery returns any rows
- Stops at first match
- Better for large datasets
- Generally faster

**Performance:** EXISTS usually more efficient for correlated subqueries.

---

## 26. What are Data Types in MySQL?

**Answer:**

**Numeric:**
- INT, TINYINT, SMALLINT, BIGINT
- FLOAT, DOUBLE
- DECIMAL (exact precision)

**String:**
- CHAR, VARCHAR
- TEXT, TINYTEXT, MEDIUMTEXT, LONGTEXT
- BLOB (binary data)

**Date and Time:**
- DATE (YYYY-MM-DD)
- TIME (HH:MM:SS)
- DATETIME (date + time)
- TIMESTAMP (auto-update)
- YEAR

**Other:**
- ENUM (enumeration)
- SET (multiple values)
- JSON (JSON documents)
- BOOLEAN (TINYINT(1))

---

## 27. What is the difference between DATETIME and TIMESTAMP?

**Answer:**

| Feature | DATETIME | TIMESTAMP |
|---------|----------|-----------|
| Range | 1000-01-01 to 9999-12-31 | 1970-01-01 to 2038-01-19 |
| Storage | 8 bytes | 4 bytes |
| Time Zone | No conversion | Converts to UTC |
| Auto Update | No | Yes (default) |
| Use Case | Absolute time | Tracking changes |

**Interview Tip:** Use TIMESTAMP for created_at/updated_at fields.

---

## 28. What is Database Partitioning?

**Answer:** Partitioning divides large table into smaller, more manageable pieces while appearing as single table.

**Types:**

**Range Partitioning:** Based on value range
**List Partitioning:** Based on predefined list
**Hash Partitioning:** Hash function determines partition
**Key Partitioning:** MySQL chooses hash function

**Benefits:**
- Improved query performance
- Easier maintenance
- Better scalability
- Faster data loading

---

## 29. What is Sharding?

**Answer:** Sharding distributes data across multiple database servers (horizontal partitioning).

**How it works:**
- Data split by shard key
- Each shard on different server
- Application routes requests to correct shard

**Benefits:**
- Horizontal scalability
- Improved performance
- Fault isolation

**Challenges:**
- Complex queries
- Data distribution
- Rebalancing

**Interview Tip:** Sharding for massive scale, partitioning for single-server optimization.

---

## 30. What is the difference between MyISAM and InnoDB?

**Answer:**

| Feature | MyISAM | InnoDB |
|---------|--------|--------|
| Transactions | No | Yes (ACID) |
| Foreign Keys | No | Yes |
| Row-level Locking | No (table-level) | Yes |
| Crash Recovery | Poor | Good |
| Full-text Search | Yes | Yes (5.6+) |
| Performance | Read-heavy | Balanced |
| Use Case | Legacy, read-only | Modern, transactional |

**Current Standard:** InnoDB is default and recommended storage engine in modern MySQL.

---
## 31. What is database normalization?

**Answer:** Normalization is process of organizing data to reduce redundancy and improve data integrity.

**Normal Forms:**

**1NF (First Normal Form):**
- Atomic values (no repeating groups)
- Each column contains single value
- Unique rows

**2NF (Second Normal Form):**
- Must be in 1NF
- No partial dependencies
- All non-key attributes depend on entire primary key

**3NF (Third Normal Form):**
- Must be in 2NF
- No transitive dependencies
- Non-key attributes depend only on primary key

**BCNF (Boyce-Codd Normal Form):**
- Stricter version of 3NF

---

## 32. What is denormalization?

**Answer:** Denormalization is intentionally introducing redundancy to improve read performance.

**When to Use:**
- Read-heavy applications
- Complex joins slowing queries
- Data warehousing
- Reporting systems

**Tradeoffs:**
- Faster reads
- Slower writes
- More storage space
- Data consistency challenges

---

## 33. What are database constraints?

**Answer:** Constraints enforce rules on data in tables.

**Types:**
- **NOT NULL:** Column cannot have NULL
- **UNIQUE:** All values must be different
- **PRIMARY KEY:** NOT NULL + UNIQUE
- **FOREIGN KEY:** References primary key in another table
- **CHECK:** Values must satisfy condition
- **DEFAULT:** Default value if none provided

**Purpose:** Data integrity, validation, relationships

---

## 34. What is ACID in databases?

**Answer:** ACID are properties ensuring reliable database transactions.

**Atomicity:**
- All or nothing
- Transaction fully completes or fully rolls back

**Consistency:**
- Database remains in valid state
- Constraints maintained

**Isolation:**
- Concurrent transactions don't interfere
- Transactions appear sequential

**Durability:**
- Committed data persists
- Survives system failures

---

## 35. What is a view in MySQL?

**Answer:** View is virtual table based on result set of SQL query.

**Characteristics:**
- Not physically stored (except materialized views)
- Updated dynamically
- Can be queried like table
- Simplifies complex queries

**Benefits:**
- Security (hide columns)
- Simplify complex joins
- Consistency
- Abstraction layer

**Limitation:** Some views not updatable

---

## 36. What are stored procedures?

**Answer:** Stored procedures are prepared SQL code saved and reused.

**Benefits:**
- Reusability
- Performance (compiled once)
- Security (encapsulation)
- Reduced network traffic
- Centralized business logic

**Drawbacks:**
- Hard to debug
- Version control challenges
- Database-specific syntax

**Syntax:** Created with `CREATE PROCEDURE`, called with `CALL`

---

## 37. What is the difference between `DELETE`, `TRUNCATE`, and `DROP`?

**Answer:**

| DELETE | TRUNCATE | DROP |
|--------|----------|------|
| Removes rows | Removes all rows | Removes table |
| WHERE clause allowed | No WHERE clause | Entire structure |
| Can be rolled back | Cannot rollback (some DBs) | Cannot rollback |
| Slower | Faster | Fastest |
| Triggers fire | Triggers don't fire | N/A |
| DML command | DDL command | DDL command |

---

## 38. What are triggers?

**Answer:** Triggers are stored programs that automatically execute in response to events on table.

**Types:**
- **BEFORE:** Executes before event
- **AFTER:** Executes after event

**Events:** INSERT, UPDATE, DELETE

**Use Cases:**
- Audit logging
- Enforce business rules
- Maintain data integrity
- Automatic calculations

**Caution:** Overuse can impact performance and make debugging hard

---

## 39. What is the difference between CHAR and VARCHAR?

**Answer:**

| CHAR | VARCHAR |
|------|---------|
| Fixed length | Variable length |
| Pads with spaces | No padding |
| Faster | Slightly slower |
| More storage | Less storage (if varied) |
| Max 255 chars | Max 65,535 chars |
| Good for fixed-length | Good for variable-length |

**Example:** CHAR(10) always uses 10 bytes, VARCHAR(10) uses 1-10 bytes + length byte

---

## 40. What is database indexing?

**Answer:** Indexing creates data structure to speed up data retrieval operations.

**Types:**
- **Primary Index:** On primary key
- **Unique Index:** Unique values
- **Composite Index:** Multiple columns
- **Full-text Index:** Text searching
- **Clustered Index:** Determines physical order
- **Non-clustered Index:** Separate structure

**Tradeoffs:**
- Faster reads
- Slower writes
- Additional storage

---

## 41. What is a subquery?

**Answer:** Subquery is query nested inside another query.

**Types:**
- **Scalar:** Returns single value
- **Row:** Returns single row
- **Column:** Returns single column
- **Table:** Returns table

**Placement:**
- SELECT clause
- FROM clause
- WHERE clause
- HAVING clause

**Correlated vs Non-correlated:** Correlated refers to outer query, non-correlated is independent

---

## 42. What are aggregate functions?

**Answer:** Aggregate functions perform calculation on set of values and return single value.

**Common Functions:**
- `COUNT()`: Number of rows
- `SUM()`: Total of values
- `AVG()`: Average of values
- `MAX()`: Maximum value
- `MIN()`: Minimum value

**Used with:** GROUP BY clause

**Note:** NULL values typically ignored except in COUNT(*)

---

## 43. What is the difference between WHERE and HAVING?

**Answer:**

| WHERE | HAVING |
|-------|--------|
| Filters rows before grouping | Filters groups after grouping |
| Cannot use aggregate functions | Can use aggregate functions |
| Used with individual rows | Used with GROUP BY |
| Applied first | Applied after GROUP BY |

**Example:** WHERE filters employees, HAVING filters departments based on aggregate conditions

---

## 44. What is a composite key?

**Answer:** Composite key is combination of two or more columns that uniquely identifies row.

**Characteristics:**
- Multiple columns together form key
- No single column can be primary key
- All columns must be NOT NULL

**Use Cases:**
- Many-to-many relationship tables
- When no single column is unique
- Junction tables

**Example:** StudentID + CourseID in enrollment table

---

## 45. What is database replication?

**Answer:** Replication is copying and maintaining database objects in multiple databases.

**Types:**
- **Master-Slave:** One master, multiple slaves (read-only)
- **Master-Master:** Multiple masters (read-write)
- **Snapshot:** Periodic copy
- **Transactional:** Real-time sync

**Benefits:**
- High availability
- Load distribution
- Disaster recovery
- Geographic distribution

**Challenges:** Consistency, conflict resolution, lag

---