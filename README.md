# LESSer-Things
A collection of mixins and many other random things I find I use over and over. 


```less
//Format
.center            { display: block; margin-right: auto; margin-left: auto; }
.txt-center     	 { text-align: center; }
.txt-italic 	     { font-style: italic; }
.uppercase		     { text-transform: uppercase; }

//Full Width Images
.bg-image 		     { background-repeat: no-repeat; background-size: cover; background-position: center center; }

//Horizontal & Vertical center: (Protip: Parent element needs to be position: relative; )
.center-hv 		    { position: absolute; top: 50%; left: 50%; .translate(-50%; -50%); }

//Image Overlay
.basic-overlay(@color: #000; @opacity: 0.4) 		{ background-color: @color; .opacity(@opacity); position: absolute; top: 0px; left: 0px; z-index: 2; width: 100%; height: 100%;} 

//Wrapper to place over the overlay (good for text and buttons)
.overlay-top { .center-hv; z-index: 3; }

// Table Centering 
.table-wrap 										{ .square(100%); display:table; }
.table-cell 										{ display:table-cell; vertical-align:middle; }

// Font size and line height
.fs(@size:18px)      { font-size:@size; }
.lh(@height:30px)    { line-height:@height; }

//All-in-one text mixin
.txt(@fs:18px; @lh:30px; @mb:initial)   { .fs(@fs); .lh(@lh); margin-bottom:@mb; }


/**** VENDOR STYLES (Hence the sudden change in style) ****/


// Buttons
.button {
  display: inline-block;
  margin-bottom: 0; // For input.btn
  font-weight: 400;
  text-align: center;
  vertical-align: middle;
  touch-action: manipulation;
  cursor: pointer;
  background-image: none; // Reset unusual Firefox-on-Android default style; see https://github.com/necolas/normalize.css/issues/214
  border: 1px solid transparent;
  white-space: nowrap;
  .button-size(@padding-base-vertical; @padding-base-horizontal; @font-size-base; @line-height-base; @border-radius-base);
  .user-select(none);

  &,
  &:active,
  &.active {
    &:focus,
    &.focus {
      .tab-focus();
    }
  }

  &:hover,
  &:focus,
  &.focus {
    color: @btn-default-color;
    text-decoration: none;
  }

  &:active,
  &.active {
    outline: 0;
    background-image: none;
    .box-shadow(inset 0 3px 5px rgba(0,0,0,.125));
  }

  &.disabled,
  &[disabled],
  fieldset[disabled] & {
    cursor: @cursor-disabled;
    pointer-events: none; // Future-proof disabling of clicks
    .opacity(.65);
    .box-shadow(none);
  }
}

// btn sizes
.button-size(@padding-vertical; @padding-horizontal; @font-size; @line-height; @border-radius) {
  padding: @padding-vertical @padding-horizontal;
  font-size: @font-size;
  line-height: @line-height;
  border-radius: @border-radius;
}

// Sizing shortcuts
.size(@width; @height) {
  width: @width;
  height: @height;
}

.square(@size) {
  .size(@size; @size);
}

// WebKit-style focus

.tab-focus() {
  // Default
  outline: thin dotted;
  // WebKit
  outline: 5px auto -webkit-focus-ring-color;
  outline-offset: -2px;
}


// Transitions
.transition(@transition) {
  -webkit-transition: @transition;
       -o-transition: @transition;
          transition: @transition;
}

// Source: http://nicolasgallagher.com/micro-clearfix-hack/
.clearfix() {
  &:before,
  &:after {
    content: " "; // 1
    display: table; // 2
  }
  &:after {
    clear: both;
  }
}

// Responsive images (Thanks BS)
//
// Keep images from scaling beyond the width of their parents.
.img-responsive(@display: block) {
  display: @display;
  max-width: 100%; // Part 1: Set a maximum relative to the parent
  height: auto; // Part 2: Scale the height according to the width, otherwise you get stretching
}

//Box Shadow
.box-shadow(@shadow) {
  -webkit-box-shadow: @shadow; // iOS <4.3 & Android <4.1
          box-shadow: @shadow;
}

// Opacity

.opacity(@opacity) {
  opacity: @opacity;
  // IE8 filter
  @opacity-ie: (@opacity * 100);
  filter: ~"alpha(opacity=@{opacity-ie})";
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
