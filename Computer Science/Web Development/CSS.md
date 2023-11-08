
CSS = Cascading Style Sheets
Cascade from most general to most specific
style sheet language

### Why we need CSS

At the very beginning of web, there's no CSS but only HTML. There is no way to control what the website looks like.

CSS allows to attach style to HTML

### How to add CSS

#### Inline

```
<html style="background:blue">
</html>
```
background is the property we want to change
and blue is the value

- inline element is useful to add CSS element to single element on the page but can be very cumbersome 

#### Internal

```
<html>
  <head>
    <style>
      html{
        background:red;
      }
    </style>
  </head>
</html>
```

<b>html</b> here is the selector
- useful to apply style to only one element, not working on multi page site
#### External

Put CSS style in a separate file

##### how to link external CSS file to HTML

```
<html>
  <head>
    <link
      rel="stylesheet"
      href="./styles.css"
	/>
  </head>
</html>
```

rel is the relationship of the file linked
href is the location of the file



### Selector

#### Element Selector
```
h2{
  color: red;
}
```

#### Class Selector

class is an attribute used to grouping element in html
```
<h2 class="red-text"> RED </h2>
<h2> Green </h2>


.red-text{
  color: red;
}
```

#### Id selector

```
<h2 id="main"> RED </h2>

#main{
  color:red;
}
```

#### id vs class
- same class can be applied to many element
- id should be only applied to one element in a single html file

#### Attribute Selector

```
p[draggable="true"]{
  color:red;
}
```

p is the html element and draggable is attribute we want to select 

#### universal seelctor

```
*{
  color:red;
}
```

select everything

### CSS properties

#### color properties
- background-color
- color (text color)
    check "named color" for color can be used in this property
    or use hexcode for colors 

#### font prorperties
- color
- font-weight
- font-size
    1px (1/96 inch)
    1pt (1/72 inch)
    1em (100% of parent)
    1rem (100% of root)
- font-family