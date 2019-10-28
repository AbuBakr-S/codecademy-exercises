# The Box Model

## Introduction to the Box Model
* Browsers load HTML elements with default position values. This often leads to an unexpected and unwanted user experience, while limiting the views you can create. 
* All elements on a web page are interpreted by the browser as “living” inside of a box. This is what is meant by the box model.
* When you change the background color of an element, you change the background color of its entire box.

### Of an Element's Box:
1. Width and height — specifies the width and height of the content area.
2. Padding — specifies the amount of space between the content area and the border.
3. Border — specifies the thickness and style of the border surrounding the content area and padding.
4. Margin — specifies the amount of space between the border and the outside edge of the element.

## Centring Content
The margin property also lets you center content. 
```
div {
  margin: 0 auto;
}
```
In the example above, `margin: 0 auto;` will center the divs in their containing elements. 
The `0` sets the top and bottom margins to 0 pixels. The auto value instructs the browser to adjust the left and right margins until the element is centered within its containing element.

In order to center an element, a **width must be set for that element.** Otherwise, the width of the div will be automatically set to the full width of its containing element, like the `<body>`, for example. It’s not possible to center an element that takes up the full width of the page.
```
div.headline {
  width: 400px;
  margin: 0 auto;
}
```

## Margin Collapse
* Top and bottom margins, also called vertical margins, collapse, while top and bottom padding does not.
* Horizontal margins (left and right), like padding, are always displayed and added together. 

```
#img-one {
  margin-right: 20px;
}

#img-two {
  margin-left: 20px;
}
```

Vertical margins collapse, so the space between vertically adjacent elements is equal to the larger margin.
```
#img-one {
  margin-bottom: 30px;
}

#img-two {
  margin-top: 20px;
}
```

## Overflow
All of the components of the box model comprise an element’s size. For example, an image that has the following dimensions is 364 pixels wide and 244 pixels tall.

* 300 pixels wide
* 200 pixels tall
* 10 pixels padding on the left and right
* 10 pixels padding on the top and bottom
* 2 pixels border on the left and right
* 2 pixels border on the top and bottom
* 20 pixels margin on the left and right
* 10 pixels margin on the top and bottom

**Sometimes, these components result in an element that is larger than the parent’s containing area.** How can we ensure that we can view all of an element that is larger than its parent’s containing area?

The overflow property controls what happens to content that spills, or overflows, outside its box. It can be set to one of the following values:

`hidden` - when set to this value, any content that overflows will be hidden from view.
`scroll` - when set to this value, a scrollbar will be added to the element’s box so that the rest of the content can be viewed by scrolling.
`visible` - when set to this value, the overflow content will be displayed outside of the containing element. Note, this is the default value.
```
p {
  overflow: scroll; 
}
```
The overflow property is **set on a parent element** to instruct a web browser how to render child elements. For example, if a div’s overflow property is set to scroll, all children of this div will display overflowing content with a scroll bar.

## Resetting Defaults
All major web browsers have a default stylesheet they use in the absence of an external stylesheet. These default stylesheets are known as user agent stylesheets.User agent stylesheets often have default CSS rules that set default values for padding and margin. 

Many developers choose to reset these default values so that they can truly work with a clean slate.
```
* {
  margin: 0;
  padding: 0;
}
```
The code in the example above resets the default margin and padding values of all HTML elements. It is often the first CSS rule in an external stylesheet.

Note that both properties are both set to 0. When these properties are set to 0, they do not require a unit of measurement.

## Visibility
Elements can be hidden from view with the visibility property.

The visibility property can be set to one of the following values:

`hidden` — hides an element.
`visible` — displays an element.
```
<ul>
  <li>Explore</li>
  <li>Connect</li>
  <li class="future">Donate</li>
<ul>

.future {
  visibility: hidden;
}
```

**Note:** An element with display: none will be completely removed from the web page. An element with visibility: hidden, however, will not be visible on the web page, but the space reserved for it will.


## Changing the Box Model
The `box-sizing property` controls the type of box model the browser should use when interpreting a web page.
The default value of this property is `content-box`. This is the same box model that is affected by border thickness and padding.

### Box Model: Border-Box
We can reset the entire box model and specify a new one: border-box.
```
* {
  box-sizing: border-box;
}
```
The code in the example above resets the box model to border-box for all HTML elements.


In this box model, the height and width of the box will remain fixed. The border thickness and padding will be included inside of the box, which means the overall dimensions of the box do not change.
```
<h1>Hello World</h1>
* {
  box-sizing: border-box;   // 
}

h1 {
  border: 1px solid black;
  height: 200px;
  width: 300px;
  padding: 10px;
}
```
In the example above, the height of the box would remain at 200 pixels and the width would remain at 300 pixels. The border thickness and padding would remain entirely inside of the box.

### The Box Model in Dev-Tools
* `CMD + Shift + C` - Shortcut to Chrome Dev-Tools
* Opens the Elements Panel
* Click on `Computed` Tab
* No values are shown with a `-`
* CLick the `+` to add new CSS rules in the Styles tab

#### Height of Box = Content Height + Padding (Top & Bottom) + Border (Top & Bottom)

#### Width of Box = Content Width + Padding (Left & Right) + Border (Left & Right)

Margin has no effect on how big or small an HTML Element's box is. It only effects proximity. 









### Position: Absolute
When an element’s position is set to absolute all other elements on the page will ignore the element and act like it is not present on the page. The element will be positioned relative to its closest positioned parent element.
```
.box-bottom {
  background-color: DeepSkyBlue;
  position: absolute;
  top: 20px;
  left: 50px;
}
```
In the example above, the .box-bottom `<div>` will be moved down and right from the top left corner of the view. **If offset properties weren’t specified, the top box would be entirely covered by the bottom box**

### Position: Fixed
When an element’s position is set to absolute, as in the last exercise, the element will scroll with the rest of the document when a user scrolls.

### Z-Index
When boxes on a web page have a combination of different positions, the boxes (and therefore, their content) can overlap with each other, making the content difficult to read or consume.

The z-index property controls the depth of elements, with deeper elements appearing behind shallower elements.
```
.box-top {
  background-color: Aquamarine;
  position: relative;
  z-index: 2;
}

.box-bottom {
  background-color: DeepSkyBlue;
  position: absolute;
  top: 20px;
  left: 50px;
  z-index: 1;
}
```
The z-index property does not work on static elements.

### Inline Display
Every HTML element has a default display value that dictates if it can share horizontal space with other elements. Some elements fill the entire browser from left to right regardless of the size of their content. Other elements only take up as much horizontal space as their content requires and can be directly next to other elements.

Three values for the display property: 
* inline
* block
* inline-block.

#### inline
Inline elements have a box that wraps tightly around their content, only taking up the amount of space necessary to display their content and not requiring a new line after each element. 

Inline elements cannot be altered in size with the height or width CSS properties.

The CSS display property provides the ability to make any element an inline element. This includes elements that are not inline by default such as paragraphs, divs, and headings.
```
h1 {
  display: inline;
}
```
The CSS in the example above will change the display of all `<h1>` elements to inline. The browser will render `<h1>` elements on the same line as other inline elements immediately before or after them (if there are any).

### block
These elements fill the entire width of the page by default, but their width property can also be set. Unless otherwise specified, they are the height necessary to accommodate their content.

### inline-block
Inline-block elements can appear next to each other and we can specify their dimensions using the width and height properties. Images are the best example of default inline-block elements.

## Float
The float property can be set to one of two values:

`left` - this value will move, or float, elements as far left as possible.

`right` - this value will move elements as far right as possible.
```
.boxes {
  width: 120px;
  height: 70px;
}

.box-bottom {
  background-color: DeepSkyBlue;
  float: right;
}
```
In the example above, we float the .box-bottom element to the right. This works for static and relative positioned elements. See the result of the code below:

Floated elements must have a width specified, as in the example above. Otherwise, the element will assume the full width of its containing element, and changing the float value will not yield any visible results.

## Clear
The float property can also be used to float multiple elements at once. However, when multiple floated elements have different heights, it can affect their layout on the page. Specifically, elements can “bump” into each other and not allow other elements to properly move to the left or right.

The clear property specifies how elements should behave when they bump into each other on the page. It can take on one of the following values:

`left` — the left side of the element will not touch any other element within the same containing element.

`right` — the right side of the element will not touch any other element within the same containing element.

`both` — neither side of the element will touch any other element within the same containing element.
none — the element can touch either side.
```
div {
  width: 200px;
  float: left;
}

div.special {
  clear: left;
}
```
In the example above, all `<div>`s on the page are floated to the left side. The element with class special did not move all the way to the left because a taller `<div>` blocked its positioning. By setting its clear property to left, the special `<div>` will be moved all the way to the left side of the page.



* All HTML elements are rectangular boxes to the browser
* The browser determines the size of the box unless we override it
* We should reset the box-model as it makes life easier for us as developers
* It's advised to use a reset stylesheet and set `box-sizing: border-box`
* Reset stylesheet: https://meyerweb.com/eric/tools/css/reset/