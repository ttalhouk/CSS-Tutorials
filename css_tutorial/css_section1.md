# CSS Tutorial

## Floats

*Clear fixing*  
clears containers that have floats
```CSS
.group:before, .group:after { content: "";
display: table; }
.group:after {
clear: both; }
.group {
zoom: 1; /* IE6&7 */ }
```
add group class to clear floats
```HTML
<div class="group">
     <img src="ski.jpg" alt="Skiing!" />
     <p>To successfully ski, simply do not fall.</p>
</div>
```
*Overflow Properties*

* `overflow:visible;` content can extend beyond border
* `overflow:auto;` adds scroll bars
* `overflow:hidden;` content can beyond border not shown
* `overflow:scroll;` scroll bars added regardless

*Positioning Properties*

* `position:static;` default

Others can be positioned using `top/left/right/bottom` properties

* `position:relative;` can be moved from its relative static position
* `position:absolute;` sticks to its parent container position to it
* `position:fixed;` positioned relative to the window not container

*Display Properties*

* `display:none;`
* `display:block;` takes up the entire width of their parent container
* `display:inline;` takes up only the size of its contents
* `display:inline-block;` takes up the size of its contents but can apply box model

##Images

Images used as part of the layout should be background images.  

```CSS
.snowmobile li {
background: url(snowmobile.jpg);
height: 300px;
width: 400px;
}
```
Images used as content should be block images.
```
<img src="..." />
```

##Overflow Cropping

```
HTML
<h4>Rental Products</h4> <ul class="rental">
<li class="crop">
  <img src="snowboard.jpg" alt="Snowboard" />
</li>

CSS
// sizes the container and crops that which overflows
.crop {
height: 300px;
width: 400px;
overflow: hidden;
}
// sets the image width to = container and keep aspect ratio the same
// swap height and width for landscape/portrait images
.crop img {
height: auto;
width: 400px;
}
```

*Image Replacement & Sprites*
```
HTML
<a href="#" class="logo">Sven's Snowshoe Emporium</a>

CSS
.logo {
    background: url(logo.png);
    display: block;
    height: 100px;
    width: 200px;
    text-indent: -9999px; // moves the text off the screen
}
.logo:hover, .logo:focus {
     background-position: 0 -100px; // moves the hover image by X Y
}
```

##Psudo Classes

Removing the last border from a list
Use `:last-child`
```
li {
     border-bottom: 1px solid #aaa;
   }
li:last-child {
     border-bottom: 0;
}
```
Zebra striping
Use `:nth-child(even)`
```
li:nth-child(even) {
     background-color: #444245;
}
```
After
Use `:after`
```
article p:last-child:after {
     content: '\2744';
}
```
Other useful ones
`:first-letter/:first-line`
