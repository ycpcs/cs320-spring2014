---
layout: default
title: "Lecture 3: Requirements, Use Cases"
---

Requirements
============

Requirements are what the software must do.

Specifically: a requirement is a singular need which must be satisified for the system to work correctly.

E.g., an ATM must allow a customer to withdraw money from his/her account.

Issues:

-   gathering requirements: requires interacting with the customer

    -   customers aren't always that great at telling you what they want
    -   sometimes if you build exactly what they want, they'll want something different

-   documenting requirements
-   making sure requirements are satisfied

    -   need to make sure that requirements have been addressed
    -   in a large system, with many requirements, this requires attention to detail

Use cases
=========

Use cases are a way of describing how the system will satisfy its requirements.

A use case shows a scenario where one or more actors use the system.

Properties of a use case:

-   The use case has a name describing what the scenario accomplishes. (E.g., "play a game of TicTacToe".)
-   The actors are agents external to the system. They might be human users. Or, they could be other software systems.
-   An actor must be an initiator of the use case. In other words, the scenario described by the use case must be a response to an actor requesting that the system do something to achieve the initiator's goal.
-   The use case has a well-defined beginning and end. The end of the use case is the achievement of a goal (normal/expected outcome), or possibly an error.

Note that although the use case will generally specify a sequence of steps, these steps must focus on WHAT the actor or actors experience, and NOT how the system achieves the functionality. So, the use case must not mention objects, methods, code, etc. The use case should also not describe the user interface: that is a separate activity.

There may be multiple paths through a use case. For example: if an error occurs, or if there is "optional" behavior seen in some cases, etc.

There are different ways of writing a use case. For some use cases, a single sentence might suffice. For more fully-specified use cases, listing a series of numbered steps is a good approach. The format described in the HFOOA&D book is a good one. As with any documentation, diagram, model, etc., the purpose is the specify an aspect of the system in enough detail to be useful, but not too much detail. Excessive detail is a waste of time.

Example: Automated Teller Machine

Who are the actors? [Ask for suggestions.]

-   Customer
-   Bank system (this is software, but it is external to the ATM system, so it's considered an actor)
-   Bank employee who adds cash, collects deposits, etc.

What are some of the requirements?

-   customers can access their accounts (withdraw, deposit, check balance, etc.)
-   the system is secure (only authorized users can use)
-   etc.

What are some scenarios in which the ATM system is used?

-   withdrawal
-   deposit
-   check balance
-   stock with cash
-   etc.

[Pick a scenario. Solicit ideas to construct a use case.]

What requirement or requirements did this use case address?
