

# CSS - Basic Style Guide

#### *per The Odin Project*

## Table of Contents

1. Learning objectives
2. Basic Syntax
3. Common Selectors
    1. Universal Selector
    2. Type Selectors
    3. Class Selectors
    4. ID Selectors
    5. Grouping Selector
    6. Chaining Selectors
    7. Descendant Combinator
    
4. Properties to Get Started With
    1. Color and Background-Color
    2. Typography Basics and Text Align
    3. Image Height and Width

5. The Cascade of CSS
    1. Specificity
    2. Inheritance
    3. Rule Order

6. Adding CSS to HTML
    1. External CSS
    2. Internal CSS
    3. Inline CSS


## 1 Learning Objectives

1. Add styles to HTML with CSS
2. Understand how to use the class and ID attributes
3. Add styles to specific elements using the correct selectors.
4. Understand what the cascade does.

## 2 Basic CSS Syntax

At it's most basic level, CSS works like this:

    selector {
        property1: value1;
        property2: value2;
        property3: value3;
    }


The below diagram outlines the basic syntax for CSS

![Alt text](https://cdn.statically.io/gh/TheOdinProject/curriculum/05ce472eabf8e04eeb2cc9139e66db884074fd7d/foundations/html_css/css-foundations/imgs/00.jpg)

> ### Side note on `<div>`
>
> A `<div>` is one of the basic HTML elements. It is an empty container. Generally we want to use other elements like `<h1>` or `<p>` for content, but sometimes you will just need a container. In The Odin Project we will use plain `<div>`s to start, but later we will go into more detail.

## 3 Selectors

Selectors refer to the HTML elements to which CSS rules apply; they're what's being "selected for each rule. Below are a few selectors that might get used a lot by everyone, so good to start for beginners:

### Common Selector 1 - ***The Universal Selector***

The universal selector will select elements of any type, hence the name "universal", and the syntax to call it is simply *

```css
* {
    color: purple;
}
```

### Common Selector 2 - ***Type Selectors***

A type selector (otherwise known as an element selector), will select all elements of a given element type, and the syntax is just the name of the element:

```html

<!-- index.html -->

<div>Hello, World!</div>
<div>Hello, again!</div>
<p> Hope you are having a *fiiine* day</p>
<div>You too pal!</div>

```

```css

/* styles.css */

div {
    color: white;
}

```

Up above, the three `<div>` elements are being selected, while the `<p>` elements are not.

### Common Selector 3 - ***Class Selectors***

Class selectors will select all elements with the given class, whcih is an attribute you can place on an HTML element. You can add a class to an HTML tag and select in in CSS like this:

```html
<!-- index.html -->

<div class="alert-text">
    Please agree to our terms of service.
</div>
```
```css
/* styles.css */

.alert-text{
    color: red;
}
```
Syntax for class selectors is a period immediately followed by the case-sensitive value of the class attribute. Classes aren't required to be unique, so the same class can be used on multiple elements.

Multiple classes can be added to to a single element with a space separated list, such as `class="alert-text severe-alert"`, where the space designates a second class selector. Never use spaces when declaring classes, use hyphens instead.

### Common Selector 4 - ***ID Selector***

ID selectors are similar to class selectors. They select an element with a given ID, which is another attribute that can be placed on an HTML element.

```html
<!-- index.html -->

<div id="title">My Awesome 90's Page</div>
```
```css
/* styles.css */

#title {
    background-color: red;
}
```

Instead of a period, for ID selectors we use a hashtag `#` immediately followed by the case-sensitive value of the ID attribute. One common pitfall of ID selectors is overuse of the ID attribute when it isn't needed. Classes typically can get the job done. IDs should be used **sparingly**.

The main difference between an ID and a class is that an element can only have **one** ID, but an element can have **multiple** classes. An ID cannot be repeated on a page, and the ID attribute should not contain any whitespace.

### Common Selector 5 - ***Grouping Selector***

What if we have two groups of elements that share some of the same style declarations?

```css

.read {
    color: white;
    background-color: black;
    /* several unique declarations */
}

.unread {
    color: white;
    background-color: black;
    /* several unique declarations */
}
```

In the styles above, both `.read` and `.unread` selectors share the `color: white;` and `background-color: black;` declarations, but otherwise have a bunch of unique declarations. To cut down on repetition, we can group these two selectors together as a comma-separated list:

```css

.read,
.unread {
    color: white;
    background-color: black;
}

.read {
    /* several unique declarations */
}

.uread {
    /* several unique declarations */
}
```
The above solution makes it easier to edit the `color` and `background-color` for both classs at once.

### Common Selector 6 - ***Chaining Selectors***

Another way to use selectors is to chain them as a list without any separation. For example, with the following html:

```html
<div>
    <div class="subsection header">Latest Posts</div>
    <p class="subsection preview">This is where a preview for a post might go</p>
</div>
```
There are two elements with the `subsection` class that need some unique styles, but lets say we want to apply a single rule to the element that has `header` as a second class. In order to do this, we can *chain* both the class selectors together in CSS like this:

```css

.subsection.header {
    color: red;
}
```

The above code has `.subsection.header` selecting any element that has both the subsection *and* `header` classes. Works for any combination of selectors, except for chaining more than one type selector.  

This can be used to chain a class and an ID, like below:

```html
<div>
    <div class ="subsection header">Latest Posts</div>
    <p class="subsection" id="preview">This is where a preview goes. </p>
</div>
```
In css you take the two elements above (subsection header and preview) and style them like this:

```css
.subsection.header {
    color: red;
}

.subsection#preview {
    color: blue;
}
```
In general, you can't chain more than one type selector, since an element can't be two different types at once. For example, chaining two type selectors like `div` and `p` would give us the selector `divp`, which wouldn't work since the selector would try and find something called <divp> which doesn't exist.

### Common Selector 7 - ***Descendant Combinator***

Combinators allow us to combine multiple selectors differently than grouping or chaining them. They show a relationship between selectors. There are *four* types of combinators. The **Descendant Combinator** is one of them.

A **descendant combinator** will only cause elements that match the last selector to be selected if they also have an ancestor (parent, grandparent, etc) that matches the previous selector.  

Something like `.ancester .child` would select ane lement with the class `child` if it has an ancestor with the class `ancestor`. Alternatively said, `child` will only be selected if it is nested inside of `ancestor`, no matter how deep.

```html
<div class="ancestor"> <!-- A -->
    <div class="contents"> <!-- B -->
        <div class="contents"> <!-- C -->
        </div>
    </div>
</div>

<div class="contents"></div> <!-- D -->

```
```css
.ancestor .contents {
    /* some declarations */
}
```

The above css would be selecting B and C, but would not be selecting D. Another example:

```html
<div class="one">
    <div class="two">
        <div class="three">
        </div>
    </div>
</div>
```
```css
.one .three {
    /* some properties */
}
```
The combinator `.one .three` is saying to select an element with a class of three, only if it has an ancestor with a class of one.

## 4 Properties to Get Started With

ThIis chapter provides a list of properties to start using:
1. Color and background-color
2. Typography basics and text align
3. Image height and width

### 1 Color and Background Color

Both `color` and `background-color` can accept one of several kinds of values. A keyword (like `red` or `transparent`), HEX, RGB, HSL values. Also RGBA (alpha channel is transparency). HSL stands for (hue, saturation, lightness).

A color guide: https://www.w3schools.com/cssref/css_colors_legal.php

Here are some good colors:
https://www.w3schools.com/colors/colors_names.asp

- AliceBlue
- Aquamarine
- BlueViolet
- Chartreuse
- Crimson
- DarkRed
- Dark Salmon
- DeepSkyBlue
- Gold
- LemonChiffon
- LightGreen
- LightYellow
- OldLace
- PapayaWhip
- SeaShell
- HoneyDew
- Ivory

### 2 Topography Basics and Text Align

`font-family` can be a single value or a comma-separated list of values that determine the font used by an element. Each font falls into two categories:

1. "font family name" like `"DejaVu Sans"` (quotes used because of whitespace)

2. "generic family name" like `sans-serif` (usually no quotes)

If a browser cannot find or doesn't support a font, it will use the next one in the list, then the next one, and so on as fall backs.  It's best practice to provide a list of values for this property, starting with the first font, and then ending with a generic family as a fallback. Example: `font-family: "DejaVu Sans", sans-serif;`

`font-size` affects the size of the font. You cnan say stuff like: 22px, 12px, 30px.

`font-weight` affects the boldness of text. Assuming that the font supports the specified weight. We can use a keyword like `bold` or numeric values beteen 1 and 1000, usually in increments between 100 and 900.



