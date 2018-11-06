# This file contains all the keypoints about bootstrap4

* there are four cdn should be linked 
    * bootstrap css
    * bootstrap slim
    * bootstrap popper
    * bootstrap min
### header,paragragh, text transform
* header
    * h5 class="h1"
        * which will make h5 element as big as h1
    * h1 class="display-1"
        * which will make h1 element much bigger to display, there are four displays
        * _**display-1**_ class: biggest
        * _**display_-2**_ class: second biggest
        * _**display-3**_ class: smaller
        * _**display-4**_ class: smallest
* paragragh
    * p class="lead"
        * lead class will make more **font weight**
    * p class="text-monospace"
        * help make monospace style
    * p class="font-weight-bold"
        * font-weight-bold
        * font-weight-normal
        * font-italic
* Text transform
    * class="text-lowercase"
    * class="text-uppercase"
    * class="text-capitalize"
* blockquote
    * class="blockquote"
    * class="blockquote text-right"
    * class="blockquote-footer"
        > this is for blockquote footer section
* turn few paragraghs to one line with ...
    * class="text-truncate"
* remove bullit point from unorder list
    * class="list-unstyled"
* list inline
    * class="list-inline" to ul element
    * class="list-inline-item" to li element

#### Text alignment
* justify, left, right, center
    * class="text-justify"
    * class="text-center"
    * class="text-right"
    * class="text-left"
* responsive align
    * class="text-sm-right"
    * class="text-md-right"
    * class="text-lg-right"
* vertical alignment
    * class="align-baseline"
    * class="align-bottom"
    * class="align-middle"
    * class="align-top"
    * class="align-text-top"

#### block
* inline
    * class="d-inline"
* block 
    * class="d-block"
* inline block
    * class="d-inline-block"

#### float and postion
* float
    * class="float-left"
    * class="float-right"
    * class="float-none"
* response float
    * class="float-sm-right"
    * class="float-lg-none"
    * class="float-sm-left"
* clearfix
    * class="clearfix"
    * put clearfix in the float element parent element 
    * for example: "<div class="bg-success clearfix"><button class="float-left">xxxxleft</button><button class="float-right">xxxxright</button></div>"

#### fix positoning
* top
    * class="fixed-top"
* stick postion
    * class="sticky-top"
        * this will be scroll down with same postion
* class="fixed-bottom"

#### text color
* primary
    * class="text-primary"
* secondary
    * class="text-secondary"
* info
    * class="text-info"
* warning
    * class="text-warning"
* danger
    * class="text-danger"
* light
    * class="text-light"
* dark
    * class="text-dark"
* white
    * class="text-white"
* text-muted
    * class="text-muted"
        * this color is same with secondary
* black 50
    * class="text-black-50"
* white 50
    * class="text-white-50"

#### link color
* primary
    * class="text-primary"
        * this will be same as text color but it is better inside of a tag

#### background color
* primary
    * class="bg-primary text-white"
        * this will be same as text color and link color, but it better set text color as well
* secondary
    * class="bg-secondary"
* success
    * class="bg-success"
* transparent
    * class="bg-transparent"
* invisible
    * class="invisible"
        * this is different with display: none, invisible means this element still there but not visible

#### spacing
* margin bottom
    * no margin
        * class="mb-0"
    * mb-1
        * class="mb-1"
        * this will based on documentation
    * mb-2
        * class="mb-2"
        * this is default?
    * mb-3
        * class="mb-3"
    
* mb means bottom, so mt, ml, mr, mx, my means?
    * m means margin
    * mt means margin top
    * ml means margin left
    * mr means margin right
    * mx means left and right
    * my means top and bottom
    * m means all side
* p means padding
    * pb means padding bottom
    * pt means padding top
    * pl means padding left
    * pr means padding right
    * px means padding left & right
    * py means padding top & bottom
    * p means all side
* Horizontal center
    * mx-auto
        * this is use margin to make center?

#### sizing adn borders
* width
    * class="w-25"
        * means width: 25%
    * class="w-50"
        * means width: 50%
    * class="w-75"
        * means width: 75%
    * class="w-100"
        * means width: 100%
    * class="w-auto"
        * means width: 
* height
    * class="h-25"
    * h-50
    * h-75
    * h-100
    * h-auto
        * auto will be the default, normally it will not change anything
        * those height will be same as width
        * the parent div need to set up height px, for example: 300px
* borders
    * border
        * regular border
    * border-top
    * border-right
    * border-bottom
        * all those are class name, which means have border to top, left, right side
* border colors
    * border 
        * all the following will give border color by bootstrap setting
        * border-primary
        * border-secondary
        * border-warning
        * border-info
        * border-danger
        * border-light
        * border-dark
* border redius
    * border
        * rounded
            * rounded
            * rounded-top
            * rounded-bottom
            * rounded-circle
            * rounded-left
            * rounded-right
            * rounded-0
                * the rounded-0 will take the radius away

#### breakpoints
* all devices breakpoints reference
    * min-width: 576px small
        * max-width:575px
            * extra small 
        * max-width: 767px
        * max-width: 991px
        * max-width: 1191px
    * min-width: 768px md
    * min-width: 992px large
    * min-width: 1200px extra large
* " @media () {} "
    

#### Button & Button group
* before use button on bootstrap, it need **btn** class first
* color 
    * btn btn-primary
        * if you just use btn-primay, it will just give link color
    * btn btn-secondary
    * btn btn-success
    * btn btn-info
    * btn btn-warning
    * btn btn-danger
    * btn btn-whtie
    * btn btn-dark
    * btn btn-link
        * this is only for link
    ###### button tags/types
    * "<a href="#" class="btn btn-primary">"
        * this will make a link looks like button
    * " <input class="btn btn-warning">"
        * this means they can worked on different types
* outline button
    * this will make button's border and text have same color and background white
    * btn btn-outline-primary
    * btn btn-outline-secondary
    * btn btn-outline-success
    * btn btn-outline-warning
    * btn btn-outline-info
    * btn btn-outlin-light


#### Button Size
* btn btn-lg
* btn btn-sm
* btn btn-block
    * this will make the button almost full width

#### Button states
* btn btn-primary active
* btn btn-primary disable
    * can not click
* data-toggle="button"
    * this will make button change color when click

#### Button group
* btn-group
    * this need to use in div element, in another word, it should be used in parent level
        * for example:  "<div class="btn-group"><button class="btn btn-primary"></button><button btn btn-secondary></button><button btn btn-primary></button></div>"
        * all child level buttons will be align together in a line

#### Button toolbar
* btn-toolbar
    * this will be top level of button-group
    * which can help orangize few button groups, make them in a line

#### Vertical Group
* btn-group-verical
    * this is should be on buttons's parent div

#### drop downs
* for example, there is a div element, whcih includes a button and another div which contains three a tags
    * class="dropdown" on top level div
    * class="btn btn-primary dropdown-toggle" and data-toggle="dropdown" on button
    * class="dropdown-menu" on inside div
        * class="dropdown-item" on a tags

    * code snippet
    > <div class="dropdown">
    >   <button class="btn btn-primary dropdown-toggle" type="button" data-toggle="dropdown">
    >       My Dropdown
    >   </button>
    >   <div class="dropdown-menu">
    >       <a class="dropdown-item" href="#"> Link one </a>
    >       <a class="dropdown-item" href="#"> Link two </a>
    >       <a class="dropdown-item" href="#"> Link three </a>
    >    </div>
    > <div>

#### SPLIT DROPDOWNS
* a little different between above
    * need to btn-group the split buttons first
    * working on the anyone you want to data-toggle & dropdown-toggle
        * put divider inside a tags
            * dorpdown-divider
* code snippet
> <div class="btn-group">
>   <button class="btn btn-primary" type="button">My button</button>
>   <button class="btn btn-secondary dropdown-toggle" type="button" data-toggle="dropdown">
>       <span>Toggle Dropdown</span>
>   </button>
>   <div class="dropdown-menu">
>       <a href="#" class="dropdown-item"> Link one </a>
>       <a href="#" class="dropdown-item"> Link two </a>
>       <div class="dropdown-divider"></div>
>       <a href="#" class="dropdown-item"> Link three </a>
>   </div>
> </div>