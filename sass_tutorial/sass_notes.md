# SASS Tutorial

## Overview

*Syntactially Awsome Style Sheets*  

1. .sass file is made  
2. Run through a sass compiler  
3. css file output  

.scss is a default  CSS

`//` is a valid comment for scss

In scss `@import` is run during compiling rather than run time making it more performant
if the file is preceded with an underscore, making it a partial such as `_buttons.scss` but is
imported into the application scss by using @import 'buttons'

### Nesting
``` CSS
in css it is written like this
.content{

}
.content h2{

}
.content p{

}
```
``` SCSS
in scss it is written like this
.content{
  h2{

  }
  p{

  }
}
```
### Nesting Namespace properties
``` SCSS
.content{
  text:{
    decoration: none;
    transform: lowercase;
  }
}

converts to

.content{
  text-decoration: none;
  text-transform: lowercase;
}
```
### Compound Selector  
& symbol is the parent Selector  
*Useful for psudo classes*
```scss
.content{
  .callout{

  }
  &.callout{

  }
}

converts to

.content .callout{// has .callout under .content

}
.content.callout{ // has both class callouts

}
```
```scss
.content{
  .users &{

  }
  h2{
    .users &{

    }
  }
}

converts to

.users .content{ // & references .content
}
.users .content h2{ // & references .content h2

}
```

## Variables

Variables are declared using `$` such
```scss
$base: #777777;

.sidebar{
  border: 1px solid $base;
  p {
    color: $base;
  }
}
```
Defaults
``` SCSS
$title:"My Blog";
$title:"About Me" !default; // sets default value

h2{
  content: $title; // "My Blog" since it exists otherwise it would use default
}
```
*useful for setting defaults in partials so that it can be used in other scss files and uses
default values unless specified by the file importing it*

Variable can store:  
* `numbers`
* `boolean`
* `colors` RGBA or named colors
* `strings` strings with or without quotes
* `lists` comma seperatoed or spaced out

### Variable Scoping  
Variables are only scoped within the context they were set so
```scss
p {
  $base: red;
  color: $base;
}
h2 {
  color: $base; // doesn't work!
}
```
But...
```
$base: blue;
p {
  $base: red; // changes $base globally
  color: $base;
}
h2 {
  color: $base; // color: red;
}
```

### String Interpolation

Similar to Ruby `#{$variable}`

## Mixins

Used to help combat repetition in styles
```SCSS
@mixin button{
  ... properties shared by all buttons
}

.btn-a{
  @include button; //includes the styles set in button mixin
  ... other styles for .btn-a
}
```
***`@mixin` must be declared before using the `@include`***

This still compiles down to the repeated CSS after compiling.  However Mixins can take arguments.

```SCSS
@mixin box-sizing($x) {
   -webkit-box-sizing: $x;
   -moz-box-sizing: $x;
   box-sizing: $x;
}
.content {
  @include box-sizing(border-box); // $x is border-box
  border: 1px solid #ccc;
  padding: 20px;
}
.callout {
  @include box-sizing(content-box);// $x is content-box
}
```
Default values can be set for the arguments
```SCSS
@mixin box-sizing($x: border-box) {
   -webkit-box-sizing: $x;
   -moz-box-sizing: $x;
   box-sizing: $x;
}
```
Multiple arguments can be passed, but defaults must come at the end.

Arguments can be key value pairs.
```SCSS
@mixin button($radius, $color: #000) {
  border-radius: $radius;
  color: $color;
}
.btn-a {
  @include button($color: #777777,
$radius: 5px); // order of arguments not important if passed with keys
}
```
For arguments that take multiple values
```SCSS
@mixin transition($val...) { // use variable... notation
  -webkit-transition: $val;
  -moz-transition: $val;
  transition: $val;
}
.btn-a {
  @include transition(color 0.3s
ease-in, background 0.5s ease-out);
}
```

```
@mixin highlight-t($color) {
  border-top-color: $color;
}
@mixin highlight-r($color) {
   border-right-color: $color;
 }
 @mixin highlight-b($color) {
   border-bottom-color: $color;
 }
 @mixin highlight-l($color) {
   border-left-color: $color;
 }
.btn-a {
@include highlight-r(#ff0);
}

// can be refactored using string Interpolation

@mixin highlight($color, $side) {   border-#{$side}-color: $color; }
.btn-a {
  @include highlight(#ff0, right);
}

```

## Extend
Inheritance of styles from classes using `@extend`
```scss
.btn-a {
  background: #777;
  border: 1px solid #ccc;
  font-size: 1em;
  text-transform: uppercase;
}
.btn-b {
  @extend .btn-a;
  background: #ff0;
}
```
**Caution: any changes made to btn-a are inherited by btn-b through @extend**

Alternately use placeholder selectors `%`
```scss
%btn{
  background: #777;
  border: 1px solid #ccc;
  font-size: 1em;
  text-transform: uppercase;
}
.btn-a {
  @extend %btn;
}
.btn-b {
  @extend %btn;
  background: #ff0;
}
```

## Directive

Using functions within Scss
```scss
@function fluidize($target, $context) {
  @return ($target / $context) * 100%;
}
.sidebar {
  width: fluidize(350px, 1000px);
}

// results in css compiled to
.sidebar {
  width: 35%;
}
```
Also allows for If statements
```
$theme: pink;
 header {
   @if $theme == dark {
     background: #000;
   } @else if $theme == pink {
     background: pink;
   } @else {
     background: #fff;
   }
}
```
Each loops
```
.item {
  position: absolute;
  right: 0;
  @for $i from 1 through 3 {
    &.item-#{$i} {
      top: $i * 30px;
    }
  }
}
// increases the size for each item
```

## Math and Color

* `round($number)` - round to closest whole number
* `ceil($number)` - round up
* `floor($number)` - round down
* `abs($number)` - absolute value
* `min($list)` - minimum list value
* `max($list)` - maximum list value
* `percentage($number)` - convert to percentage

Color functions are available as well

## Responsive

**Media Queries**
```
.sidebar {
   border: 1px solid #ccc;
 }
 @media (min-width: 700px) { // checks size of viewport
   .sidebar {
     float: right;
     width: 30%;
} }
```
Responsive mix-in
```
@mixin respond-to($type: min-width, $query: 960px ) {
  @media ($type: $query) {
    @content;
  }
}
```

## Installing Sass

`gem instal sass`
