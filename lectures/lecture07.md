---
layout: default
title: "Lecture 7: HTML and CSS"
---

HTML
====

HTML and its companion language CSS form the markup language used to render web resources for people (rather than programs). HTML/CSS allow text and images to be styled and formatted in a way that is meaningful to human users.

Hello, world in HTML
--------------------

    <!DOCTYPE html>

    <html>
        <head>
            <title>Hello, world!</title>
        </head>

        <body>
            Hello, world!
        </body>
    </html>

[Link](lecture07/hello.html)

Try saving this in a text file with a **.html** file extension and then open it in a web browser.

HTML documents are trees of elements
------------------------------------

An HTML document is a tree of elements. Each element is delimited by a *start tag* and an *end tag*. Each tag can contain an arbitrary number of children. Each child is either text or an element.

In the **Hello, world** document, the parent element is **html**. It has two children, **head** and **body**. The **head** element has a child element, **title**. The **body** element has one child, which is text (the string **Hello, world!**). You will see this basic structure (**html**, **head**, **body**) in all HTML documents. The **head** element contains *meta-information* about the document, such as its title. The **body** contains the elements that the user sees in the body of the web page.

The tree of elements is known as the **Document Object Model**, or **DOM**.

It looks boring: how do I jazz it up?
-------------------------------------

Because HTML is a visual medium, it can use colors, fonts, and layout to convey information more effectively.

*CSS*, the *Cascading Style Sheet* language, allows visual properties to be associated with HTML elements. Using CSS, you can control the font, color, and position of each element.

Each HTML document can have one or more CSS stylesheets associated with it. A CSS stylesheet uses *selectors* to match elements in the HTML document and set CSS properties which control things like font, color, size, etc.

Modified version of Hello, world:

[Link](lecture07/helloJazzy.html)

In this version, we used a selector which matches the **body** element and used it to change the size, color, and background color of the body element.

Note that normally we don't embed CSS rules directly in the HTML document, but instead save them in a separate file. This makes it easier to apply a common set of CSS rules to a number of documents, in order to give those documents a common visual appearance. However, for testing purposes, you can put them in the **style** element within the **head** element.

divs and spans
--------------

Any interesting HTML document doesn't just contain an undifferentiated mass of text. Instead, the text will be broken up to form a logical structure. The **div** and **span** elements help you to define this structure.

A **div** element is a "block" of text: basically, a paragraph. A **span** element is a linear sequence of text: basically, a sentence (or part of a sentence).

Let's say we're going to make a website to display items (kinds of fruit) we have in our inventory database. We'll want to display a page describing each item. Each item page will contain several distinct sections:

-   the name of the item
-   a picture of the item (you can display images in an HTML document)
-   the description of the item
-   information about the vendor which supplies the item

Example HTML:

    <!DOCTYPE html>

    <html>
        <head>
            <title>Mangoes</title>
        </head>

        <body>
            <div id="itemName">
                Mangoes
            </div>

            <div id="itemPicture">
                <img src="mango.jpg" />
            </div>

            <div id="itemDescription">
                Mangoes are a delicious tropical fruit.
                They are pink/orange in color and have a
                delightful fragrance.  Werewolves and vampires
                both shun mangoes, but they have no effect on
                zombies.
            </div>

            <div id="itemVendor">
                Supplied by FruitCo, Inc.
            </div>
        </body>
    </html>

[Link](lecture07/item-mangoes.html)

Notice that each **div** element in the HTML has an **id** attribute. An **id** attribute is a way to assign an "identity" to an element so that it can be styled with a CSS rule. This is an example of *semantic markup*: we are using **div**s and element ids to specify the *meaning* of the HTML content, without specifying how that content should be presented.

Clean separation of semantic content and presentation (visual appearance) is important, because it allows the developers who work on the functionality of a website to work largely independently of the visual designers who define the layout and appearance of the website.

A CSS selector can match an element by its **id** attribute:

[Link](lecture07/item-mangoes-styled.html)

What happened? We appled the **float: left** CSS property to the first two divs, arranging them from left to right (rather than stacking them vertically as is the default for **div** elements). Applying the **clear: both** property to the **itemDescription** element causes it to be placed below the previous elements (otherwise, the browser would attempt to flow this element's contents around the floated elements.) Visual styles are applied to the divs in order to give each one a distinct appearance.

Element classes
---------------

A limitation of using **id** attributes is that elements cannot share the same id. So, CSS rules that select an element by an id can only apply to one element.

A *class* is a way of designating an arbitrary number of elements as sharing some common semantic property. For example, we might want distinguish company names from other text. Consider the following document:

    <!DOCTYPE html>

    <html>
        <head>
            <title>Companies I like</title>
        </head>

        <body>
            <div class="rant">
                I like <span class="companyName">Google</span>.  I'm not as fond
                of <span class="companyName">Microsoft</span>.
            </div>

            <div class="rant">
                Don't ask me about <span class="companyName">Apple</span>
                or <span class="companyName">Blackboard</span>.
            </div>
        </body>
    </html>

[Link](lecture07/companyNames.html)

A version in which the company names are styled differently than the surrounding text (and we also add a margin above/below the divs):

[Link](lecture07/companyNames-styled.html)
