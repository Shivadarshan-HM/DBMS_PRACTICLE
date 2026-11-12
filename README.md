# Relational Database Management Systems (RDBMS) - Lab Practical File

A comprehensive repository containing database design, relational schemas, SQL scripts, performance benchmarks, and practical reports for **Experiments 1 to 10**.

---

## Repository & Experiments Overview

| No. | Experiment Name | Focus Area | Directory | Files |
| :---: | :--- | :--- | :--- | :--- |
| **01** | **Entity-Relationship (ER) Modeling** | Conceptual Database Design, Entities, Relationships, Cardinality | [`Experiment 1/`](./Experiment%201/) | `Experiment_1.pdf` |
| **02** | **Relational Schema & Integrity Constraints** | DDL, Primary/Foreign Keys, `ON DELETE CASCADE`, Referential Integrity | [`Experiment 2/`](./Experiment%202/) | `Experiment_2.sql`, `Experiment_2.pdf` |
| **03** | **Employee-Department-Project Operations** | DML, Aggregations, `GROUP BY`, `HAVING`, Summary Statistics | [`Experiment 3/`](./Experiment%203/) | `Experiment_3.sql`, `Experiment_3.pdf` |
| **04** | **Complex SQL Joins & Subqueries** | `INNER`, `LEFT`, `SELF`, `3-WAY JOIN`, Subqueries, `EXISTS`, Execution Analysis | [`Experiment 4/`](./Experiment%204/) | `Experiment_4.sql`, `Experiment_4.pdf` |
| **05** | **Views & Hierarchical Reporting (Recursive CTE)** | Updatable & Read-Only Views, WITH RECURSIVE, Manager-Employee Hierarchy | [`Experiment 5/`](./Experiment%205/) | `Experiment_5.sql`, `Experiment_5.pdf` |
| **06** | **Stored Procedures, Triggers & Auditing** | `CREATE PROCEDURE`, `BEFORE/AFTER` Triggers, Salary Validation, Audit Trails | [`Experiment 6/`](./Experiment%206/) | `Experiment_6.sql`, `Experiment_6.pdf` |
| **07** | **Functional Dependencies & Normalization** | UNF $\rightarrow$ 1NF $\rightarrow$ 2NF $\rightarrow$ 3NF $\rightarrow$ BCNF, Lossless Decomposition, Dependency Preservation | [`Experiment-07-Normalization/`](./Experiment-07-Normalization/) | `exp07_normalization.sql`, `output.txt` |
| **08** | **Transactions & Concurrency Control** | ACID, `COMMIT`, `ROLLBACK`, `SAVEPOINT`, Isolation Levels, Concurrency Anomalies | [`Experiment-08-Transactions-Concurrency/`](./Experiment-08-Transactions-Concurrency/) | `exp08_*.sql`, `output*.txt` |
| **09** | **Indexing & Query Performance Benchmarking** | B+ Tree Indexes, Single vs. Composite, Covering Index, Execution Plans (`EXPLAIN`) | [`Experiment-09-Indexing-Benchmark/`](./Experiment-09-Indexing-Benchmark/) | `exp09_railway_indexing.sql`, `output.txt` |
| **10** | **Query Optimization & Sargability** | Query Rewriting, Sargable Predicates, Eliminating Filesort/Scans, Keyset Pagination | [`Experiment-10-Query-Optimization/`](./Experiment-10-Query-Optimization/) | `exp10_query_optimization.sql`, `output.txt` |

---

## Detailed Experiment Summaries

### Experiment 1: Entity-Relationship (ER) Modeling
- **Aim**: Design a conceptual Entity-Relationship (ER) model for an e-commerce platform.
- **Concepts**: Entities (Customers, Orders, Products, Categories, Payment, Shipment), attributes, composite/multi-valued attributes, primary/candidate keys, cardinality ratios (1:1, 1:N, M:N), and participation constraints.
- **Artifacts**: Complete conceptual ER diagrams and documentation in [`Experiment 1/Experiment_1.pdf`](./Experiment%201/Experiment_1.pdf).

---

### Experiment 2: Relational Schema & Integrity Constraints
- **Aim**: Convert the conceptual ER diagram into a physical relational database schema in MySQL and demonstrate referential integrity enforcement.
- **Database**: `ECOMMERCE`
- **Tables**: `CUSTOMER`, `CUSTOMER_PHONE`, `CATEGORY`, `PRODUCT`, `ORDERS`, `ORDER_ITEM`, `PAYMENT`, `SHIPMENT`.
- **Key Concepts**:
  - Primary Key, Foreign Key constraints, and Unique constraints.
  - Cascade actions: `ON DELETE CASCADE` and `ON UPDATE CASCADE`.
  - Testing referential integrity violations: attempting orphan inserts and child record cascades upon parent row deletion.
- **Files**: [`Experiment_2.sql`](./Experiment%202/Experiment_2.sql), [`Experiment_2.pdf`](./Experiment%202/Experiment_2.pdf).

---

### Experiment 3: Employee-Department-Project Schema & Aggregations
- **Aim**: Create a departmental database system and execute analytical queries utilizing aggregate functions, grouping, and filtering conditions.
- **Database**: `EmployeeDB`
- **Tables**: `Department`, `Employee`, `Project`, `WorksOn`.
- **Key Concepts**:
  - Multi-table schema design with realistic organizational data.
  - Aggregate functions: `COUNT()`, `SUM()`, `AVG()`, `MIN()`, `MAX()`.
  - Partitioning with `GROUP BY` and post-aggregation filtering via `HAVING`.
  - Departmental salary distribution, headcounts, and project allocation metrics.
- **Files**: [`Experiment_3.sql`](./Experiment%203/Experiment_3.sql), [`Experiment_3.pdf`](./Experiment%203/Experiment_3.pdf).

---

### Experiment 4: SQL Joins, Subqueries & Correlated Subqueries
- **Aim**: Query data across multiple related relations using different join variations and nested/correlated subqueries.
- **Key Concepts**:
  - `INNER JOIN`: Matching records between Employees and Departments.
  - `LEFT OUTER JOIN`: Preserving unmatched department records.
  - `SELF JOIN`: Evaluating employee hierarchies and peer-to-peer relationships.
  - `3-WAY JOIN`: Linking `Employee`, `WorksOn`, and `Project` records.
  - Nested subqueries and correlated subqueries with `EXISTS` / `NOT EXISTS`.
- **Files**: [`Experiment_4.sql`](./Experiment%204/Experiment_4.sql), [`Experiment_4.pdf`](./Experiment%204/Experiment_4.pdf).

---

### Experiment 5: SQL Views, Updatability & Recursive CTEs
- **Aim**: Implement logical views for security/abstraction, verify updatability rules, and model organizational hierarchies using Recursive Common Table Expressions (CTEs).
- **Key Concepts**:
  - Creating views (`CREATE VIEW`) to encapsulate business logic and restrict direct column access.
  - Testing view updatability rules: when a view can and cannot accept `INSERT`/`UPDATE` operations.
  - Hierarchical employee-manager reporting chains using `WITH RECURSIVE` CTEs.
- **Files**: [`Experiment_5.sql`](./Experiment%205/Experiment_5.sql), [`Experiment_5.pdf`](./Experiment%205/Experiment_5.pdf).

---

### Experiment 6: Stored Procedures, Triggers & Audit Logging
- **Aim**: Implement modular database procedural logic and automated event-driven triggers with audit tables.
- **Key Concepts**:
  - **Stored Procedure** (`transfer_employee`): Encapsulates employee department transfers within an atomic operation.
  - **Triggers**:
    - `BEFORE INSERT`/`BEFORE UPDATE`: Enforce domain rules (e.g., minimum salary checks, negative value validation).
    - `AFTER UPDATE`/`AFTER DELETE`: Maintain an automated `AuditLog` table capturing timestamp, user, old values, and new values.
- **Files**: [`Experiment_6.sql`](./Experiment%206/Experiment_6.sql), [`Experiment_6.pdf`](./Experiment%206/Experiment_6.pdf).

---

### Experiment 7: Functional Dependencies & Normalization (UNF to BCNF)
- **Aim**: Normalize an unnormalized sales dataset (`sales_unf`) containing multi-valued attributes and redundancy into 1NF, 2NF, 3NF, and BCNF, while verifying lossless-join and dependency-preservation properties.
- **Database**: `sales_norm_db`
- **Normalization Progression**:
  - **UNF**: Flat multi-valued and comma-separated records.
  - **1NF**: Atomic cell values; composite primary key `(invoice_no, product_id)`.
  - **2NF**: Elimination of partial functional dependencies (attributes depending on a subset of the candidate key). Decomposed into `Invoices`, `Products`, and `Invoice_Items`.
  - **3NF**: Elimination of transitive dependencies (non-prime attribute determining another non-prime attribute). Decomposed customer details into a dedicated `Customers` table.
  - **BCNF**: Ensuring every determinant is a superkey.
  - **Verification**: SQL validation using `EXCEPT` and natural joins to prove lossless-join decomposition and absence of spurious tuples.
- **Files**: [`exp07_normalization.sql`](./Experiment-07-Normalization/exp07_normalization.sql), [`output.txt`](./Experiment-07-Normalization/output.txt).

---

### Experiment 8: Transactions, Savepoints & Concurrency Control
- **Aim**: Demonstrate ACID properties in banking workflows using `COMMIT`, `ROLLBACK`, and `SAVEPOINT`, and evaluate transaction isolation levels and concurrency anomalies across concurrent client sessions.
- **Database**: `bank_db`
- **Part 1 - Transaction Controls**:
  - Atomic money transfers between accounts.
  - Handling partial failures using named `SAVEPOINT`s and conditional rollbacks.
- **Part 2 - Isolation Levels & Concurrency Anomalies (Two-Session Simulation)**:
  - **READ UNCOMMITTED**: Demonstration of *Dirty Reads*.
  - **READ COMMITTED**: Demonstration and resolution of *Dirty Reads*; manifestation of *Non-Repeatable Reads*.
  - **REPEATABLE READ**: Demonstration of snapshot isolation; evaluation of *Phantom Reads*.
  - **SERIALIZABLE**: Strict two-phase locking preventing concurrent phantom inserts.
  - **Deadlock Simulation**: Cross-locking resource dependency resolution via InnoDB deadlock detection and rollback.
- **Files**:
  - Setup: [`exp08_concurrency_setup.sql`](./Experiment-08-Transactions-Concurrency/exp08_concurrency_setup.sql)
  - Single-session operations: [`exp08_transactions.sql`](./Experiment-08-Transactions-Concurrency/exp08_transactions.sql)
  - Concurrent sessions: [`exp08_session_A.sql`](./Experiment-08-Transactions-Concurrency/exp08_session_A.sql), [`exp08_session_B.sql`](./Experiment-08-Transactions-Concurrency/exp08_session_B.sql)
  - Execution logs: [`output.txt`](./Experiment-08-Transactions-Concurrency/output.txt), [`output_session_A.txt`](./Experiment-08-Transactions-Concurrency/output_session_A.txt), [`output_session_B.txt`](./Experiment-08-Transactions-Concurrency/output_session_B.txt).

---

### Experiment 9: Indexing & Railway Booking Performance Benchmark
- **Aim**: Create a realistic 50,000+ row Railway Booking system dataset (`railway_db`) and benchmark query performance before and after applying B+ Tree indexes.
- **Key Concepts**:
  - **Clustered vs. Secondary Indexes**: Primary key clustering vs. secondary non-clustered index traversals.
  - **Single-Column vs. Composite Indexes**: Performance tradeoffs and index size.
  - **Leftmost-Prefix Rule**: How composite indexes `(train_no, journey_date)` serve specific query shapes.
  - **Covering Index**: Eliminating clustered index lookups (`Extra: Using index`).
  - **Execution Plan Analysis**: Measuring cost, row examinations, and latency before and after indexing via `EXPLAIN / EXPLAIN ANALYZE`.
- **Files**: [`exp09_railway_indexing.sql`](./Experiment-09-Indexing-Benchmark/exp09_railway_indexing.sql), [`output.txt`](./Experiment-09-Indexing-Benchmark/output.txt).

---

### Experiment 10: Query Optimization, Sargability & Execution Plans
- **Aim**: Generate a 120,000+ row retail order dataset (`shop_db`), identify 5 classic anti-pattern slow queries, and optimize them using query rewriting, sargable predicates, and index restructuring.
- **Optimized Anti-Patterns**:
  1. **Non-sargable Functions on Indexed Columns**: `WHERE YEAR(order_date) = 2024` rewritten as a range scan `WHERE order_date >= '2024-01-01' AND order_date < '2025-01-01'`.
  2. **Implicit Type Conversion**: String phone numbers compared against numeric literals causing full table scans; resolved with matching types.
  3. **Unindexed Correlated Subqueries**: Transformed into efficient `JOIN ... GROUP BY ... HAVING` structures.
  4. **Large OFFSET Pagination Overhead**: Replaced high-offset scanning with **Keyset (seek) pagination** (`WHERE (order_date, order_id) < (:last_date, :last_id)`).
  5. **Filesort with Unindexed Sort & Filter**: Resolved using targeted composite indexes aligning filtering and sorting orders.
- **Files**: [`exp10_query_optimization.sql`](./Experiment-10-Query-Optimization/exp10_query_optimization.sql), [`output.txt`](./Experiment-10-Query-Optimization/output.txt).

---

## Environment & Execution Guide

### Software Prerequisites
- **DBMS**: MySQL Server 8.0+ (InnoDB Storage Engine)
- **Client**: MySQL Command Line Client or VS Code Database Client extension

### Executing Scripts
To execute any experiment's SQL script and generate tabular output:

```bash
# General syntax
mysql -u <username> -p -t -vvv --force < <path-to-script.sql>

# Example: Run Experiment 7 Normalization
cd "Experiment-07-Normalization"
mysql -u root -p -t -vvv --force < exp07_normalization.sql > output.txt

# Example: Run Experiment 9 Indexing Benchmark
cd "../Experiment-09-Indexing-Benchmark"
mysql -u root -p -t -vvv --force < exp09_railway_indexing.sql > output.txt
```

### Running Concurrency Tests (Experiment 8)
Experiment 8 (Part 2) tests isolation levels between concurrent sessions:
1. Open two separate terminal windows (**Session A** and **Session B**).
2. Run `exp08_concurrency_setup.sql` once in either session to initialize the tables.
3. Step through `exp08_session_A.sql` in Terminal A and `exp08_session_B.sql` in Terminal B according to the prompt instructions.
