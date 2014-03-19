---
layout: default
title: "Lab 8: ORM"
---

# Getting Started

Download [CS320\_Lab08.zip](CS320_Lab08.zip). Import it into your Eclipse workspace (**File&rarr;Import...&rarr;General&rarr;Existing projects into workspace&rarr;Archive File**). You will see a project called **CS320\_Lab08** in the Package Explorer.

Start by creating the **test.db** file that creates the initial [books database](../lectures/lecture11.html).  (Note that there are some minor differences in the relations, specifically the addition of an **id** field to the **books** relation.)  Execute the **SqliteDatabase** class as a Java application: you should see the following output:

    Creating tables...
    Loading initial data...
    Success!

You may work individually or with a small group.

# Task

In the lab skeleton you will find a program called **TitleQuery** which demonstrates using an ORM interface to find all books that have the title entered by the user (along with the author information).

Your task is very similar to [Lab 7](lab07.html), except that rather than directly executing database queries/statements, you will add methods to the **IDatabase** interface and implement them in **FakeDatabase** and **SqliteDatabase**.

Tasks:

Using **TitleQuery** as a model, write your own programs to do the following:

1. Find all books written by the author whose last name is specified. Return the books in the same form as the **TitleQuery** program.
2. Given the full (first and last) name of an author, a title, and an ISBN, insert the book into the database. The program should add a new tuple to the authors table if the author doesn't already exist. If the author does exist already, the program should use that author's **author\_id**.  Use the SQL **insert** statement to insert the new tuple(s).

## Hints

For the first task, add the following method to **IDatabase**:

    public List<Pair<Author, Book>> findAuthorAndBookByAuthorLastName(String lastname);

Implement it in **FakeDatabase** and **SqliteDatabase**.  Start by implementing the method in **FakeDatabase** (just have the method in **SqliteDatabase** throw an **UnsupportedOperationExecption**.)

For the second task, do a query to see if the author exists.  If it doesn't, insert it.  (Note: you will want to have the database automatically assign an author id).  Then, use the author id to insert a new tuple into the books relation.  Note that the entire operation should be executed as part of a single transaction.

<!-- vim:set wrap: ­-->
<!-- vim:set linebreak: -->
<!-- vim:set nolist: -->
