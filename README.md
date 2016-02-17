# LESSer-Things
A collection of mixins and many other random things I find I use over and over. 


```less
.fs(@size:18px)      { font-size:@size; }
.lh(@height:30px)    { line-height:@height; }

//Format and Font
.center              { margin-right: auto; margin-left: auto; }
.txt-center     	 { text-align: center; }
.txt-italic 	     { font-style: italic; }
.uppercase		     { text-transform: uppercase; }

//Full Width Images
.bg-image 		     { background-repeat: no-repeat; background-size: cover; background-position: center center; }

//Horizontal & Vertical center: (Reminder: Parent element needs to be position: relative; )
.center-hv 		    { position: absolute; top: 50%; left: 50%; .translate(-50%; -50%); }

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
```
