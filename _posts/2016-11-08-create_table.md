---
layout: post
title: Flask Intro
excerpt: "Basic Postgresql Functionality"
comments: false
---

**Create, Insert, Select, Delete in Postgresql**
To Create table in the Postgresql you follow the basic syntax shown below:

    CREATE TABLE table_name (
		column_name1 col_type (field_length),
        column_name2 col_type (field_length),
        column_name3 col_type (field_length)
    );


As you can see, we give the table a name, and then define the columns that we want, as well as the column type and the max length of the field data.

For our purposes, we're going to create a simple table like this:

    CREATE TABLE stundent_info (
        student_id serial PRIMARY KEY,
        first_name varchar (50) NOT NULL,
        last_name varchar (25) NOT NULL,
        Address text
    );
We have made a student_info table that stores the student information. First column in the table is student_id, which is of the serial type. This data type is an auto-incrementing integer. We have given this column the constraint of primary key which means that the values must be unique and not null.
Some columns have a NOT NULL attribute, which means that these columns can not be left empty and must be filled when inserting data into the table. Unlike varchar, address is type text which does not need the length attribute. 

We can see our new table by typing this:

    \d

                       List of relations
     Schema |          Name              |   Type   |  Owner   
    --------+----------------------------+----------+----------
     public | student_info               | table    | postgres
     public | student_info_student_id_seq| sequence | postgres
    (2 rows)

As you can see, we have our student_info  table, but we also have something called student_info_student_id_seq that is of the type sequence. This is a representation of the "serial" type we gave our student_id column. This keeps track of the next number in the sequence.

Now that we have a table created, we can insert some data into it.
Let's add a student record. We do this by calling the table we're wanting to add to, naming the columns and then providing data for each column. Our student record could be added like this:

    INSERT INTO student_info (frist_name, last_name, address) values ('John', 'Snow', 'abc street');
You should notice a few things. First, keep in mind that the column names should not be quoted, but the column values that you're entering do need quotes.

Another thing to keep in mind is that we do not enter a value for the student_id column. This is because this is auto-generated whenever a new row in the table is created. You can always override the auto_generation sequence by providing the unique ID. In that case you have to provide column name student_id and the unique value that can be associated with that column student_id.

 We can then get back the information we've added by typing:

     student_id	| first_name | last_name  | address
     1	          John         Snow         abc street

Here, you can see that our student_id has been filled in successfully and that all of our other data has been organized correctly.

We can also remove the row from our table by typing:

    DELETE FROM student_info WHERE first_name = 'John';

