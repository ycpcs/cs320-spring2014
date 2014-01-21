---
layout: default
title: "Lecture 6: OO Design, OCP, LSP"
---

OO Design
=========

Basic idea: take our analysis model and turn it into a detailed blueprint for our implementation

Design goals:

> 1. Design a system that will solve the problem
>
> > In enough detail that the implementation should flow easily from the design
>
> 2. Design a system that is easy to change

Goal \#1 should be fairly obvious - there's no point in building incorrect software.

Goal \#2 has several important motivations:

> We know the requirements will change as the system evolves.
>
> We know that we will learn more about the problem and revisit earlier decisions.
>
> Designs that accomodate change tend to be easy to understand - which is very important when we're dealing with a complex system.

As always in software development, there are an infinite number of ways we could design a system to solve any particular problem. So, how will we design a system that best achieves our goals?

Having a good analysis model generally gives us a very good place to start in constructing a design model. So, if we simply elaborate the analysis model (adding methods, method parameters and return types, fields, etc.) we will most likely get a reasonably good design. However, as we build the design model, we will have many opportunities to *improve* the design.

So, the question becomes, "what makes a good design?"

[Solicit ideas.]

There is one ultimate principle that describes good design, in software as well as almost any other kind of system:

> The simplest solution that solves the problem is generally the best one.

Simplicity has many benefits:

> less code to write, debug, maintain
>
> the system is easier to understand
>
> the system is easier to modify

As we discuss design, we will a number of more specific design principles to help achieve simplicity.

Design Principles
=================

The essential problem of software is that there are an infinite number of ways that we could build a system that works and correctly solves the problem we want to solve. However, many possible designs are needlessly complex, fragile, difficult to understand, etc. Given the challenging environment in which software is developed (limited time/money, changing requirements, etc.) we need to make sure that the systems we design have a simple, flexible design.

There is no automatic way to come up with a "perfect" design.

Instead, what we can do is take an existing design and judge it according to the *principles* of object-oriented design. By doing so, we may find ways to improve the design.

Today, we will talk about some of the important OO design principles. These principles are the product of many years of experience building object-oriented software.

From: [Design Principles and Design Patterns](http://www.objectmentor.com/resources/articles/Principles_and_Patterns.pdf) by [Robert C. Martin](http://www.objectmentor.com/omTeam/martin_r.html) of [ObjectMentor](http://www.objectmentor.com/).

Open/Closed Principle (OCP)
---------------------------

"A module should be open for extension but closed for modification." (from [Martin])

It should be possible to extend the functionality of a module (a component of the system) without changing the implementation of that module.

How is this possible? [Ask.] *Abstract superclasses*.

The idea is that we try to design and implement modules (classes) so that they *use* (call methods on) objects through *abstract classes* and *interfaces*. That way, we can extend the functionality of the module by simply adding new subclasses which add new behavior, instantiating objects which are instances of those subclasses, and passing the objects to the module which uses them through the abstract superclass or interface.

Example:

A video game. The game supports player ship, enemy ship, missile, and power up objects:

> ![image](figures/ocpExample1.png)

If we want to add a new type of visual object to the game, we have to add a new class (not a big problem) and then modify the game module to use it (not so great).

We can observe that there are important commonalities in the way that the game *uses* the visual objects:

> it draws them
>
> it allows them to take turns (one turn per animation frame
>
> etc.

This suggests a better design:

> ![image](figures/ocpExample2.png)

Now, adding new visual objects to the game is as simple as adding a new subclass of Sprite.

Interestingly, there is an important consideration if we are truly to satisfy the Open/Closed Principle. How are the various Sprite objects created? Specifically, can the Game class (or module) create instances of Sprite (or subclasses of Sprite)?

The answer is NO: if the Game module creates subclasses of Sprite directly, then code changes are required to extend Game.

This seems like a dilemma, but we can get around it by observing that we only have a problem if Game *directly* creates Sprites. There is no problem if Game *indirectly* creates Sprites.

So, how could Game *indirectly* create Sprites? [Ask.]

Game can creates *indirectly* if it *delegates* the creation of the Sprites to another object:

> ![image](figures/spriteFactory.png)

The SpriteFactory class is responsible for creating the sprites for each level. It is also not a problem for one Sprite object to create another: for example, a PlayerShip object might create a Missile object when the user fires a Missile.

The idea of using a *factory class* to indirectly create instances of subclasses of an abstract superclass is an example of a *design pattern*. Design patterns are good ideas that help improve designs to more closely follow OO design principles. We will discuss many design patterns as we discuss OO design.

Liskov Substitution Principle (LSP)
===================================

"Subclasses should be substitutable for their base classes." (from [Martin]) Another way of stating this principle is that anywhere in a program that an instance of a superclass may be used, an instance of a subclass is allowed.

This principle is named for Barbara Liskov of MIT, an important researcher in programming languages (particularly OO languages).

This principle is related to the Open/Closed Principle. Specifically, if it is *not* possible to freely use instances of subclasses in modules which use the superclass, then we have not achieved the Open/Closed principle.

Example: is a Square a Rectangle?

In a geometric sense, a square is certainly a rectangle.

However, in an OO sense, it is not necessarily the case that a Square *behaves like* a Rectangle. Consider:

    public class Rectangle {
       ...

       public int getWidth() { ... }

       public int getHeight() { ... }

       public void setWidth(int w) { ... }

       public void setHeight(int h) { ... }
    }

If we make Square a subclass of Rectangle, how will it implement setWidth and setHeight?

> we could have changes to width be reflected in the Square's height, and vice versa, but that violates the contract of the setHeight and setWidth methods (which should only change one dimension of the Rectangle)
>
> we could leave setWidth and setHeight unimplemented for Square objects (i.e., throw an exception when called), but that will certainly surprise clients of the Rectangle class

What this example shows is that we cannot make one class a subclass of another class unless it can truly behave in a way that is consistent with the expectations established by the superclass.

Note that in the case of Rectangle/Square, there is no problem if Rectangles and Squares are *immutable*, meaning their properties are fixed (no setter methods).

[TODO - update to talk about method contracts, allowed scope of changes to contract in subclasses]
