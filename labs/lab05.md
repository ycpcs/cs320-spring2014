---
layout: default
title: "GWT Calculator"
---

Your task is to create a simple calculator application using [GWT](http://www.gwtproject.org).

# Getting started

Start by downloading [CS320\_Lab05.zip](CS320_Lab05.zip).  Import it into Eclipse (**File &rarr; Import... &rarr; General &rarr; Existing projects into workspace &rarr; Archive file**.

You should see a project called **CS320\_Lab05** in your Eclipse workspace.

# Your task

Your task is to implement a simple calculator that looks something like this:

(TODO: screenshot.)

# Hints

Open **OperationAndResultView.java** by right clicking and choosing **Open With &rarr; GWT Designer**.

Add labels and text boxes to allow the user to enter two numeric values.

Add buttons for Add, Subtract, Multiply, and Divide operations.

Add click handlers for the buttons.  They should convert the text in the textboxes to **double** values, and then use the controller to set the first and second operand values and an operation type, and then call the **perform** method to compute a result value (modifying the **Result** object).

When the value of the **Result** object changes, the result should be displayed automatically (in the **ResultView** which is already part of **OperationAndResultView**).
