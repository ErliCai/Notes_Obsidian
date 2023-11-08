### What is HTML

HTML defines content and structure of website

HTML = Hypertext Markup Language

Hypertext: piece of text that can link to other docs in the  website


### Tags
#### Heading

<h1>  Hello World </h1>
```
<h1>  Hello World </h1> HTML element
<h1> opening tag
</h1> closing tag
```

only has h1 through h6

- don't have more than 1 h1
- don't skip a level in heading
```
<h1> heading1 </h1>
<h3> heading3 </h3>
```


#### paragraph

paragraph tag is used to separate paragraph into different lines

```
<p> paragraph conten </p>
```

placeholder text: it's used to simulate content in a paragraph (often used  in web dev and print industry: Lorem Ipsum)

#### self closing tags

void element: forbidden to put anything inside the tag
eg. horizontal rule <hr />     break element <br />

```
could write <hr> <br> without closing tag
```
- don't use br when you actually need a new paragraph





#### List

- unordered list (bullet list
- 
- )
```
<ul>
  <li> item1 </li>
  <li> item2 </li>
</ul>
```

- ordered list
```
<ol>
  <li> item1 </li>
  <li> item2 </li>
</ol>
```
#### Anchor element

<a href="http://www.google.com">This is a link </a>
```
<a href="http://www.google.com">This is a link </a>
<tag attribute=value> content </tag>
```

#### image element

```
<img src="url" alt="description of the image" />
```
img is a self closing tag


### Multipage website

#### file path
- absolute file path: file path relative to the root of the computer
- relative file path: relative to location where we are writing the code

relative file path: shorter and validate while moving folder around



### other

#### Nesting and indentation

Proper indentation helps reading your code when there are nested structure
e.g.
<ul>
  <li> item1 </li>
  <li> item2 </li>
  <li>
    <ul>
      <li> item3.1 </li>
      <li> item3.2 </li>
    </ul>
  </li>
</ul>
```
<ul>
  <li> item1 </li>
  <li> item2 </li>
  <li>
    <ul>
      <li> item3.1 </li>
      <li> item3.2 </li>
    </ul>
  </li>
</ul>
```
#### attribute

- specific attribute
e.g.
![[HTML#Anchor element]]

- global attribute
In addition to attribute specific to a tag, there are also global attributes, that every tag has access to.
e.g. draggable

#### HTML Boilerplate
```
<!DOCTYPE html>   // doctype declaration
<html lang="en">
  <head>
    <meta charset="UTF-8">
    <title> website title </title>
  </head>

  <body>
    //content of website
  </body>
</html>
```


#### hosting website

hosting website: make your site available everywhere on earth by puting all data of site on a web server

how to host page on github: https://www.udemy.com/course/the-complete-web-development-bootcamp/learn/lecture/37350028#notes
