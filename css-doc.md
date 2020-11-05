
CSS:
=====

DIV and SPAN:
============
A div is a block-level element and a span is an inline element. 

The div should be used to wrap sections of a document, while use spans to wrap small portions of text, images, etc.

INHERITANCE:
===========
```
body {
  font-family: sans-serif;
} 
```
Child elements can inherit the body font property.

LAST RULE and SPECIFICITY:
======================
```
Ex:
p {
    color: blue;
}
p {
    color: red;
}
```
Last rule will be applied for 'P' tag

```Ex:
<p class="red">Indumathi</p>

.red {
    color: red;
}
p {
    color: blue;
}
```
Even though 'p' tag is the last rule, here class="red" is more specific, so red will be applied to 'p' tag.

UNIVERSAL SELECTOR:
==================
```
p {
   color: red;
}
*{
   color: blue;
}
```
Here red will be applied to ‘p’ tag. Universal selector is the least specific.

COLOR:
======
```
p {
    color: red;
    background : grey; // or background-color: grey;
}
```

RGB : RED, GREEN, BLUE (0 to 255)
---
```
color: rgb(255, 0, 0) -> Red
color: rgb(0, 255, 0) -> Green
color: rgb(0, 0, 0) -> Black
color: rgb(255, 255, 255) -> White
```
RGBA : RED, GREEN, BLUE (0 to 1) OPACITY/TRANSPARENCY
----
```
color: rgba(100, 123, 56, 0.5)
```
HEX values #RRGGBB :
-------------------
1 2 3 4 5 6 7 8 9 (10)A (11)B (12)C (13)D (14)E (15)F 
```
#FF0000 -> RED
#00FF00 -> GREEN
#000 -> Black
#fff -> White
#f234ad -> Pink
```
For more colors:
https://coolors.co/

UNITS IN CSS:
===========
Control the layout of the project

Pixels: Absolute
-------
Absolute unit of mesurement. 1 pixel represents one .(dot on screen)
```
Ex: <h1>Indumathi </h1>

h1 {
    font-size: 60px;
    width: 200px;
    height: 200px;
}
```

Relative: %
--------
% are depend on the parent element.
```
<div class="outer">
  <div class="inner">Indu</div>
</div>

.outer {
    width: 500px;
    height: 500px;
    background: #7a6060;
}
.inner {
    width: 50%;
    height: 50%;
    background: red;
}
```
 Inner Width occupies half of the parent width. Relative to parent.


em :
---
Relative depends on parent

1em = 16px default browser style

1em = base value
```
Ex: 1
 <h3 class="relative">Relative</h3>
 <h3 class="absolute">Absolute</h3>

 .relative {
    font-size: 2em;
 }
 .absolute {
    font-size: 32px;
 }
```
Here both h3 tag assigned with 32px; 2em = 32px;

We can change the default browser font size by going to settings -> Font size -> very large
now relative h3 tag alone will look bigger in font size.

```
Ex: 2
    <div>
        <h3 class="relative">Relative</h3>
    </div>
    <div>
        <h3 class="absolute">Absolute</h3>
    </div>

    .relative {
        font-size: 2em;
    }
    .absolute {
        font-size: 32px;
    }
    div {
        font-size: 10px;
    }
```
 Here now div is assigned with 10px; so relative class gets assigned with 20px;

 If we assign div with 16px then relative gets 32px;


rem :
----
It depends on root. Not depend on parent.
1rem = 16px default browser style
```
<div><h3 class="relative">Relative</h3></div>
<div><h3 class="absolute">Absolute</h3></div>

Ex: 1
  div {
    font-size: 40px;
  }
  .relative {
    font-size: 2rem; //Here even though parent div assigned with 40px, relative will be assigned with HTML default size 16px so 32px:
  }
  .absolute {
    font-size: 32px;
  }
 
Ex: 2: HTML is actual root for rem

      html {
        font-size: 32px;
      }
      div {
        font-size: 40px;
      }
      .relative {
        font-size: 2rem;
      }
      .absolute {
        font-size: 32px;
      }
```
Here relative will be assigned with 64px;


vh & vw :
---------
Useful for banners.
view height - view width
```
<div class="banner"></div>
<div class="header"></div>

.banner{
    width: 50vw;
    height: 50vh;
    background: red;
}
.header {
    width: 100vw;
    height: 100vh;
    background: green;
}
```
Depending on the screen size it changes 50% horizontally and 50% vertically for .banner


This is not exactly 100% or 50% 


Default browser styles and google devTools:

For every element get render in browser has some default styles applied to it.


calc():
--------
Performs math operations + - * /
mix and match values

Ex:
--
 ```
<div class="navbar">Navbar</div>
 <div class="banner"></div>

 .banner {
    min-height: 100vh; //Property sets the minimum height of an element
    background: red;
  }
  .navbar {
    font-size: 3rem;
    color: white;
    height: 100px;
    background: green;
  }
```

We need to set the banner height based on the navbar height. We can use calc()
```
.banner {
    min-height: calc(100vh - 100px);
    background: red;
  }

> calc(100vh- 100px) or calc(100vh-100px) wont work give space before and after '-'

```
FONT:
=====
Font stack: If the browser is not supported with the mentioned font-family.  So we can have a font stack(with several font family). If browser doesn’t support for the first one it will try with second.

At the end of the 'font stack' we can mention the 'generic family'.
```
 body {
    font-family: 'Times New Roman', Times, serif
 }
```
If browser doest take 'Times New Roman' then checks 'Times'. Then 'Times' not available then take the generic family 'serif'.

Generic: serif, sans-serif, cursive, fantasy, monospace


Google Fonts:
-------------

Go to : https://fonts.google.com/

Select the font, Copy the link and use the font.
```
index.html:
<link
  href="https://fonts.googleapis.com/css2?family=Roboto:wght@300&display=swap"
  rel="stylesheet"
/>

index.css:
body {
    font-family: 'Roboto', sans-serif;
  }
```
----------

Or we can import in index.css:
```
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@300&display=swap');

body {
    font-family: 'Roboto', sans-serif;
  }
```

Font weight:
------------
```
.one{
    font-weight: 600;
  }

font-weight: 900;
font-weigth: bold; // bolder, lighter

font-style: italic;
```
Text align:
----------
```
text-align: left; //center, right -> Control the alignment of the text.

text-indent: 50px;  //Indent the first line

line-height: 1.5em;  //Control the space between each lines. It is relative.

letter-spacing: 5px; //Control the space between each letters.

word-spacing: 20px; //Control the space between each words.

text-transform: uppercase; //capitalize, lowercase

Ex:
<a href="#">Heading</a>

a {
    text-decoration: none;
  }

> It removes the underline for 'a' tag

Ex:
 h1 {
    text-decoration: line-through; // o/p: sub heading
  }

Ex:                                ___________
text-decoration: overline; // o/p: sub heading

text-decoration: underline;  
```
 CSS BOX MODEL:
=============

Margin

Border

Padding

Content  

Each element displayed as a box.
Padding: Distance between the content of the element.
Border: Go around the element.
Margin: Distance between end of the screen or some other element.

PADDING:
=======
```
 div {
    background: red;
    padding-top: 32px;
    padding-bottom: 32px;
    padding-left: 23px;
    padding-right: 50px;
  }

or we can write as

 div {
    background: red;
    padding: 30px 60px; // top and bottom 30px, left and right 60px;
  }
```
Or we can give padding: 50px; // For all the sides. 

or padding: 20px 40px 30px 50px; padding: top right bottom left;

All of them are valid.

MARGIN:
======
We can use the margin property like padding.
```
 div {
    background: red;
    padding: 20px;
    margin-top: 20px;
    margin-bottom: 32px;
    margin-left: 23px;
    margin-right: 50px;
  }
```
By default browser assign margin for each element. If i dont want margin we cna assign with 0.
```
 div {
    background: red;
    padding: 20px;
    margin-bottom: 0;
  }
  p {
    background: blue;
    padding: 20px;
    margin-top: 0;
  }
```
To get rid of default margin to all the elements:
```
*{
    margin: 0;
}
```
BORDER:
======
```
div {
    background: red;
    padding: 20px;
    margin: 30px;
    border-style: solid;
    border-width: 10px;
    border-color: rgb(24, 10, 226);
  }

> Shorter version
border: width style color;

>border-bottom:
div {
    background: red;
    padding: 20px;
    margin: 30px;
    border-bottom-style: dotted;
    border-bottom-width: 10px;
    border-bottom-color: rgb(24, 10, 226);
  }
```
BORDER-RADIUS:
==============
```
Ex:
div {
    background: red;
    padding: 20px;
    border: 20px solid black;
    border-radius: 20px;  //Makes the boder edges curve
  }

border-radius: 50%; //Makes oval

```
Negative margin:
================
```
margin-top: -100px; //Overlaps other element.
```

Outline:
========

Margin

Outline

Border

Padding

Content
```
Ex:
<div class="buttons">
  <a id="one" href="#">One</a>
  <a id="two" href="#">Two</a>
</div>

css:
 a {
    text-decoration: none;
    color: black;
    padding: 1.2rem 1.5rem;
    text-transform: uppercase;
    cursor: pointer;
    background: #df6bdd;
  }
 #one {
    border: 0.2rem solid #222;
 }
 #two{
    outline: 0.2rem solid #222;
    outline-offset: 10px; // moves the ouline 10px above i.e out of the button
 }

> Outline same like border. Here we can use the offset property.

outline-offset: -10px; // moves the ouline 10px inside the button
```

Default display property:
=========================
Block: Always starts a new line and takes full width.
Inline: Doesnt start new line and only take up as much as content space.

Some of the element are block and inline elements by default.
We can change the default property of the elements by having "display: block;"
```
https://www.pexels.com/ -> to get images.

EX:
//Each one renders in seprate line
<div class="block">Block Element</div>
<h1 class="block">Block Element</h1>
<p class="block">Block Element</p>
//Below 3 appers in one line
<span class="inline">Inline Element</span> 
<a class="inline" href="#">Inline Element</a>
<img src="img/blackberries.jpeg" width="50" alt="Missing" />

CSS:
  .block {
    background: blue;
    color: aliceblue;
    display: inline; //div, h1, p are appears in same line.
  }
  .inline {
    background: red;
    color: aliceblue;
    display: block; //Now span, a, img will be rendered in new line.
  }
```
Horizontal Centering:
====================
```
<div class="block">Block Element</div>
<h1 class="block">Block Element</h1>
<p class="block">Block Element</p>


CSS:
  .body {
    text-align: center;
  }
  .block {
    background: blue;
    color: aliceblue;
    width: 150px;
    margin: 0 auto;
  }
```
We can also flex box for this.

BLOCK and INLINE:
=================
Block: Top Margin Bottom Respected by browser.
Inline: Top Margin Bottom Not Respected by browser.
```
Ex: 1 Padding and margin wont work in below example.
links are inline element. Browser is not respect that.

<ul>
  <li href="#">Home</li>
  <li href="#">Products</li>
  <li href="#">Contact us</li>
</ul>

CSS:
  *{
    margin:0;
    padding:0;
    box-sizing: border-box;
  }
  body{
    font-family: Verdana, Geneva, Tahoma, sans-serif;
  }
  ul li {
    list-style-type: none;
  }
  ul li a{
    text-decoration: none;
    text-transform: capitalize;
    letter-spacing: 2px;
    background: black;
    color:bisque;
    padding: 5px;
    margin: 10px;
  }
```
So here we need to make the link as block level element.

Ex: 2 Inline Block
-------------------
```
<a href="#">Home</a>
<a href="#">Products</a>
<a href="#">Contact us</a>

CSS:
 a {
    background: rgb(223, 9, 159);
    color: white;
    font-size: 60px;
    margin: 32px;  // Margin top and bottom wont be applied for inline element 'a' tag
 }
```
So here we can give display: inline-block, So it wont take new line.


BORDER BOX:
===========

```
<div class="box-1"><h1>Border box</h1></div>
<div class="box-2"><h1>Normal box</h1></div>
<div class="box-3"><h1>Without Border box</h1></div>

CSS:
  .box-1,
  .box-2,
  .box-3 {
    width: 200px;
    height: 200px;
    color: white;
  }
  .box-1 {
    background: red;
    padding: 20px;
  }
  .box-2 {
    background: blue;
  }
  .box-3 {
    background: green;
    padding: 20px;
  }
```
If we inspect the div of box-1 and box-3, it will be 240px x 240px;

But we assigned width as 200px;

Because we added padding 20px; left, right, top and bottom.

Eventhough the div is originally 200px x 200px.

Here we can use border-box

```
  .box-1 {
    background: red;
    padding: 20px;
    box-sizing: border-box;
  }
```
Now the content is 160 and padding is 20, so the width of div is 200px x 200px
Now padding will be applied inside of the element.

If we add border-box it wont mess up with the layout.


Display none, opacity, visibility:
===================================
```
<div class="none">Display none</div>
<div class="opacity-1">Opacity - 1</div>
<div class="opacity-5">Opacity - 5</div>
<div class="opacity-0">Opacity - 0</div>
<div class="visibility">Visibility</div>

CSS:
 div {
    background: blue;
    margin: 10px;
    color: white;
  }
  .none {
    display: none; //Hide the element. We cant see in the browser.
  }
  .opacity-1 {
    opacity: 1;
  }
  .opacity-5 {
    opacity: 0.5; //Half transperant
  }
  .opacity-0 {
    opacity: 0; //Hide the element. Element is there in browser but hidden with opacity 0
  }
 .visibility {
    visibility: hidden; //Hide the element. Element is there in browser but hidden
 }
```

Background Images:
===================
```
<div class="big-img"><h1>Big image</h1></div>
<div class="small-img"><h1>Small Image</h1></div>
<div class="folder-img"><h1>Folder image</h1></div>

CSS:
  div {
    height: 300px;
    color: red;
  }
  .big-img {
    background: url("./big.jpeg");
  }
  .small-img {
    background: url("./small.jpeg");
    background-repeat: repeat; //Repeats the image if the image doesnt fit the background.
  }
  .folder-img {
    background: url("img/blackberries.jpeg");
  }
```
background-repeat: no-repeat; --> Image wont get repeated.

background-repeat: repeat-x; --> Repeat only in x axis.

background-repeat: repeat-y; --> Repeat only in y axis.

background-repeat: space; --> Space between the images.

background-repeat: round; --> If the image is not fit to the div then 2 images exactly fits the div.

Regardless of the size of the div, the background images always fill up the div. Even though the image is small. But actual quality of the image suffer.
```
 .big-img {
    background: url("./big.jpeg");
    background-size: cover;
  }
```
background-size: contain; --> fits the div and repeat the image.


Background Position:
-------------------
```
 .small-img {
    background: url("./small.jpeg");
    background-repeat: no-repeat;
    background-position: center;
  }
```
To place the image at center of the div.

background-position: bottom; 

background-position: 20% 50%; --> 20% on x-axis and 50% on y-axis.

Background Attachment:
---------------------

Make sure the background image stay fixed. 
```
<div class="big-img"><h1>Big image</h1></div>
<div class="small-img"><h1>Small Image</h1></div>
<div class="folder-img"><h1>Folder image</h1></div>

CSS:
 * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }
  div {
    min-height: 100vh;
    color: red;
    font-size: 50px;
    display: flex;
    justify-content: center;
    align-items: center;
    text-align: center;
  }
  .big-img {
    background: url("./big.jpeg");
    background-position: center;
    background-size: cover;
    background-repeat: no-repeat;
    background-attachment: fixed;
  }
  .small-img {
    background: url("img/blackberries.jpeg");
    background-position: center;
    background-size: cover;
    background-repeat: no-repeat;
    background-attachment: fixed;
  }
  .folder-img {
    background: url("./big.jpeg");
    background-position: center;
    background-size: cover;
    background-repeat: no-repeat;
    background-attachment: fixed;
  }
```
background property not respected if we place it in div.


LINEAR GRADIENT:
===============
```
Ex:1
<div class="one"></div>
<div class="two"></div>
<div class="three"></div>
<div class="four"></div>
<div class="five"></div>

CSS:
  body {
    display: flex;
  }
  div {
    height: 150px;
    width: 150px;
    margin: 5px;
  }
  .one {
    background: linear-gradient(red, green);
  }
  .two {
    background: linear-gradient(to top, red, green, yellow);
  }
  .three {
    background: linear-gradient(150deg, red, green);
  }
  .four {
    background: linear-gradient(to top right, red, green);
  }
  .five {
    background: linear-gradient(rgba(0, 0, 0, 0.3), rgba(0, 0, 0, 0.9));
  }


Ex:2 To make the h1 more visible than background. 

* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }
  div {
    min-height: 100vh;
    display: flex;
    justify-content: center;
    text-align: center;
    align-items: center;
    font-size: 60px;
    color: white;
  }
  .banner {
    background: url("./img/blackberries.jpeg");
    background-position: center;
    background-size: cover;
    background-repeat: no-repeat;
    background-attachment: fixed;
  }
  .header {
    background: linear-gradient(rgba(0, 0, 0, 0.1), rgba(0, 0, 0, 0.5)),
      url("./img/watermelon.jpeg") center/cover no-repeat fixed;
  }
```
In header class we can write background in shorter way.
center/cover --> should be in this way, we should not change the order.

Shorter way:
```
.banner {
    background: url("./img/blackberries.jpeg") center/cover no-repeat fixed;
  }
```

For more gradient visit https://www.colorzilla.com/gradient-editor/

Edit the colors and copy the properties and use it for your div


FLOAT PROPERTY:
===============

```
<div class="banner">
  <img src="./small.jpeg" alt="" />
  <p>
    Lorem ipsum dolor sit amet consectetur adipisicing elit. Possimus ipsam
    numquam blanditiis accusantium obcaecati illum ratione, nobis harum
    officiis in a commodi repellendus voluptates eaque dolorum, mollitia
    facilis qui earum!
  </p>
</div>

CSS:
 .banner {
    border: 2px solid red;
    padding: 10px;
  }
  img {
    float: left; // Moves the image to right of the paragraph;
  }
  p {
    clear: both; //Clear the float right and left.
  }

Ex: 2
img {
    float: right;
    margin-left: 50px;
  }

Ex: 3 Float property column layout:
<div class="banner-1">
  Lorem ipsum dolor sit amet consectetur adipisicing elit.
</div>
<div class="banner-2">
  Lorem ipsum dolor sit amet consectetur adipisicing elit.
</div>
<div class="banner-3">
  Lorem ipsum dolor sit amet consectetur adipisicing elit.
</div>

CSS:
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }
  div {
    float: left;
    height: 100px;
    width: 33%;
  }
  .banner-1 {
    background: red;
  }
  .banner-2 {
    background: blue;
  }
  .banner-3 {
    background: green;
  }
```

Position:
---------
By default all the elements are position static.

```
Ex: 1 Position: relative
 <div>
  <p class="one">
    Lorem ipsum dolor sit amet consectetur adipisicing elit.
  </p>
  <p class="two">
    Lorem ipsum dolor sit amet
    <span class="special">Hey Im absolute</span>consectetur adipisicing
    elit.
  </p>
</div>

CSS:
  div {
    border: 2px solid red;
    background: rgb(240, 224, 8);
    margin-top: 40px;
    width: 50%;
  }
  .one {
    background: #7a6060;
    position: relative;
    right: 50%;
    bottom: 20px;
  }
  .two {
    background: #6007ee;
  }
  .special {
    background: #f8f4f4;
    font-size: 20px;
  }


Ex: 2 Position Absolute -> checks for any parent which has position relative. If nothing found it places itself position relative to 'body'.

CSS:
  div {
    border: 2px solid red;
    background: rgb(240, 224, 8);
    margin-top: 40px;
    width: 50%;
  }
  .one {
    background: #7a6060;
  }
  .two {
    background: #6007ee;
  }
  .special {
    background: #f8f4f4;
    font-size: 20px;
    position: absolute;
    top: 0;
    right: 0;
  }
```
Here span assigned with 'special' class which has position: absolute; 

It checks for ancesters who is having position: relative;

Here nothing found so assigned with body.

Because of the 'special' class having top and right as 0, the span moves to top right corner of the 'body'

If we assign .two class as position: relative then 
```
 .two {
    background: #6007ee;
    position: relative;
  }
```
span will move top right corner of the 'P' tag

```
Ex: 3 Position: fixed -> For navigation buttons

 .button {
    background: red;
    font-size: 30px;
    color: white;
    position: fixed;
    top: 0;
    right: 0;
  }
<button class="button">Submit</button>
```
Even if we scroll, the button will be fixed to top right corner.


MEDIA QUERY:
===========
Helps to write responsive design.

Style Elements depends on different screen sizes.

min-width: starting from

max-width: up to

```
Ex: 
<div class="banner">
  <h1>
    Lorem ipsum dolor
  </h1>
</div>

CSS:
  body {
    background: yellow;
  }
  .banner {
    background: blue;
  }
  h1 {
    color: white;
    text-align: center;
    text-decoration: underline;
    text-transform: capitalize;
  }
  @media screen and (max-width: 576px) {
    body {
      background: rgb(5, 218, 33);
    }
    .banner {
      background: red;
    }
    h1 {
      color: black;
      font-size: 60px;
    }
  }
  @media screen and (min-width: 768px) {
    body {
      background: rgb(233, 76, 199);
    }
    .banner {
      background: rgb(14, 193, 238);
    }
    h1 {
      color: rgb(80, 5, 5);
      font-size: 60px;
    }
  }
```

Z-index:
=======
By default z-index is 0.

It only work with position absolute and relative.

It wont work with position: static
```
<div class="banner">
  <img src="./small.jpeg" class="one" />
  <img src="./big.jpeg" class="two" />
  <img src="./img/watermelon.jpeg" class="three" />
</div>

CSS:
 img {
    width: 100px;
    height: 100px;
    position: absolute;
  }
  .banner {
    margin: 20px;
    width: 80vw;
    height: 70vh;
    border: 5px solid red;
    position: relative;
  }
  .one {
    top: 0;
    left: 0;
  }
  .two {
    top: 10%;
    left: 10%;
  }
  .three {
    top: 20%;
    left: 20%;
  }
```
Here image appears in this order -> small, big, watermelon

If i give z-index: 1 for 'small' image then 'small' image wont get hide with the 'big'

```
 .one {
    top: 0;
    left: 0;
    z-index: 1;
  }
 .two {
    top: 10%;
    left: 10%;
    z-index: -1; // 'big' goes below to small and above to 'watermelon'
  }
  .three {
    top: 20%;
    left: 20%;
    z-index: -2; // 'watermelon' goes below to big 
  }
```
It wont work with position: static
```
 .one {
    top: 0;
    left: 0;
    position: static
    z-index: 1; // it wont work
  }
```

PSEUDO ELEMENTS:
=================
Style specific parts of the element. 

::before ::after Content not Element -> add the Content before or after the content of the Paragraph.
```
content:'' -> required
img -> does not work. We cant add ::before ::after img

Ex:
<p>before and after pseudo elements</p>

CSS:
  p::before {
    content: "hello ";
  }

O/P : hello before and after pseudo elements

Ex:1
We can also apply CSS for the content.
  p::before {
    content: "hello ";
    color: red;
    font-weight: bold;
    font-size: 2rem;
  }

Ex:2 adding 'Bye' at the end of the content of 'p' tag and also making the content appear in new line by adding display:block;

 p::after{
    content: " Bye";
    display:block;
  }

Ex: 3
<div>
  <img src="big.jpeg" />
</div>

CSS:
  div {
    width: 50vw;
    margin: 100px auto;
    border: 2px solid red;
  }
  img {
    width: 100%;
  }
```
Even though width is 100% the image wont exactly fit into the border red.

To get rid of the extra margin at bottom, We can update like below
```
img {
    width: 100%;
    display: block;
  }
```

Ex: 4 Box transition
```
 <div>
  <img src="big.jpeg" />
</div>

CSS:
 div {
    width: 50vw;
    margin: 100px auto;
    position: relative;
  }
  img {
    width: 100%;
    display: block;
  }
  div::before {
    content: "";
    border: 2px solid grey;
    width: 100%;
    height: 100%;
    position: absolute;
    box-sizing: border-box;
    top: -40px;
    left: -40px;
    z-index: -2;
    transition: all 0.5s linear;
  }
  div::after {
    content: "";
    background: grey;
    width: 100%;
    height: 100%;
    position: absolute;
    box-sizing: border-box;
    top: -20px;
    left: -20px;
    z-index: -1;
    transition: all 0.5s linear;
  }
  div:hover::after,
  div:hover::before {
    top: 0;
    left: 0;
  }
```





















