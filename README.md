[README.md](https://github.com/user-attachments/files/29162115/README.md)
# Build a Student Database: Part 2

A set of advanced SQL queries run against the student/major/course database from Part 1, covering pattern matching, multi-table joins, aggregation, and anti-join logic. Built as part of freeCodeCamp's Relational Database certification.

## What This Demonstrates

- **Pattern matching with `LIKE` and `ILIKE`**: filtering on partial string matches, wildcard positions (`'_e%'`, `'%r_'`), and case-insensitive search, the same techniques used to build flexible search and filter features in real applications.
- **Multi-condition filtering**: combining `AND`/`OR` logic with comparison operators and range conditions in a single `WHERE` clause, including correct operator precedence with parentheses.
- **Joins across three tables**: chaining `INNER JOIN`, `RIGHT JOIN`, and `FULL JOIN` across `students`, `majors`, `majors_courses`, and `courses` to answer questions that span the full relationship graph, not just a single table.
- **Aggregation with `GROUP BY` and `HAVING`**: computing per-group counts and averages (`COUNT`, `AVG`, `ROUND`), then filtering those aggregated results with `HAVING`, the correct way to filter on an aggregate rather than a raw column.
- **Anti-join / "find the gap" logic**: using `FULL JOIN` plus a `NULL` check to find majors with zero enrolled students, and `RIGHT JOIN` plus a `NULL` check to find courses nobody is taking. This pattern (find rows in A with no match in B) comes up constantly in real data work, like finding unfulfilled orders or unmatched records during data reconciliation.
- **Readable, well-documented query scripts**: each query is preceded by a plain-English comment describing exactly what it returns, useful both for review and for explaining query logic to non-technical stakeholders.

## Sample Queries

| Query | SQL Technique |
|---|---|
| Students with a 4.0 GPA | Simple equality filter |
| Courses starting before "D" alphabetically | String comparison |
| Students with last names "R" or later, with extreme GPAs | Combined `AND`/`OR` with parentheses |
| Last names containing "sa" or with "r" as second-to-last letter | `ILIKE` and wildcard `LIKE` |
| Top 5 courses by name pattern, reverse alphabetical | `LIKE`, `ORDER BY DESC`, `LIMIT` |
| Average GPA across all students | `AVG`, `ROUND` |
| Student count and average GPA per major (majors with 2+ students) | `GROUP BY`, `HAVING` |
| Majors with no students, or students with "ma" in their name | `FULL JOIN` with `NULL` check |
| Courses nobody is taking, or taken by a specific student | `RIGHT JOIN`, `INNER JOIN`, anti-join logic |
| Courses with exactly one enrolled student | Multi-table `JOIN`, `GROUP BY`, `HAVING COUNT(*) = 1` |

## Running This Project

1. Create the database from the schema: `psql -U your_username -f students.sql`
2. Run the query script: `./student_info.sh`

## Course

Part of [freeCodeCamp's Relational Database Certification](https://www.freecodecamp.org/learn/relational-databases-v9/).

