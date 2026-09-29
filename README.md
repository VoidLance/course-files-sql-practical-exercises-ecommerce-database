# SQL Practical Exercises: eCommerce Database

Hands-on SQL practice for creating and managing a small online-store database. The repository contains the exercise write-up, a bundled course solution script, and exported MySQL/MariaDB table files for reference.

## Why this project is useful

This project is a compact example of the core data-management operations used in an eCommerce schema:

- Create `customers`, `products`, and `orders` tables.
- Insert related records and enforce primary-key, unique, and foreign-key constraints.
- Update customer details, product prices, and order quantities.
- Delete records while considering relationships between tables.
- Practice grouping changes in transactions with `START TRANSACTION` and `COMMIT`.

It is intended for learners who want a small, repeatable database exercise rather than a production application.

## Repository contents

| Path | Description |
| --- | --- |
| [`exercises.md`](exercises.md) | Exercise notes, SQL statements, and the author's working process. |
| [`KlHHUzwESRClNNu6xcJJ_Module_7.zip`](KlHHUzwESRClNNu6xcJJ_Module_7.zip) | Course-provided archive containing `Module_7.sql`. |
| `Practical@0020Exercises/` | MySQL/MariaDB `.frm`, `.ibd`, and database metadata files exported from a local database. |

## Getting started

### Prerequisites

- MySQL 8.x or MariaDB 10.x (or a compatible MySQL client/server).
- A shell with `unzip` if you want to extract the bundled course script.

There is no application server or package dependency to install.

### Create a practice database

Start a local MySQL or MariaDB server, then create a database and select it:

```sql
CREATE DATABASE ecommerce_practice;
USE ecommerce_practice;
```

The schema and sample data are documented in [`exercises.md`](exercises.md). Copy the relevant SQL into your client, or extract and run the course script:

```sh
unzip -p KlHHUzwESRClNNu6xcJJ_Module_7.zip Module_7.sql > /tmp/Module_7.sql
mysql -u <username> -p ecommerce_practice < /tmp/Module_7.sql
```

The script creates three related tables and demonstrates inserts, updates, and deletes. To inspect the resulting data:

```sql
SELECT * FROM Customers;
SELECT * FROM Products;
SELECT * FROM Orders;
```

The script is designed as a learning exercise and does not include a reset or migration framework. If you rerun table-creation statements, reset the practice database first or add appropriate `DROP TABLE` statements in foreign-key dependency order.

## Database model

The tables form a simple relationship:

```text
Customers 1 ────< Orders >──── 1 Products
```

`Orders.CustomerID` references `Customers.CustomerID`, and `Orders.ProductID` references `Products.ProductID`. The course script uses auto-incrementing identifiers; the worked notes in `exercises.md` also show explicit identifiers and transaction examples.

## Getting help

Start with the comments and explanations in [`exercises.md`](exercises.md), then consult the documentation for the database engine you are running:

- [MySQL Reference Manual](https://dev.mysql.com/doc/refman/8.0/en/)
- [MariaDB Server Documentation](https://mariadb.com/kb/en/documentation/)

For a reproducible question, include the SQL statement, database engine/version, and the exact error message. Do not include passwords or other credentials.

## Contributing

Contributions that improve the exercises, clarify the notes, or correct SQL are welcome. Before opening a change:

1. Keep examples compatible with MySQL/MariaDB unless a difference is explicitly documented.
2. Test SQL in a disposable practice database.
3. Update [`exercises.md`](exercises.md) when changing the demonstrated workflow.
4. Describe what was tested in the pull request or commit.

Please keep changes focused on the learning materials and avoid committing local database credentials or unrelated exported files.

## Maintainer

This repository is maintained by [Alistair Sweeting](https://github.com/VoidLance). Use GitHub issues or pull requests for questions, corrections, and improvements.

## License

No `LICENSE` file is currently included in the repository. Add or consult the project owner's license terms before redistributing these materials.
