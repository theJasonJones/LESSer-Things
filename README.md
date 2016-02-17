# LESSer-Things
A collection of mixins and many other random things I find I use over and over. 


```less
//Format
.center              { margin-right: auto; margin-left: auto; }
.txt-center     	 { text-align: center; }
.txt-italic 	     { font-style: italic; }
.uppercase		     { text-transform: uppercase; }

//Full Width Images
.bg-image 		     { background-repeat: no-repeat; background-size: cover; background-position: center center; }

//Horizontal & Vertical center: (Reminder: Parent element needs to be position: relative; )
.center-hv 		    { position: absolute; top: 50%; left: 50%; .translate(-50%; -50%); }

// Font size and line height
.fs(@size:18px)      { font-size:@size; }
.lh(@height:30px)    { line-height:@height; }

//All-in-one text mixin
.txt(@fs:18px; @lh:30px; @mb:initial)   { .fs(@fs); .lh(@lh); margin-bottom:@mb; }

// Sizing shortcuts

.size(@width; @height) {
  width: @width;
  height: @height;
}

.square(@size) {
  .size(@size; @size);
}

// Transitions
.transition(@transition) {
  -webkit-transition: @transition;
       -o-transition: @transition;
          transition: @transition;
}

// Responsive images (Thanks BS)
//
// Keep images from scaling beyond the width of their parents.
.img-responsive(@display: block) {
  display: @display;
  max-width: 100%; // Part 1: Set a maximum relative to the parent
  height: auto; // Part 2: Scale the height according to the width, otherwise you get stretching
}

// Horizontal gradient, from left to right
//
// Creates two color stops, start and end, by specifying a color and position for each color stop.
// Color stops are not available in IE9 and below.
.horizontal-g(@start-color: #555; @end-color: #333; @start-percent: 0%; @end-percent: 100%) {
    background-image: -webkit-linear-gradient(left, @start-color @start-percent, @end-color @end-percent); // Safari 5.1-6, Chrome 10+
    background-image: -o-linear-gradient(left, @start-color @start-percent, @end-color @end-percent); // Opera 12
    background-image: linear-gradient(to right, @start-color @start-percent, @end-color @end-percent); // Standard, IE10, Firefox 16+, Opera 12.10+, Safari 7+, Chrome 26+
    background-repeat: repeat-x;
    filter: e(%("progid:DXImageTransform.Microsoft.gradient(startColorstr='%d', endColorstr='%d', GradientType=1)",argb(@start-color),argb(@end-color))); // IE9 and down
  }

  // Vertical gradient, from top to bottom
  //
  // Creates two color stops, start and end, by specifying a color and position for each color stop.
  // Color stops are not available in IE9 and below.
.vertical-g(@start-color: #555; @end-color: #333; @start-percent: 0%; @end-percent: 100%) {
    background-image: -webkit-linear-gradient(top, @start-color @start-percent, @end-color @end-percent);  // Safari 5.1-6, Chrome 10+
    background-image: -o-linear-gradient(top, @start-color @start-percent, @end-color @end-percent);  // Opera 12
    background-image: linear-gradient(to bottom, @start-color @start-percent, @end-color @end-percent); // Standard, IE10, Firefox 16+, Opera 12.10+, Safari 7+, Chrome 26+
    background-repeat: repeat-x;
    filter: e(%("progid:DXImageTransform.Microsoft.gradient(startColorstr='%d', endColorstr='%d', GradientType=0)",argb(@start-color),argb(@end-color))); // IE9 and down
  }
```
