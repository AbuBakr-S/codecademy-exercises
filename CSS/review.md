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
