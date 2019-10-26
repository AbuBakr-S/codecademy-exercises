## Specificity

* IDs are the most specific selector in CSS, followed by classes, and finally, tags.
* HTML elements could have two or more CSS selectors at the same time.

## Chaining selectors
```
h1.special {

}
```
The code above would select only the h1 elements that have a class of special. If a p element also had a class of special, the rule in the example would not style the paragraph.

## Nested Elements
In addition to chaining selectors to select elements, CSS also supports selecting elements that are nested within other HTML elements. For instance, consider the following HTML:
```
<ul class='main-list'>
  <li> ... </li>
  <li> ... </li>
  <li> ... </li>
</ul>
```
The nested `<li>` elements are selected with the following CSS:
```
.main-list li {

}
```

## Important
There is one thing that is even more specific than IDs: !important. !important can be applied to specific attributes instead of full rules. It will override any style no matter how specific it is. As a result, it should almost never be used. Once !important is used, it is very hard to override.

The syntax of !important in CSS looks like this:
```
p {
  color: blue !important;
}
```

## Multiple Selectors
In order to make CSS more concise, add CSS styles to multiple CSS selectors all at once to keep your code DRY.
```
h1,
.menu {
  font-family: Georgia;
}
```
By separating the CSS selectors with a comma, both the h1 and the .menu elements will receive the font-family: Georgia styling.
