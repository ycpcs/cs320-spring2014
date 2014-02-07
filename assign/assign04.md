---
layout: default
title: "Assignment 4: Problem Domain Analysis"
---

Due: <strike>Monday, February 17th</strike> **Wednesday, February 19th** by 11:59 PM

This is a **team** assignment

Problem Domain Analysis
=======================

In this assignment, your team will conduct an analysis of the problem domain of your team project, and build an analysis model of the problem domain.

Step 1: Textual Analysis
------------------------

Go through the requirements and use cases you wrote in [Assignment 3](assign3.html). Identify the important noun and verb phrases which describe entities and concepts in your problem domain.

Step 2: Build an Analysis Model
-------------------------------

Based on your textual analysis, construct a UML class diagram using [Violet UML](http://alexdp.free.fr/violetumleditor/page.php) which models the "core" classes in your problem domain.  Note that you can download the Violet UML jar file from the course [Resources](../resources/index.html) page.

> **Note**: If you would like to use a different UML modeling tool, please see me.

Use associations (plain, aggregation, composition) and generalizations (Is-A / inheritance) to show the relationships between the classes (noun phrases) in your model. Give each association a name to indicate the roles of the two classes involved in the association. Add the important methods (verb phrases) to the classes to which they are most likely to belong. Don't worry about specifying parameters and return types for the methods.

> **NOTE**: Because you are building an analysis model, avoid modeling any "implementation" classes such as those involved in the user interface, data storage, etc., unless there are important requirements which would not otherwise be addressed by the model.

Step 3: Explain the Model
-------------------------

In a text document of 1 page, *briefly* explain your analysis model. Discuss why you felt the classes you modeled are the most important ones. Is there a class or classes that seem to be "central" to the model? How did you determine where to put the important methods?

Submitting
==========

Create a zip file containing:

1.  a text document with your textual analysis (noun and verb phrases)
2.  the Violet UML (.class.violet) file with your analysis model
3.  a text document with your explanation of the analysis model

Text documents must be in **PDF** format.

You can create a zip file using Windows by creating a folder, putting some files inside the folder, right-clicking on the folder, and choosing **Send to &rarr; Compressed Folder**.

Upload the zip file to the Marmoset server as **assign04**:

> <https://cs.ycp.edu/marmoset/>

Only one team member needs to upload the zip file.
