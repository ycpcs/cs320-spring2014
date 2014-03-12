---
layout: default
title: "Lab 6: SQL, Queries, Joins"
---

Getting Started
===============

Download [CS320\_Lab06.zip](CS320_Lab06.zip). Import it into your Eclipse workspace (**File-\>Import...-\>General-\>Existing projects into workspace-\>Archive File**). You will see a project called **CS320\_Lab06** in the Package Explorer.

Setting up the database
=======================

Execute the **SQLDemo** class as a Java application.

Use **create table** commands to create **books** and **authors** tables. From the **SQL\>** prompt, enter the following commands:

    create table books (
        author_id integer,
        title varchar(50),
        isbn varchar(20)
    );

    create table authors (
        author_id integer primary key,
        author_lastname varchar(40),
        author_firstname varchar(40)
    );

Next, use **import** commands to load data into these tables:

    import books books.csv;

    import authors authors.csv;

Your database is now populated with data.

The schemas of the database tables are described in the notes for [Lecture 11](../lectures/lecture11.html).

Task
====

Try executing some queries to retrieve the following information:

-   the titles of all books written by F.G. Smallfinger
-   the titles of all books written by Callus Tacticus
-   the author name (first and last) and the ISBN number of the book with the title "First Flights in Witchcraft"

Each query should be terminated with a semicolon (**;**). For example, here is session showing a query to select all of the tuples in the **authors** table (user input in **bold**):

<pre>
SQL> <b>select * from authors;</b>
author_id author_lastname author_firstname
--------- --------------- ----------------
        1     Smallfinger             F.G.
        2       Whittlbey           W.H.J.
        3          Earwig          Lettice
        4         Lightly             W.E.
        5        Tacticus           Callus
OK (5 rows(s))
</pre>
