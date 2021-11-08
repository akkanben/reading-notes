# Reading Notes 11 - Mongo & Mongoose

## NoSQL vs. SQL

From [The Geek stuff article](https://www.thegeekstuff.com/2014/01/sql-vs-nosql-db/?utm_source=tuicool)

| SQL | NoSQL |
| --- | ----- |
| Relational | Not Relational |
| Strict Schema | No Schema |
| Vertical Scaling | Horizontal Scaling |
| Data on multiple tables| Data is typically merged (fewer tables) |
| Limitations in huge read/writes per second| Fewer limitations and massive read/writes |

1. What kind of data is a good fit for an SQL database?
  - Data that can take advantage of complex queries, and not a good fit for hierarchical data.
2. Give a real world example.
  - Something like a payroll system where the layout is known ahead of time.
3. What kind of data is a good fit a NoSQL database?
  - Something that would benefit from a more dynamic data layout
4. Give a real world example.
  - 'Big Data' or something that uses more real-time data.
5. Which type of database is best for hierarchical data storage?
  - SQL
6. Which type of database is best for scalability?
  - SQL scales vertically well, increasing a single servers RAM/CPU/SSD will improve performance. NoSQL scales better horizontally by adding more servers.

## SQL vs. NoSQL part deux

From the [Academind](https://www.youtube.com/watch?v=ZS_kXvOeQ5Y)


1. What does SQL stand for?
  - Structured Query Language
2. What is a relational database?
  - A database that is meant to be used with multiple tables that can be combined in queries.
3. What type of structure does a relational database work with?
  - A strict schema.
4. What is a ‘schema’?
  - The shape or layout/structure of the tables and fields of the database.
5. What is a NoSQL database?
  - A database that has no schema and does not require fixed shapes to each table.
6. How does it work?
  - Instead of a table with fixed fields and consistent record sizes, a NoSQL DB has no schema and can have documents of completely different shapes.
7. What is inside of a Mongo database?
  - Collections that are similar in concept to tables. Collections are filled with documents (JSON like files).
8. Which is more flexible - SQL or MongoDB? and why.
  - A MongoDB would be more flexible because additional data can be added to new documents and old data doesn't need to be affected by it. This makes NoSQL more adaptable. Horizontal scalability also has fewer limits than vertically scaling.
9. What is the disadvantage of a NoSQL database?
  - The database user is responsible for knowing the shape of the data and being consistent if that is important because there is no guarantee that a group of data will have the same shape. Also this type of database is not designed for querying data from different documents do there ends up being duplicate data when compared with a SQL database.

## Things I want to know more about

- The practical things involved in reading and writing to databases from our code.
- Big Data
