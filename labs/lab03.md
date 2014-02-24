---
layout: default
title: "Lab 3: JavaScript and jQuery"
---

Your Task
=========

Modify the [Canvas Demo](../lectures/lecture08/canvas.html) so that the circles bounce around inside the box. Each timer tick callback should check the position of each circle to see if it has reached the edge of the canvas, and if so, deflect it away from the edge.

Hints
-----

You will need to add fields to each circle object to keep track of each circle object's vertical and horizontal velocity. For example, you could add **dx** and **dy** fields to keep track of the distance the circle moves in the x and y directions on each timer tick.
