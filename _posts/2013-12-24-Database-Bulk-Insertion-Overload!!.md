---
layout: posts
title: Database Bulk Insertion Overload!!
permalink: /posts/database-bulk-insertion
author: vtruong
---

Database Bulk Insertion Overload!!
=================

> Imagine that you're in a do or die scenario where you must insert one million records in a table and this database transaction can be done within a matter of seconds. But how exactly are we suppose to do this?
>
> Let us suppose that we have a table called users. Within this users table, we have column names called first_name, last_name, email, phone_no and password. We also have a CSV file that contains information found within each row that can fill each record's field which is separated by a comma.
>
> For example,
		Vincent, Truong, vincentruong90@gmail.com, 1231231324, password6843
		Bob, Smith, bsmith@gmail.com, 1231231324, pas1234sword6843
>
> Our *objective* is to import the CSV file into the users table.
>
> One way of doing this is to create a script that will insert the CSV records one by one with the following SQL insert statement.
>
		INSERT INTO users VALUES (Vincent, Truong, vincentruong90@gmail.com, 1231231324, password6843);
		INSERT INTO users VALUES (Bob, Smith, bsmith@gmail.com, 1231231324, pas1234sword6843);
>
> Seems easy enough? Well imagine doing this one million times for each different record. This will take quite a bit of time because for each INSERT SQL script requires a database transaction. There are three steps are required for a database transaction to go through:
		1. Initiate the database transaction
		2. Run a data manipulation query or in this example, an INSERT SQL query
		3. If there are no errors, commit to the database; else, rollback the transaction
>
> These steps can be hefty on database traffic operations because depending on the database; other incoming transactions must wait for the bulk insertion transaction to complete or if the database allows other database transactions to come through, the bulk insertion transaction will take forever to complete. After doing this brute force mysql insertion transaction, I had to find a BETTER way to this tedious task. This ONE line mysql code does exactly the job FOR YOU in a single database transaction. You're welcome.
		load data infile '/my/path/to/file.csv' fields terminated by ',' enclosed by '"' lines terminated by '\n'
>
> Cheers.




