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

task - 4
==========

No, They can not . containers om the default bridge network can onlhy communicate with each other using the ip address , not their container names , automatic dns resolutions is disabled on the default bridge for security and isolation reasons


to allow containers to ping and comminicate with each other by name , you must use a user defined bridge network.


docker network create my_custom_network

yes they can .containers on the default bridge network can ping each other by ip address by default .docker does not block direct ip to ip communicate between containers on the same network unless you explicitely configyre it to do so.

