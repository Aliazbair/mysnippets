---
title: flexBox
slug: css-flexbox
excerpt: CSS Flexbox is a layout mode in CSS that provides a more efficient way to lay out, align and distribute space among items within a container, even when their size is unknown and/or dynamic.
date: 2023-01-20
author: ali
image: '../../../logo.png'
---

CSS Flexbox is a layout mode in CSS that provides a more efficient way to lay out, align and distribute space among items within a container, even when their size is unknown and/or dynamic.

Here's a simple example of how to use CSS Flexbox:

HTML:

```html
<div class="container">
  <div class="item item-1">1</div>
  <div class="item item-2">2</div>
  <div class="item item-3">3</div>
</div>
```

CSS:

```css
.container {
  display: flex;
  justify-content: space-between;
  align-items: center;
  height: 200px;
}

.item {
  width: 30%;
  height: 50px;
  background-color: lightblue;
  text-align: center;
  line-height: 50px;
  color: white;
}
```

In this example, the .container is set to display: flex to make it a flex container. The justify-content property is set to space-between which distributes the items evenly within the container, while also adding equal space between the items. The align-items property is set to center, which centers the items vertically within the container.

The items are set to width: 30% and height: 50px with a lightblue background color and centered text. The line height is also set to 50px to vertically center the text within the item.

This is just a basic example of what you can do with CSS Flexbox, but it's a powerful tool that can be used to create complex and responsive layouts.

key concepts and properties of CSS Flexbox:

Flex Direction: Defines the direction of the flex items in a flex container. The default value is row, which aligns the items horizontally from left to right. Other values include row-reverse, column, and column-reverse.

Flex Wrap: Defines whether flex items should wrap or not if they don't fit within the container. The default value is nowrap, but you can also set it to wrap or wrap-reverse.

Flex Flow: A shorthand property for setting both flex-direction and flex-wrap in a single line.

Justify Content: Defines how flex items are positioned along the main axis (horizontally for row direction, vertically for column direction). Possible values include flex-start, flex-end, center, space-between, space-around, and space-evenly.

Align Items: Defines how flex items are positioned along the cross axis (vertically for row direction, horizontally for column direction). Possible values include flex-start, flex-end, center, baseline, and stretch.

Align Content: Defines how the space between lines of a multi-line flex container is distributed. Possible values are similar to justify-content, including flex-start, flex-end, center, space-between, space-around, and stretch.

Flex Grow: Defines the proportion of free space that a flex item should take up within a container. The default value is 0, but you can set it to any positive number to determine the item's relative size compared to other items in the container.

Flex Shrink: Defines the proportion by which a flex item should shrink relative to the rest of the items if the container is smaller than the total size of the items. The default value is 1.

Flex Basis: Defines the default size of a flex item before any remaining space is distributed according to flex-grow and flex-shrink. The default value is auto, but you can set it to a specific length, percentage, or the keyword content.

These are some of the key concepts and properties of CSS Flexbox, but there is much more to learn and explore. I hope this has been helpful in getting you started with CSS Flexbox.

more examples of how to use CSS Flexbox:

## Example 1: Flex Container with Equal Height Items:

```html
<div class="container">
  <div class="item">Item 1</div>
  <div class="item">Item 2</div>
  <div class="item">Item 3</div>
</div>
```

```css
.container {
  display: flex;
  flex-wrap: wrap;
}

.item {
  flex: 1;
  height: 100px;
  background-color: lightblue;
  text-align: center;
  line-height: 100px;
  color: white;
  margin: 10px;
}
```

In this example, the .container is set to display: flex to make it a flex container. The flex-wrap property is set to wrap so that the items will wrap to the next line if the container is too small to fit them all on one line.

The .item class is given a flex value of 1, which means that each item will take up an equal amount of the available space. The height is set to 100px and the line height to 100px to vertically center the text within the item. The items are given a 10px margin to create space between them.

## Example 2: Flex Container with Vertically Centered Items:

```html
<div class="container">
  <div class="item">Item 1</div>
  <div class="item">Item 2</div>
  <div class="item">Item 3</div>
</div>
```

```css
.container {
  display: flex;
  height: 200px;
  align-items: center;
}

.item {
  width: 30%;
  height: 50px;
  background-color: lightblue;
  text-align: center;
  line-height: 50px;
  color: white;
  margin: 10px;
}
```

In this example, the .container is set to display: flex to make it a flex container. The height property is set to 200px to give the container a defined height. The align-items property is set to center, which centers the items vertically within the container.

The .item class is given a width of 30% and a height of 50px with a lightblue background color and centered text. The line height is also set to 50px to vertically center the text within the item. The items are given a 10px margin to create space between them.

These are just a few more examples of how to use CSS Flexbox, but the possibilities are endless. With CSS Flexbox, you can create complex and responsive layouts with ease.

## create a navigation bar using CSS Flexbox:

```html
<header class="navbar">
  <div class="logo">Logo</div>
  <nav class="nav-links">
    <a href="#">Home</a>
    <a href="#">About</a>
    <a href="#">Contact</a>
  </nav>
</header>
```

```css
.navbar {
  display: flex;
  justify-content: space-between;
  padding: 20px;
  background-color: lightgray;
}

.logo {
  font-weight: bold;
}

.nav-links {
  display: flex;
}

.nav-links a {
  margin-left: 20px;
  text-decoration: none;
  color: black;
}
```

In this example, the header with the class .navbar is set to display: flex to make it a flex container. The justify-content property is set to space-between so that the logo and navigation links will be positioned at opposite ends of the container, with equal amounts of space between them.

The .logo class sets the font weight to bold for the logo text. The .nav-links class is set to display: flex so that the navigation links will be displayed as a row of items.

Each a element within the .nav-links container is given a margin-left of 20px to create space between them and a text-decoration of none to remove the default underline. The color is set to black.

This is just one way to create a navigation bar using CSS Flexbox, but you could also experiment with different arrangements, alignments, and styles to create the look you want.
