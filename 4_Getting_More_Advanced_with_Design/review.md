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
