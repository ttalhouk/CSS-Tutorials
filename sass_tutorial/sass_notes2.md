# SASS Tutorial 2
*from codeschool.com*

## SASS Extras

### Indented `.sass` Syntax


```Sass
.content
  border: 1px solid #ccc
  padding: 20px
  h2
    font-size: 3em
    margin: 20px 0
```
*similar to haml and html*

**SASS mixin syntax**
```Sass
=box-sizing($x) // defines mixin
  -webkit-box-sizing: $x
  -moz-box-sizing: $x
  box-sizing: $x
.content
  +box-sizing(border-box) // includes mixin
```

**SASS list helpers**

* `length($authors)` returns the length of a list
* `append($authors, tim)` adds to the end of a list (doesn't modify list variable)
* `join($authors1, $authors2)` joins to lists similar to append
* `index($authors, dan)` returns the index of query (lists start with index 1)
* `nth($authors, 3)` returns the nth value of a list
* `zip($authors, $co-authors)` pairs indexes of both lists to form new list

**More Utilities**

single line if statements

`if(condition, "true value", "false value")`

Example
`background: if($theme == dark, #000, #fff)`

## Compass

Compass is a Sass library that has extra functionality

> [Compass github]: http://github.com/chriseppstein/compass

**Compass Modules**

* `utilities`
* `typography`
* `css3`
* `layout`
* `reset` // not ideal for production

Once installed add the following to the main Sass file
```
@import "compass" // imports utilities, typography, css3
@import "compass/layout"
```

**Why use Compass**

1. Handles prefixes `webkit`, `moz`, etc...
```
@import "compass"
.content
  +box-sizing(border-box)
```
  * background (gradients)
  * border-radius
  * box-shadow
  * columns
  * transform
  * transition

Example

```
// CSS gradients

.content {
   background: -webkit-gradient(linear, 50% 0%, 50% 100%,
     color-stop(0%, #9b9592), color-stop(100%, #3c3733));
   background: -webkit-linear-gradient(top, #9b9592, #3c3733);
   background: -moz-linear-gradient(top, #9b9592, #3c3733);
   background: -o-linear-gradient(top, #9b9592, #3c3733);
   background: -ms-linear-gradient(top, #9b9592, #3c3733);
   background: linear-gradient(top, #9b9592, #3c3733);
}

// Can be written with this
@import "compass"
 .content
   +background(radial-gradient(center, #9b9592, #3c3733))
```

## Utilities

Setting vertical baselines

```
@import "compass"

$base-font-size: 18px
$base-line-height: 30px
+establish-baseline

// results in spacing calculated for you
html {
  font-size: 112.5%;
  line-height: 1.667em;
}
```
Once baseline is established, change font sizes like this
```
h1
  +adjust-font-size-to(50px)
```
**Leading**

```
blockquote
  +adjust-leading-to(2)
  background: #ccc
```
*this blockquote will take up 2 vertical units*

If adjusting the font size as well, it needs to be passed in as an argument.
```
blockquote
  +adjust-font-size-to(20px)
  +adjust-leading-to(2, 20px)
  background: #ccc
```
*this will adjust the font size but keep the spacing correct*

Note: maintaining vertical rhythm is difficult and can cause CSS bloat due to the excess css that gets written.
use sparingly as needed.

Example of rhythm use
```
@import "compass"
 $base-font-size: 18px
 $base-line-height: 30px
 +establish-baseline
 h1
   +adjust-font-size-to(50px)
   +trailer(2, 50px)
   +trailing-border(10px, 1, 50px)
 blockquote
   +adjust-font-size-to(20px)
   +rhythm-borders(2px, 1, 20px)
 p
   +leader(1)
   +trailer(1)
```

## Sprites

```
@import "compass"
@import "icons/*.png"
// grabs all png's from the icons folder and generates a png with all

+all-icons-sprites
// where this is located

outputs
// assuming 3 icons cancel, next, and warning were in the icon folder
.icons-sprite, .icons-cancel,
.icons-next, .icons-warning {
  background: url('/images/icons-
s451834c886.png') no-repeat;
}
.icons-cancel {
  background-position: 0 -169px; // auto locates position, width and height need to be set manully
}
.icons-next {
  background-position: 0 -335px;
}
.icons-warning {
  background-position: 0 0;
}
```

**Manually Built Spritemap**

```
@import "compass"
$icons: sprite-map("icons/*.png")

i                       //Icon selector
  display: inline-block

.icn-cancel  // icon positioning for cancel icon
  background-position: sprite-position($icons, cancel) // auto locates icon
  +sprite-dimensions($icons, cancel) // sets height and width automatically

refactored

@import "compass"
$icons: sprite-map("icons/*.png")
i
@each $i in sprite_names($icons) // creates the class for each icon in the folder
  .icn-#{$i}
    background-position: sprite-position($icons, $i)
    +sprite-dimensions($icons, $i)

```
