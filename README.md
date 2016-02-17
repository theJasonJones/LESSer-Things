# LESSer-Things
A collection of mixins and many other random things I find I use over and over. 


```less
.fs(@size:18px)    { font-size:@size; }
.lh(@height:30px)  { line-height:@height; }
.center 		       { margin-right: auto; margin-left: auto; }
.txt-center     	 { text-align: center; }
.txt-italic 	     { font-style: italic; }
.uppercase		     { text-transform: uppercase; }
.bg-image 		     { background-repeat: no-repeat; background-size: cover; background-position: center center; }

//Reminder: Parent element needs to be position: relative;
.center-hv 		    { position: absolute; top: 50%; left: 50%; .translate(-50%; -50%); }
```
