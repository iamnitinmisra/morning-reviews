# Week 7, Day 4 Review

Given that this is the last morning review that students receive before jumping into personal projects, I have found that this is a good time to ask students what they have questions on and prioritize those questions first. If there are no questions, now would be a good time to review with students the importance of structuring DB tables and information correctly (a review of SQL-2).

See the note from the SQL-2 - Week 6, Day 4 morning review [here](../week6/sql-2)

If this morning review has already been delivered, have the students work through a whiteboarding exercise, some CodeWars problems, or have them work through some sort of additional debugging practice. 

**SEND SLIDES OUT TO THE COHORT FIRST**

```SQL
DROP TABLE IF EXISTS friends;
DROP TABLE IF EXISTS group_post_comments;
DROP TABLE IF EXISTS user_post_comments;
DROP TABLE IF EXISTS group_posts;
DROP TABLE IF EXISTS user_posts;
DROP TABLE IF EXISTS group_members;
DROP TABLE IF EXISTS groups;
DROP TABLE IF EXISTS user_information;
DROP TABLE IF EXISTS users;

CREATE TABLE users(
user_id SERIAL PRIMARY KEY,
username VARCHAR(500),
password VARCHAR(3000)
);

--this table will have a relationship with the users table

CREATE TABLE user_information(
user_id INTEGER REFERENCES users(user_id),
first_name VARCHAR(100),
last_name VARCHAR(100),
profile_pic VARCHAR(3000),
birthday DATE
);

-- Next Slide (3/7)

CREATE TABLE groups(
group_id SERIAL PRIMARY KEY,
description VARCHAR(3000),
organizer INTEGER REFERENCES users(user_id),
creation_date DATE
);

-- Take the next 5 minutes to write create a new table called "group_members", using a join statement.

-- 3 columns should be included:
-- user_id (users table)
-- group_id (groups table)
-- creation_date (groups table)

SELECT users.user_id, groups.group_id, groups.creation_date
INTO group_members
JOIN groups ON users.user_id = groups.group_id;


-- We can use aliasing to clean up the code
-- SELECT u.user_id, g.group_id, g.creation_date
-- INTO group_members
-- FROM users u
-- JOIN groups g ON u.user_id = g.group_id;

-- SELECT * FROM group_members;

--(SLIDE 4/7)

CREATE TABLE user_posts(
post_id SERIAL PRIMARY KEY,
user_id INTEGER REFERENCES users(user_id),
title VARCHAR(100),
text VARCHAR(3000),
date DATE
);

--(SLIDE 5/7)

CREATE TABLE group_posts(
id SERIAL PRIMARY KEY,
group_id INTEGER REFERENCES groups(group_id),
title VARCHAR(100),
text VARCHAR(3000),
date DATE
);

--(SLIDE 6/7)

CREATE TABLE user_post_comments(
id SERIAL PRIMARY KEY,
user_id INTEGER REFERENCES users(user_id),
post_id INTEGER REFERENCES user_posts(post_id),
title VARCHAR(100),
text VARCHAR(3000),
date DATE
);

--(SLIDE 7/7)

CREATE TABLE group_post_comments(
id SERIAL PRIMARY KEY,
user_id INTEGER REFERENCES users(user_id),
post_id INTEGER REFERENCES group_posts(id),
title VARCHAR(100),
text VARCHAR(3000),
date DATE
);

CREATE TABLE friends (
user_id INTEGER REFERENCES users(user_id),
friend_id INTEGER REFERENCES users(user_id),
accepted BOOLEAN
);

INSERT INTO users(username, password)
VALUES 
('abbey', 'a'),
('cassiopeia', 'a'),
('orion', 'a'),
('pippa', 'a');

-- SELECT * FROM users;

INSERT INTO user_information(user_id, first_name, last_name, profile_pic, birthday)
VALUES
(1, 'Abbey', 'Misra', 'NA', '1990-01-01'),
(2, 'Cassiopiea', 'Misra', 'NA', '2010-02-12'),
(3, 'Orion', 'Misra', 'NA', '2016-03-01'),
(4, 'Pippa', 'Misra', 'NA', '2012-04-01');

-- SELECT * FROM user_information;
INSERT INTO groups(description, organizer, creation_date)
VALUES
('Group 1', 3, '2020-06-10'),
('Group 2', 1, '2020-01-01'),
('Group 3', 3, '2019-12-12');

INSERT INTO group_members(user_id, group_id, creation_date)
VALUES
(3, 1, '2020-06-10'),
(1, 2, '2020-01-01'),
(4, 3, '2019-12-15'),
(2, 3, '2020-02-02');

```