# SQL Technical Paper

## ACID Properties

ACID stands for **Atomicity, Consistency, Isolation, and Durability**—a set of four principles that ensure database transactions (a series of operations, like updating records) are reliable and error-free, even if something unexpected happens, like a system crash. These properties are especially important in relational databases like MySQL, PostgreSQL, or Oracle.

- **Atomicity**: This ensures a transaction is treated as a single, all-or-nothing unit. Either every operation in the transaction completes successfully, or none of them do. For example, when transferring $200 from your savings account to your checking account, atomicity ensures both the withdrawal and deposit happen together. If the system crashes halfway, the database "rolls back" to undo any partial changes, preventing an unbalanced state.
- **Consistency**: This guarantees that a transaction leaves the database in a valid state, following all rules, constraints, and data integrity requirements. For instance, if a database rule requires that an account balance can’t be negative, consistency ensures no transaction violates this. It acts like a gatekeeper, rejecting changes that break the database’s logic.
- **Isolation**: Isolation prevents transactions from interfering with each other. If two users try to update the same record simultaneously, isolation ensures one transaction finishes before the other starts, avoiding confusion. For example, if you’re booking a concert ticket while someone else books the same seat, isolation prevents both from getting it.
- **Durability**: Once a transaction is committed (saved), durability ensures the changes are permanently stored, even if the power goes out or the server crashes. This is often achieved by writing changes to a disk or using backup systems. For example, once you confirm an online payment, durability ensures it’s recorded forever.

## CAP Theorem

The **CAP Theorem** applies to distributed databases, which store data across multiple computers or servers (like in cloud systems). It states that a distributed database can only guarantee two out of three properties at once: **Consistency, Availability, and Partition Tolerance**. This forces database designers to make trade-offs.

- **Consistency**: Every server in the system shows the same data at the same time. If you update your address in an online store, every server reflects that change instantly, so no one sees an old address.
- **Availability**: The database always responds to requests, even if it means returning slightly outdated data. This ensures you can always access the system, even during issues.
- **Partition Tolerance**: The system keeps working even if some servers can’t communicate due to network failures. This is crucial for systems spread across cities or countries.

Since network issues (partitions) are inevitable in distributed systems, databases must choose between being **CP** (consistent and partition-tolerant, but less available) or **AP** (available and partition-tolerant, but less consistent). **CA** systems (consistent and available) are rare because they can’t handle partitions well.

## Joins

**Joins** combine data from two or more tables in a relational database based on a common column, like an ID. They’re essential for pulling related information together in a single query.

- **Inner Join**: Returns only rows where there’s a match in both tables. For example, if you have a "Customers" table and an "Orders" table, an inner join shows only customers who have placed orders.
- **Left Join**: Returns all rows from the first table and matching rows from the second. If there’s no match, it fills in with "null." For example, a left join lists all customers, even those without orders, with blanks for order details.
- **Right Join**: Opposite of left join, it includes all rows from the second table, with nulls for non-matching rows from the first.
- **Full Join**: Combines all rows from both tables, with nulls where no match exists. It’s like combining left and right joins.

## Aggregations and Filters in Queries

**Aggregations** and **filters** are used in database queries to summarize or narrow down data, making it easier to analyze or display.

- **Aggregations**: These perform calculations on data, like counting rows, summing values, averaging numbers, or finding the minimum/maximum. For example, a query might calculate the total revenue from all sales (`SUM(sale_amount)`) or count how many orders were placed (`COUNT(*)`).
- **Filters**: These limit the data returned based on conditions. For example, a `WHERE` clause like `WHERE city = 'Chicago'` shows only records for Chicago customers. Filters can also use ranges, like `WHERE order_date >= '2025-01-01'`.

## Normalization

**Normalization** is the process of organizing a database to eliminate redundant data and ensure logical relationships. It splits data into smaller, related tables and uses keys (like IDs) to connect them. This makes databases easier to maintain and reduces errors.

- **First Normal Form (1NF)**: Ensures each column contains only one value (no lists or groups). For example, instead of a column with "apple, banana" in one row, split it into separate rows or columns.
- **Second Normal Form (2NF)**: Requires that all non-key columns depend on the entire primary key (a unique identifier for a row). For instance, in an "Orders" table with a composite key (order_id, product_id), details like product name must relate to both, not just one.
- **Third Normal Form (3NF)**: Ensures no non-key column depends on another non-key column. For example, don’t store a customer’s city and zip code together if the zip code determines the city—put city in a separate table.

## Indexes

**Indexes** are like a book’s index, helping the database find data faster. They’re special data structures that store pointers to rows based on specific columns, like a customer’s name or order date.

- Without an index, the database scans every row (called a full table scan), which is slow for large tables.
- With an index, the database jumps directly to the relevant rows, speeding up queries.
- Indexes are created on frequently searched columns, but they take extra storage space and can slow down data updates (inserts, updates, deletes) because the index must be updated too.

## Transactions

A **transaction** is a group of database operations treated as a single unit. Either all operations succeed, or none are applied, ensuring data stays consistent.

- For example, when you pay a bill online, the database might deduct money from your account and mark the bill as paid in one transaction. If any step fails (e.g., the bill can’t be updated), the whole transaction is undone (rolled back).
- When all steps succeed, the transaction is committed (saved permanently).
- Transactions rely on ACID properties to work correctly.

## Locking Mechanism

**Locking** controls how multiple users or processes access the same data at the same time, preventing conflicts like two people changing the same record simultaneously.

- **Shared Lock**: Allows multiple users to read data but not change it. For example, many people can view a product’s price at once.
- **Exclusive Lock**: Allows only one user to change data, locking others out until the change is done. For example, only one person can update a customer’s address at a time.
- Locks are automatically applied during transactions and released when the transaction commits or rolls back.

## Database Isolation Levels

**Isolation levels** define how transactions interact with each other, controlling what changes one transaction can see from another. They balance data accuracy with performance.

- **Read Uncommitted**: The least strict (and fastest) level. Transactions can see uncommitted (unsaved) changes from others, risking "dirty reads." For example, you might see a payment that’s later undone.
- **Read Committed**: Only shows committed changes, preventing dirty reads. However, repeated reads might show different results if another transaction commits midway.
- **Repeatable Read**: Ensures data read during a transaction doesn’t change, even if others commit changes. This prevents "non-repeatable reads" but may allow "phantom reads" (new rows appearing).
- **Serializable**: The strictest (and slowest) level. Transactions run as if one at a time, preventing all conflicts but reducing speed.

## Triggers

**Triggers** are automatic actions the database performs when specific events occur, like inserting, updating, or deleting a row. They’re like pre-programmed rules that run without extra effort.

- For example, when a new order is added, a trigger can automatically reduce the product’s stock in the inventory table.
- Triggers can enforce rules (e.g., reject invalid data) or log changes (e.g., record who updated a record).
- They’re powerful but can slow down operations if overused, as they run every time the event occurs.

