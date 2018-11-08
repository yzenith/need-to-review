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
         ``` 
         for example:  "<div class="btn-group"><button class="btn btn-primary"></button><button btn btn-secondary></button><button btn btn-primary></button></div>"
         ```
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
        ```
         <div class="dropdown">
           <button class="btn btn-primary dropdown-toggle" type="button" data-toggle="dropdown">
               My Dropdown
           </button>
           <div class="dropdown-menu">
               <a class="dropdown-item" href="#"> Link one </a>
               <a class="dropdown-item" href="#"> Link two </a>
               <a class="dropdown-item" href="#"> Link three </a>
            </div>
         <div>
         ```

#### SPLIT DROPDOWNS
* a little different between above
    * need to btn-group the split buttons first
    * working on the anyone you want to data-toggle & dropdown-toggle
        * put divider inside a tags
            * dorpdown-divider
* code snippet
    ```
     <div class="btn-group">
       <button class="btn btn-primary" type="button">My button</button>
      <button class="btn btn-secondary dropdown-toggle" type="button" data-toggle="dropdown">
          <span>Toggle Dropdown</span>
        </button>
       <div class="dropdown-menu">
           <a href="#" class="dropdown-item"> Link one </a>
           <a href="#" class="dropdown-item"> Link two </a>
           <div class="dropdown-divider"></div>
           <a href="#" class="dropdown-item"> Link three </a>
       </div>
     </div>
     ```

* Colors
    * navbar-light => this will control the text color for light theme? 
        * you can understand as navbar for light, so the text should be black
    * bg-dark => this will control background color
    * bg-sucess => green navbar
    * bg-primary => blue navbar

* fixed
    * fixed-top

        ```
            <nav class="navbar fixed-top navbar-dark bg-dark">
                <a href="#" class="navbar-brand">Navbar fixed top</a>
            </nav>
        ```
    * fixed-bottom
        * check above
    * sticky top
        * when the screen go down it will alway in the top
            you probably need offset, which can help navbar and sticky part not mess together

* NAVS
    * nav nav-pills

        ```
           <ul class="nav nav-pills">
                <li class="nav-item">
                    <a href="#" class="nav-link">Link1</a>
                </li>
                <li class="nav-item">
                    <a href="#" class="nav-link active">Link2</a>
                </li>
                <li class="nav-item">
                    <a href="#" class="nav-link">Link3</a>
                </li>
                <li class="nav-item">
                    <a href="#" class="nav-link">Link4</a>
                </li>
            </ul>
        ```
    * Horizontal Align
        * add justify-content-center to ul element above
    * right Align
        * add justify-content-end to ul element above
    * the default will to left
    * vertical
        * add flex-column to ul element
    * fill & justify
        * use nav-fill

#### list groups
* list-group 
    ```
        <ul class="list-group">
            <li class="list-group-item">My list item one</li>
            <li class="list-group-item">My list item two</li>
            <li class="list-group-item">My list item three</li>
            <li class="list-group-item">My list item four</li>
        </ul>
    ```
* list group links
    * list-group
        * list-group-item active or not

* contextual classes
    * list-group
        * list-group-item list-group-item-primary

* flush list group
    * list-group list-group-flush
        * list-group-item active or not
    * this will make whole list no borders

* Badge
    * list-group
        * list-group-item
            * this should be used for a link with how many posts

        ```
            <ul class="list-group">
                <li class="list-group-item">My list Item One</li>
                <li class="list-group-item">My list Item Two
                    <span class="badge badge-primary">30</span>
                </li>
                <li class="list-group-item">My List Item Three</li>
                <li class="list-group-item">My List Item four</li>
            </ul>
        ```
* BreadCrumb
    * this is for links go back to user profile, etc
        ```
            <ol class="breadcrum">
                <li class="breadcrum-item">
                    <a href="#">Home</a>
                </li>
            </ol>
            <ol class="breadcrum">
                <li class="breadcrum-item">
                    <a href="#">Home</a>
                </li>
                <li class="breadcrum-item active">Users</li>
            </ol>
            <ol class="breadcrum">
                <li class="breadcrum-item">
                    <a href="#">Home</a>
                </li>
                <li class="breadcrum-item">
                    <a href="#">Users</a>
                </li>
                <li class="breadcrum-item active">Brad</li>
            </ol>
        ```
* Forms
    * div inside form tag but parent of input tag
        * form-group => which will give margin-bottom 
        * form-control => stylish input tag
        * form-control-lg => make input show bigger
        * form-control-sm => smaller
        * form-text text-muted  => small message under input/ this will be like a note
        * readonly in input => then this input can not type anything
   
    * select / textarea
        * form-group on parent div
            * form-control on select tag

    * file input
        * form-group on parent div
            * form-control-file on file input
                * use small tag for help text which also need form-text and text-muted

    * custom file input
        * custom-file on parent div
            * custom-file-input on input
            * custom-file-lable
            ```
            <div class="custom-file">
                <input class="custom-file-input" id="myfile" type="file">
                <label class="custom-file-label" for="myfile">choose one</label>
            </div>
            ```
    * range
        * form-group
            * custom-range 
                * the range have nice attribute, look at below
                * min="1" max="5" step="1" value="1"
                    * min and max will represent the left to right
                    * step and value means each move how it changed
     
     * inline-form
        * form-inline on parent div tag
            * form-control on input

            * form-check for div tag on check function
                * form-check-label for label tag
                * form-check-input for check input

    * form row
        * form-row on parent div
            * col on lower level div
                * form-control on inside input

#### Validation

* form-group on parent div
    * form-control on input 

##### normally use javascript add this class
* is-valid / go green
* is-invalid / go red
* invalid-feedback on error message




#### input group

* input-group on parent div
    * input-group-prepend
        * input-group-text
    * form-control

    ```
    <div class="input-group">
        <div class="input-group-prepend">
            <span class="inout-group-text">
                @
            </span>
        </div>
        <input class="form-control" type="text" placeholder="Username">
    </div>
    ```
* input-group-append / this will let element stick behand, it is a oppstie way of prepend
    * prepend and append is used a lot of search box

#### alerts & progress bar

* works on login /logged out
    * alert alert-primary  // first alert should be need
    * alert alert-success
    * alert alert-danger
    * alert alert-info
    * etc...

* Dismissable alert
    * alert alert-success alert-dismissable 
        * class="close" date-dismiss="alert" // this will let alert disappear

        ```
        <div class="alert alert-success alert-dismissable">
            <button class="close" type="button" data-dismiss="alert">
                <span>&times;</span>
            </button>
            <strong>Dismissable</strong> Blog post added
        </div>
        ```

* extra content
    * alert alert-success
        * alert-heading
        
        ```
        <div class="alert alert-success">
            <h4 class="">Congrats!</h4>
            <p>askjdbkjsbgnsdfhgjkdsngkdfsngkjsndjfgksdnfjg</p>
            <hr>
            <p>jkasldkjfhsajkdhfkasjhdfkjsalhd</p>
        </div>
        ```

#### Progress Bar
* class="progrss" on parent div
    * class="progress-bar" style="width:35%" on lower level div
        * bg-success progrss-bar to change the color

    ```
    <div class="progress">
        <div class="progress-bar" style="width:35%">35%</div>
    </div>
    ``` 

* progress height
    * need style="height:xxpx" next to class="progress"

* striped
    * progress-bar-striped progress-bar

* animated
    * progress-bar-striped progress-bar progress-bar-animated


#### tables and pagination

* class="table"

* Inverse dark table
    * table table-dark 

* table head inverse
    * table class on parent
        * thead-dark on thead element

* striped table
    * table table-striped 
    
* Bordered-table
    * table table-bordered

* borderless table
    * table table-borderless

* hoverable
    * table table-hover //when mouse hover, it will show grey background

* contentual Class
    * table 
        * table-sucess on tr tag

* small table
    * table table-sm

* respponsive table
    * table-responsive on div parent level of table


#### pagination
* class="pagination" on ul tag
    * class="page-item" on li
        * page-link on a tag

        ```
        <nav>
            <ul class="pagination">
                <li class="page-item">
                    <a class="page-link">Previous</a>
                </li>
                <li class="page-item">
                    <a class="page-link">1</a>
                </li>
                <li class="page-item">
                    <a class="page-link active">2</a>
                </li>
                <li class="page-item">
                    <a class="page-link">3</a>
                </li>
                <li class="page-item">
                    <a class="page-link">Next</a>
                </li>
            </ul>
        </nav>
        ```
* center pagination
    * pagination justify-content-center / justify-content-end / pagination-lg
    
    * arrow as previous/next

        ```
        old one:
        <a class="page-link">Previous</a>

        change to:
        <span>&lasquo;</span>
        <span class="sr-only">Previous</span>

        and:
        <span>&rlasquo;</span>
        <span class="sr-only">Previous</span>
        ```

#### cards
* class="card" on top div
    * class="card-body" on lower div

* simple card structure
    * card style="width:20rem"
        * card-body
            * card-title
            * card-subtitle text-muted
            * card-text

* card with image
    * card
        * card-img-top //on img tag
            * there is an API so random img 
                ```
                https://source.unsplash.com/random/300x200
                ```
        * card-body
        * card-title
        * card-text

* card with header
    * card 
        * card-header
        * card-body
        * card-text

* header, footer center
    * card text-center
        * card-header
        * card-body
        * card-text
        * card-footer text-muted

* card with nav/tabs
    * card
        * card-header
            * nav nav-tabs card-header-tabs
                * nav-item
                    * nav-link
            * card-body
                * card-title
                * card-text

* image overlays
    * card
        * card-img
        * card-img-overlay // here do not use card-body
            * card-title
            * card-text

* background-color
    * card bg-primary
        * card-header
        * card-body
            * card-title
            * card-text

* card-outline
    * card border-outline-primary

* card-columns //responsive
    * card-columns
        * card
            * card-img-top img-fluid // what is the imgae fluid

        * card card-dark 
            * card-bodyquote
            * bodyquote-footer
                * source-title


#### media Object //not frequently used
* media 
    * media-body

##### nest media objects
* media-object 
    * media
        * media-body

* top aligned
    * media
        * media-body
    
* center aligned
    * media
        * align-self-end // on img 

##### media list
* list-unstyled //on ul tag
    * media // on li tag



#### jumptron
* jumptron text-center
    * display-4 //this is size
    * lead //on first paragragh
    * btn btn-primary btn-lg


* Fluid Jumptron   // this is will full wide
    * jumptron jumptron-fluid // on top level div
        * container // on lower div