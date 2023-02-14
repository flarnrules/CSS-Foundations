

# CSS - Basic Style Guide

#### *per The Odin Project*

## Table of Contents

1. Learning objectives
2. Basic Syntax
3. Selectors
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

