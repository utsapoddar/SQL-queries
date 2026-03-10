# SQL Queries Practice

This repository contains a collection of example SQL queries used for learning and demonstrating database querying and analytics skills. The queries are designed to showcase common operations such as selecting, filtering, joining tables, grouping and aggregation, sorting, and using window functions and subqueries. A PDF schematic of the sample database is included for reference.

## Contents

- **company-database.pdf** – ER diagram / schema showing the tables and relationships used in the example queries.
- **example_queries.sql** – SQL file containing all the example queries used for practice.

## How to Use

1. Review the `company-database.pdf` to familiarize yourself with the schema. It describes tables such as `employees`, `departments`, and `salaries` and shows how they are related.
2. Create a sample database in your preferred SQL environment (e.g., PostgreSQL, MySQL, SQLite) based on the schema described in the PDF. You can use your own sample data or generate data that matches the schema.
3. Open `example_queries.sql` in a SQL editor or command line and execute the queries against your sample database. Each query demonstrates a particular concept.
4. Experiment by modifying the queries or writing your own to answer additional analytical questions.

## Topics Covered

- Basic `SELECT` statements and filtering rows using `WHERE`.
- Joining tables (INNER JOIN, LEFT/RIGHT JOIN, etc.).
- Grouping and aggregation (`GROUP BY`, `HAVING`, `COUNT`, `SUM`, `AVG`).
- Sorting results with `ORDER BY`.
- Subqueries and common table expressions (CTEs).
- Window functions (e.g., `ROW_NUMBER`, `RANK`, `OVER`).
- Set operations (`UNION`, `INTERSECT`, `EXCEPT`).

These queries serve as a starting point for practicing SQL and exploring typical patterns used in data analysis and reporting.

## Contributing

Feel free to fork this repository and contribute additional queries or improvements. For significant changes, please open an issue or discussion first to propose your changes.

## License

This project is licensed under the [MIT License](LICENSE).
