<!--
Creator: Baseline curriculum
Editor: Ben Hulan and ZebGirouard
Market: DEN
-->

![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png)

<!--9:00 5 minutes -->

<!--Schedule is tight this day. Stick close to times. -->

# CSS Selectors Basics
<!--
**Hook:**

http://www.sportsmanssupplyco.com/

How would everyone fix this site?

Most of these things are changeable with CSS Selectors
-->

## Why is this important?
After this workshop, developers should be able to hand code a simple website from scratch with HTML and CSS. Generally, nobody really starts from scratch anymore. However, this should solidify your conceptual model of how these things go together and improve your specific knowledge of some fundamental CSS properties so you can debug CSS more quickly.

## Objectives
*After this lesson, students will be able to:*

- **Describe** the syntactical and functional relationship between selectors, properties, and values
- **Style** all elements of a particular HTML element on a web page
- **Describe** the difference between class and id selectors
- **Apply** styles to specific elements by selecting elements with classes and ids
- **Apply** a set of styles to children of a specific class or tag
- **Change** the style of a specific element using an inline style


## Preparation

*Before this lesson, students should already be able to:*

- **Write** basic HTML
- **Use** a text editor

## What is CSS?

If HTML is a set of instructions telling the browser what to display, CSS tells it how to display it. It's the **Adjectives** to our HTML **nouns**.

CSS stands for:

- **C**ascading
- **S**tyle
- **S**heet

It provides the browser with precise instructions on how to style each element we want displayed on the page and can affect the text format - like font, size, color - the size and position of various objects on the page, colors, spacial layouts, etc. There are literally hundreds of different properties we can use to style HTML elements on a webpage.
<!--
**CFU:**
Fist-to-five (before): How comfortable would you be implementing styles in your webpage?
-->

<!--9:05 20 minutes -->

## Let's write some CSS!

<!--**Reiterate half-mast concept**-->

Create a new folder with a HTML page:

```bash

$ mkdir css-basics
$ cd css-basics
$ touch index.html

```

First, add a basic HTML structure to your `index.html` file:

```html

 <!DOCTYPE>
 <html>
   <head>
     <title>Intro to CSS</title>
   </head>
 <body>
 </body>
 </html>
```

<!-- Half-mast break (catch up) -->

## Adding CSS

There are three different ways to use CSS to style your HTML:

- Inline style
- Style Sheet: Internal
- Style Sheet: External


Let's take a look at each one:

<!--Demo Inline CSS and Internal Stylesheet with devs at half-mast -->

### Inline Style

Style rules can be added directly to an element with a `style` attribute. However, we're going to reserve this method for JavaScript DOM manipulation. Using it for anything else is frowned upon, as it leaves your code sloppy, repeatative, and hard to update.

To use inline styles, add the style attribute to the relevant tag. The style attribute can contain any CSS property. The example shows us changing the HTML body's background to azure:

```html

 <!DOCTYPE>
 <html>
   <head>
     <title>Intro to CSS</title>
   </head>
   <body style="background:azure;">
   </body>
 </html>
```

### Style Sheets - Internal and External

Style sheets can be written in your HTML (internal) or in a separate CSS file (external).  Whatever style sheet you use, the CSS syntax is the same. We build our CSS with a selector - usually the name of the HTML tag, a specific class of elements, or an element with a unique ID:

```css
selector {
  property_1: value_1;
  property_2: value_2;
}

```

Do not forget the curly brackets or the semi-colon after the value!

#### Internal Style Sheets

If a _single page_ has a unique style, you could use an internal style sheet - these are defined and written in your HTML using the `<style>` element, inside the head section of an HTML page:

```html

 <!DOCTYPE>
 <html>
   <head>
   <style>
    body {
      background: black;
    }
   </style>
     <title>Intro to CSS</title>
   </head>
 <body>
 </body>
 </html>

```

Just like before, if you open the `index.html` with your browser, you'll notice the body background has changed. We've selected the body element and instructed the browser to color it black.
While very easy to implement, this method is also frowned upon unless you have a very specific reason for doing so.

#### External Style Sheets

This is the preferred method for writing CSS. With just one file - your external style sheet - you can modify the styles of your entire website. It's extremely powerful, and helps keep your code organized and separate.

First, we'll create a css file. We often have a specific folder for stylesheets, since we can have several in one application - so we'll put this in a `/css` folder:

```bash

mkdir css
touch css/style.css

```

To link our stylesheet to our HTML, we have to call it into our`index.html` file. Inside the `<head>` tags, we need to add a self-closing `<link>` tag, indicating the type of relations (`rel="stylesheet"`) and the file path: 


```html
 <!DOCTYPE>
 <html>

   <head>
     <title>Intro to CSS</title>
   <link rel="stylesheet" href="css/style.css">
   </head>

   <body>
   </body>
 </html>

```

Now any CSS we write in our `style.css` file will show up on our `index.html` page!

### Try it Out!

Let's add some more html to our index.html:


```html

 <!DOCTYPE>
 <html>

   <head>
     <title>Intro to CSS</title>
   <link rel="stylesheet" href="css/style.css">
   </head>


   <body>
     <p>This is a paragraph element</p>
     <div>This is a DIV</div>
     <div>This is another DIV</div>
   </body>

 </html>
```

Now, let's add the CSS we had - plus some more - to our stylesheet file:

```css

body {
  background: azure;
}

p {
  color: orange;
}

div {
    border-width: 1px;
    border-style: solid;
    border-color: black;
}

```

<!--Already 9:28 (9:03 start) here -->

<!-- Half-mast break - put this up on projector, split HTML/CSS screens, NO COPY-PASTE-->

Our body rule is still applied, and these new rules will change the color of all paragraph tags to have the font-color "orange" and add a 1px black border to each DIV on the page, since the selector targets the "div" elements.  Refresh your browser and check it out.

Luckily for us, CSS gives us some nice shortcuts that we'll go over throughout this lesson, and we can combine the `div` border styles into this:

```css

  border: 1px solid black;
  /*border-width: 1px;
  border-style: solid;
  border-color: black;*/
```

Notice, we can comment out CSS with `/* your css */`.

<!--Devs try that out -->

<!-- 9:25 10 minutes -->

<!--Get two-column table on board: one with "class" heading, one with "ID" heading -->
<!--Half-mast for this whole demo -->

## Classes and IDs

You can add a `class` or `id` to any HTML element to style it in your external CSS:

```html

    <div id="header">My Header</div>

    <div class="paragraph">My Paragraph</div>

```

But there's a big difference between the two. It's important to know when to use them.

#### The Class Selector

Classes are used to denote HTML elements **that share similarities**. For instance, there's different classes of cars - like SUVs, vans, and trucks. All trucks are not identical, but they share enough similarities that we can easily  classify them when we see them. In the same way, you'll use CSS classes to group objects that are visually similar, so that you update their appearance in only one place.

<!--Whip-around for this while instructor writes on board -->

- Classes are **NOT** unique
- You can use the same class on multiple elements
- You can use multiple classes on the same element
- You can select a class using `.class-name {}`

Watch me add some HTML to our index.html and then style those elements by selecting the classes associated with them:

```html
<!DOCTYPE>
<html>
  <head>
  <title>Intro to CSS</title>
  <link rel="stylesheet" href="css/style.css">
  </head>

  <body>
    <p>This is a paragraph element</p>

    <div>This is a DIV</div>
    <div>This is another DIV</div>

    <div class="comments">
        Hello
    </div>

    <div class="comments">
        Hello
    </div>

    <div class="comments">
        Hello
    </div>

  </body>

</html>

```

Now, for the style:

```css

body {
  background: azure;
}

p {
  color: indigo;
}

div {
  border: 1px solid black;
}

.comments {
    font-weight: bold;
    color: #64FE2E; /* green */
}
```

If I refresh my browser (`cmd + R`), I see the updates.  The browser selects all elements on the page with the `comments` class and alters the font-weight and color.

#### The ID Selector

IDs are used to denote HTML elements that are **unique**. An ID can only be used once in an HTML page, and should be reserved for extremely specific content.

<!--Whip-around while writing -->

- An ID is **unique** within a page.
- You should use an id selector when you want to find a single, unique element.
- In the CSS document, you use a hashtag (#) to denote an ID.

How about we try it out?  Altering the HTML:

```html

<!DOCTYPE>
<html>
  <head>
  <title>Intro to CSS</title>
  <link rel="stylesheet" href="css/style.css">
  </head>

  <body>
    <p>This is a paragraph element</p>

    <div>This is a DIV</div>
    <div>This is another DIV</div>

    <div class="comments">
        Hello
    </div>

    <div class="comments">
        Hello
    </div>

    <div class="comments">
        Hello
    </div>

    <div class="comments" id="dolphin">
        I am a dolphin
    </div>

  </body>

</html>

```

And now the style:

```css

body {
  background: azure;
}

p {
  color: indigo;
}

div {
  border: 1px solid black;
}

.comments {
    font-weight: bold;
    color: #64FE2E;
}

#dolphin {
    font-style: italic;
    color: #0040FF;
}
```

Sweet!

<!--
**CFU:**
Fist-to-five (after): How comfortable would you be implementing styles in your webpage?
-->

<!--9:35 10 minutes -->

## Style using Classes and IDs - Independent Practice

Create a new directory with an `index.html` and `styles.css` file inside. Using what we've done in class, see how far you can get through these exercises:

- make an unordered HTML list of the following animals:  

    - mouse  
    - canary  
    - penguin  
    - salmon  
    - cat  
    - goldfish  
    - dog  
    - sheep  
    - parakeet  
    - tuna  

- make all the mammals pink, all the birds blue, and all the fish orange using CSS classes
- apply the following colors to the list using IDs:

    - mouse = gray
    - penguin = black
    - goldfish = gold  

- add the following background colors to your existing classes:
    - mammal = lavenderBlush
    - bird = lightGray
    - fish = lightYellow

<!--9:45 10 minutes -->

<!--Just Demo-->

## Multiple classes and multiple elements

You can also chain classes together, applying several classes to one element:

Let's add:

```html

<!DOCTYPE>
<html>
  <head>
  <title>Intro to CSS</title>
  <link rel="stylesheet" href="css/style.css">
  </head>

  <body>
    <p>This is a paragraph element</p>

    <div>This is a DIV</div>
    <div>This is another DIV</div>

    <div class="comments">
        Hello
    </div>

    <div class="comments">
        Hello
    </div>

    <div class="comments">
        Hello
    </div>

    <div class="comments" id="dolphin">
        I am a dolphin
    </div>

    <div class="comments first second">
        Multiple classes
    </div>

  </body>

</html>

```

Then, create two classes:

```css
body {
  background: azure;
}

p {
  color: indigo;
}

div {
  border: 1px solid black;
}

.comments {
    font-weight: bold;
    color: #20B2AA;
}

#dolphin {
    font-style: italic;
    color: #FF69B4;
}

.first {
  font-size: 40px;
}

.second {
  color: MidnightBlue;
}
```

As we can imagine, the possibilities are endless. There are many properties and values to work with and many ways to target specific elements. Two pages could have the same HTML content, and yet look dramatically different due to different CSS stylesheets.

We can even use classes/IDs with elements to select and style HTML. Lets add a short unordered list:

```html
<!DOCTYPE>
<html>
  <head>
  <title>Intro to CSS</title>
  <link rel="stylesheet" href="css/style.css">
  </head>

  <body>
    <p>This is a paragraph element</p>

    <div>This is a DIV</div>
    <div>This is another DIV</div>

    <div class="comments">
        Hello
    </div>

    <div class="comments">
        Hello
    </div>

    <div class="comments">
        Hello
    </div>

    <div class="comments" id="dolphin">
        I am a dolphin
    </div>

     <div class="comments first second">
        Multiple classes
    </div>

     <ul>
        <li class="why" >Why a dolphin?</li>
        <li class="why" id="not">Why not?</li>
     </ul>

  </body>

</html>
```

Imagine, we wanted a particular style to apply to all of the elements from the list but wanted other particular styles to apply to each item, individually. Definitely doable. Take a look at our CSS:

```css
body {
  background: azure;
}

p {
  color: indigo;
}

div {
  border: 1px solid black;
}

.comments {
    font-weight: bold;
    color: #20B2AA;
}

#dolphin {
    font-style: italic;
    color: #FF69B4;
}

.first {
  font-size: 40px;
}

.second {
  color: MidnightBlue;
}

li {
  text-align: center;
  font-style: italic;
  color: Tomato;
}

li.why {
  font-family: sans-serif;
  font-size: 16px;
}

li#not {
  font-family: serif;
  font-size: 36px;
}
```

Now, all our list items are centered but the top item has a different font than the bottom. What styles were inherited? What was overwritten?

<!--9:55 5 minutes -->

## Specificity in CSS - Intro

One of the most important concepts with CSS is specificity. Imagine you select an element by its class and give it some style; then, on the next line, you select the same element by its element name and its ID - how does the browser know what style to apply?  Well, every element gets a score and it's this score that dictates what CSS property is applied.

[Specificity Calculator](http://specificity.keegan.st/)

Every selector has its place in the specificity hierarchy, and if two selectors apply to the same element, the one with higher specificity wins.  Overall, there are four distinct factors that define the specificity level of a given selector: inline styles, IDs, classes+attributes and elements.  You can calculate CSS specificity with the CSS Specificity Calculator:

<img src="https://css-tricks.com/wp-content/csstricks-uploads/specificity-calculationbase.png" style="width: 400px;" />

### Calculating specificity

<img src='https://css-tricks.com/wp-content/csstricks-uploads/cssspecificity-calc-1.png' style="width: 400px;" />

*This is calculated as 0113*

<img src='https://css-tricks.com/wp-content/csstricks-uploads/cssspecificity-calc-2.png' style="width: 400px;" />

*This is calculated as 0023*

<img src='https://css-tricks.com/wp-content/csstricks-uploads/cssspecificity-calc-4.png' style="width: 400px;" />

*This is calculated as 1000*

A couple of rules to think about:

- If two selectors apply to the same element, the one with higher specificity wins
- When selectors have an equal specificity value, the latest rule is the one that counts
- More specific selectors beat less specific ones
- id specificity > class specificity > tag specificity
- Inline styles > Internal styles > External styles
- !important trumps all of the above.

<!--10:00 5 minutes -->

## Conclusion

![](images/css.gif)

CSS can be really fun or a total nightmare. You have to remember a few rules, but once you have them memorized, it's great to see your webpage come to life as you imagined.

<!--Think-pair-share -->

- Describe the differences between classes and IDs.
- Identify the popular CSS properties we used today.
- What are the use cases for inline styling vs. internal/external style sheets?

## Additional Practice Exercises

### Using CSS to select class and id attributes

Go back to your code from the previous independent practice problem and continue to work through these exercises:

- make the mammals bold
- make the birds italic
- make the fish underlined

- create a new unordered list add a list item for each the following plants:

    - Dogwood Tree
    - Oak Tree
    - Saguaro
    - Kelp
    - Venus Fly Trap
    - Ent

- give all `ul`s a border with a width of 3 pixels, a color of plum, and a style of dotted. Also, give them a border radius of 5px.
- give all `li`s a top border of 3 pixels, a color of seagreen, and a style of solid.

## Licensing
All content is licensed under a CC­BY­NC­SA 4.0 license.
All software code is licensed under GNU GPLv3. For commercial use or alternative licensing, please contact legal@ga.co.
