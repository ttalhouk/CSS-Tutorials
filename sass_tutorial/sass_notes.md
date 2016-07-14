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
