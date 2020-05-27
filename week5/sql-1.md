# Week 5, Day 3 Review - SQL 1

Before jumping in, ask for any questions. Try to structure the review around their questions, making sure to touch on any points they ask about. I find it helpful to write down all of their questions at the start and work from there.

## Lecture Notes and Slides

- Notes: https://github.com/WLH-16/sql-1
- Slides: https://slides.com/matias_perez/scott-s-sql-one/

## Important Concepts to Review

1. What is SQL?
2. Common Queries and Syntax
   - CREATE TABLE
   - SELECT
   - INSERT
   - UPDATE
   - DELETE
3. Conditional Statements & Logical Operators
   - <, >, <=, >=, IN, NOT IN, AND, OR

## Review
Using the link to the DevMountain PostgreSQL DB included [here](https://postgres.devmountain.com/), have the students do the following:


    3. Using a `SELECT` query, return all the movies from the `movies` table
    4. Using an `UPDATE` query, update the `title` of the second movie in the `movies` table
    5. Using a `DELETE` query, delete the third movie in the `movies` table
    6. Using a `SELECT` query, return all movies from the `movies` table ordered by `release_year` ascending
    7. Using a `SELECT` query, return all movies from the `movies` table where the `release_year` is greater than 1995
    8. Using a `SELECT` query, return all movies from the `movies` table where the `release_year` is greater than or equal to 2000
    9. Using a `SELECT` query, return all movies from the `movies` table where the `release_year` is less than 2010 or greater than 2013
    10. Using a `SELECT` query, return all movies from the `movies` table where the `release_year` is less than to 2010 and `id` is greater than 2
    11. Using a `SELECT` query, return all movies from the `movies` table where the `release_year` is either 2001, 2002, 2003, or 2004
    12. Using a `SELECT` query, return all movies from the `movies` table where the `release_year` is not 2001, 2002, 2003, or 2004
    13. Using a `DROP TABLE` query, drop the `movies` table from the database

Feel free to have the students practice additional SQL statements as needed

1. Create a table called `movies` with columns for `id`, `title`, `director`, and `release_year`
```SQL
CREATE TABLE movies (
   id SERIAL PRIMARY KEY,
   title VARCHAR(64),
   director VARCHAR(50),
   release_year INTEGER
);
```
2. Add 5 movies into the `movies` table
```SQL
INSERT INTO movies
(title, director, release_year)
VALUES
('The Matrix', 'The Wachowski Brothers', 2000),
('Back to the Future', 'Robert Zemeckis', 1985),
('Inception', 'Christopher Nolan', 2010),
('Star Wars: Return of the Jedi', 'Richard Marquand', 1983),
('The Fast and the Furious', 'Rob Cohen', 2001);
```
3. Using a `SELECT` query, return all the movies from the `movies` table
```SQL
SELECT * FROM movies;
```
4. Using an `UPDATE` query, update the `title` of the second movie in the `movies` table
```SQL
UPDATE movies
SET title = 'Back to the Future Part II', director = 'Robert Zemeckis', release_year = 1989 
WHERE id = 2;
```
5. Using a `DELETE` query, delete the third movie in the `movies` table
```SQL
DELETE FROM movies
WHERE id = 3;
```
6. Using a `SELECT` query, return all movies from the `movies` table ordered by `release_year` ascending
```SQL
SELECT * FROM movies
ORDER BY release_year ASC;
```
7. Using a `SELECT` query, return all movies from the `movies` table where the `release_year` is greater than 2000
```SQL
SELECT * FROM movies
WHERE release_year > 2000;
```
8. Using a `SELECT` query, return all movies from the `movies` table where theh `release_year` is greater than or equal to 1985
```SQL
SELECT * FROM movies
WHERE release_year >= 1985;
```
9. Using a `SELECT` query, return all movies from the `movies` table where the `release_year` is less than 1985 or greater than 2000
```SQL
SELECT * FROM movies
WHERE release_year < 1985
OR release_year > 2000;
```
10. Using a `SELECT` query, return all movies from the `movies` table where the `release_year` is less than 2010 and `id` is greater than 2
```SQL
SELECT * FROM movies
WHERE release_year < 2010
AND id > 2;
```
11. Using a `SELECT` query, return all movies from the `movies` table where the `release_year` is either 1983 or 2000
```SQL
SELECT * FROM movies
WHERE release_year = 1983
OR release_year = 2000;
```
12. Using a `SELECT` query, return all movies from the `movies` table where the `release_year` is not 1983 or 2000

note: `OR` will not work because it will grab all of the movies. need to use `AND` instead
```SQL
SELECT * FROM movies
WHERE release_year != 1983
OR release_year != 2000;

SELECT * FROM movies
WHERE release_year != 1983
AND release_year != 2000;
```

13. Using a `SELECT` query, return all movies whose name start with "The"
```SQL
SELECT * FROM movies
WHERE title LIKE 'The%';
```

14. Using a `DROP TABLE` query, drop the `movies` table from the database
```SQL
DROP TABLE movies;
```