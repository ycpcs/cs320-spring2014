---
layout: default
title: "Lab 1: Using Git"
---

In this lab, you will practice using [Git](http://git-scm.com/), which is currently the most widely used and arguably the best version control system.

In this course, we will mostly be using [EGit](https://www.eclipse.org/egit/), which is the Git client software built into Eclipse.  This lab will familiarize you with using EGit.

## Before you start

Be aware of the following fact:

<div class="callout">
Git has a bit of a learning curve.
</div>

As with most worthwhile skills, becoming proficient with Git takes some work.  The best advice is to *think carefully* about what you're doing.

Another thing to keep in mind:

<div class="callout">
Git is one of the most awesome and powerful software development tools ever created.
</div>

Like [OO Analysis](../lectures/lecture05.html), Git proficiency is a software development super power.

## Step 1: Create an ssh keypair

Execute the following commands in Cygwin terminal:

::

	export HOME=/cygdrive/h
	ls ~/.ssh

If this command shows the files **id\_rsa** and **id\_rsa.pub**, then you can continue to Step 2.  Otherwise, execute the following commands:

::

	ssh-keygen -t rsa -b 2048

When prompted for a passphrase, just press enter.

## Step 2: Add your public key to your GitHub account

Log into GitHub.  Click on the account settings icon in the top right of the page.  (It looks like a wrench and a screwdriver.)

Click on the **SSH keys** item on the left side of the account settings page.

Click the **Add SSH key** button at the top right of the SSH Keys list.

Enter "YCP" as the title.  In Notepad++, open the file **H:/.ssh/id\_rsa.pub**.  Copy the text in this file, and copy it into the Key textbox.  Then press the **Add key** button.  You might need to enter the password for your GitHub account.

## Step 3: Fork

Log into [GitHub](https://github.com) using your GitHub account.

Go to the following GitHub repository page:

  [https://github.com/daveho/MoveTheSquare](https://github.com/daveho/MoveTheSquare)

Click the **Fork** button.  This will make a clone of this repository in your own GitHub account.  This will be your public repository for this lab.

The repository you just forked contains an Eclipse project called **MoveTheSquare**, a game engine that will be the basis for the next great indie game.  You will just need to add some additional gameplay features!

## Step 4: Configure Eclipse

Start Eclipse.  Choose **Window &rarr; Preferences &rarr;** to open the preferences dialog.

Choose **General &rarr; Network Connections &rarr; SSH2**.  Make sure that **SSH2 home** is set to **H:/.ssh** and also that **Private keys** is set to **id\_dsa,id\_rsa**.

Next, choose **Team &rarr; Git &rarr; Configuration**.  Use **Add Entry...** to create the following configuration entries:

> Setting | Value
> ------- | -----
> user.email | *your email*
> user.name | *your name*
> core.autocrlf | true
> core.fileMode | false

Use appropriate values for *your email* and *your name*. If you would prefer not to reveal your real name and email address, that's fine.

Also note the following:

<div class="callout">
It is <i>extremely</i> important that you set the <b>core.autocrlf</b> setting to <b>true</b>.  If you do not do this, you will experience horrible problems when you try to synchronize your work with your teammates' work.  You will also incur my wrath.  Do not incur my wrath.
</div>

## Step 5: Clone your fork of the repository

In Eclipse, choose the **Git Repository Exploring** perspective.  Click the "Clone a Git Repository and add the clone to this view" button.

In the web page for the repository fork you created in Step 3, copy the **SSH clone URL** and paste it into the **URI** tab of the dialog.  The click **Next** twice and then **Finish**.

Next, choose the **Java** perspective.  Choose **File &rarr; Import... &rarr; Git &rarr; Projects from Git &rarr; Local**.  Select the **MoveTheSquare** repository and click **Next**.  Click **Next** two more times, then click **Finish**.  You should now have a **MoveTheSquare** project in your Eclipse workspace that is connected to your public repository (the fork you created in Step 3).

## Step 6: Make changes

You can run the program by right clicking on **GameView** and choosing **Run As &rarr; Java Application**.

Make some changes to the code:

* change the colors
* make the square bigger or smaller
* use a circle instead of a square
* make the square move faster
* prevent the square from moving outside the boundaries of the window

## Step 7: Commit and push your changes

Once you have made a change, right-click on the **Move The Square** project and choose **Team &rarr; Commit**.  Enter a log message describing your changes.

Next, right-click on **Move The Square** and choose **Team &rarr; Push**.

If the push succeeds, you should be able to refresh your GitHub repository web pages and see the commit you just made.

## Step 8: Fetch and merge changes from other people

Refer to the [Fetch/Merge](../resources/fetchMerge.html) document for instructions on how to set up remote tracking branches to track the changes made by other people.

Find someone in the class whose changes you want to fetch and merge.

Using the Eclipse Git Repository Exploring perspective, configure a *remote* for that person's public repository.  Then return to the Java perspective and fetch changes from the remote.  Finally, merge changes from the remote tracking branch containing the changes you fetched.

### Merge conflicts

If a merge does not cause any conflicts &mdash; meaning that the changes you merged did not make edits to any parts of the code that you edited in your changes &mdash; the merge succeeds and the result of the merge is committed to your private repository.

If the merge does cause conflicts, Eclipse will notify you and place a red conflict icon on all directories and files where conflicts occurred.  Eclipse will also add *conflict markers* in the source code to show you precisely where conflicts occurred, and to indicate what the conflicting text in each conflicting change was.  You will need to edit the code to remove the conflict markers and resolve the markers.

Once you have resolved a conflict, right-click on the file and choose **Team &rarr; Add** to indicate that the contents of the file have been restored to a consistent state.

Once all conflicts are resolved, you can commit the result of the merge.

<div class="callout">
Resolving merge conflicts is the most difficult part of using version control.  <b>Be careful</b> not to arbitrarily remove anyone else's code when you resolve a merge conflict.  If you are not sure what to do when a merge conflict occurs, <b>ask me for help</b>.
</div>

If you see a merge conflict where a conflict marker shows a conflict between two identical or nearly-identical versions of the entire file, it means that you or someone you fetched changes from did not set the **core.autocrlf** property to **true**.  If that happens,

<div class="callout">
<span style="font-size: 200%;"><i>Prepare to experience my wrath!</i></span>
</div>

### Pushing following a merge

Once a merge has been completed, you should to a push so that your public repository is updated with the results of the merge.

<!-- vim:set wrap: ­-->
<!-- vim:set linebreak: -->
<!-- vim:set nolist: -->
