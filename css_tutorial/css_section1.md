#CSS Tutorial

##Floats

*Clear fixing*

```CSS
.group:before, .group:after { content: "";
display: table; }
.group:after {
clear: both; }
.group {
zoom: 1; /* IE6&7 */ }
```
