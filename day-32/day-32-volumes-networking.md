### Task 1: The Problem
1. Run a Postgres or MySQL container
2. Create some data inside it (a table, a few rows — anything)
3. Stop and remove the container
4. Run a new one — is your data still there?
=====================================================

-> docker run --name my-postgres-test -e POSTGRES_PASSWORD=bijaya -p 5432:5432 -d postgres

-> docker logs postgres

-> docker exec -it postgres bash

-> psql -U postgres
-> \dt
-> CREATE TABLE users (
    id SERIAL PRIMARY KEY,
    name VARCHAR(50),
    email VARCHAR(50)
);

-> Insert three rows of sample data
INSERT INTO users (name, email) VALUES 
('Alice Smith', 'alice@example.com'),
('Bob Jones', 'bob@example.com'),
('Charlie Brown', 'charlie@example.com');

-> SELECT * FROM users;

-> \dt users

-> docker stop postgres && docker rm posgres


docker ps

then run new one  postgres container check table and data not exists