# This file is for Bootstrap4 grid system

#### responsive grid

######check the code below:

```
<div class="row">  //row will make this div tag has 12 column wide
    <div class="col-sm-6 col-md-8 col-lg-9 col-xm-10" style="border: 1px solid #333">
        <ul>
            <li>6 column on small screens</li>
            <li>8 column on medium screens</li>
            <li>9 column on large screen</li>
            <li>10 column on extra large screen</li>
        </ul>
    </div>
    <div class="col-sm-6 col-md-4 col-lg-3 col-xl-2" style="border:1px solid #333">
        <ul>
            <li>6 column on small screens</li>
            <li>4 column on medium screen</li>
            <li>3 column on large screen</li>
            <li>2 column on extra large screen</li>
        </ul>
    </div>
</div>
```

###### Equal Width 

* row // which is make 12 column for this div tag
    * col   // will make Equal width with other div with col class
    * col
    * col
    * col


###### Equal with mutip row

* row 
    * col
    * col
    * w-100 //this will one stack, still stay with Equal column
    * col
    * col

###### auto layout

* row
    * col    // always take rest
    * col-6  // always take 6/12
    * col-4   // always take 4/12


###### Equal width stacked

* row
    * col-sm  // or col-sm-12 
    * col-sm  // they will stack on small screens
    * col-sm


###### Ordering

* row
    * col order-3  // this will go the end
    * col order-2
    * col order-1


###### offsetting

* row
    * col-md-6 offset-md-3  // push over md-3 space, this will be more like margin-auto

* row 
    * col-md-4
    * col-md-4 offset-md-4 // push over this column to the 
    
* row
    * col-md-3 offset-md-3
    * col-md-3 offset-md-3

###### nesting

* row    // nest should be working on some case
    * col-sm-9
        * row
            * col-8 col-sm-6
            * col-4 col-sm-6



#### Grid Alignment

###### Vertical Alignment

* row align-items-start  // this is the top alignment of default
* row align-items-center // this is will help go center
* row align-items-end    // this is will go right

###### Vertical Alignment Individual Cols

* col align-self-start // top by default
* col align-self-center 
* col align-self-end


###### Horizontal Aligned cols

* row justify-content-start
* row justify-content-center
* row justify-content-end
* row justify-content-around  // add spacing on each element
* row justify-content-between  // put spacing between/middle each element

###### Column wrapping & no Gutters

* row no-gutters // this will make each column no space between
    * col-9 
    * col-4
    * col-6 