# LESSer-Things
A collection of mixins and many other random things I find I use over and over. 


```less
.fs(@size:18px) { font-size:@size; }
.lh(@height:30px) { line-height:@height; }

//Reminder: Parent element needs to be position: relative;
.center-hv 		{ position: absolute; top: 50%; left: 50%; .translate(-50%; -50%); }
```
