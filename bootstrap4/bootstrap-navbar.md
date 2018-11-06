# this file is tips for bootstrap4 navbar

* container class will make all element align center. but navbar is not in the container
* usually people put container class inside nav tag
    * _nav tag need to navbar class_
    * _navbar-light to control the color_
    * _navbar-expand-sm_ this one need to know what it is
        * this is the breakpoint to tigger collapse
            * sm means small screen trigger that

    ```
        <nav class="navbar navbar-expand-sm navbar-light bg-light">
            <div class="container"> // this will make navbar do not go very big
                <a class="navbar-brand" href="#">Navbar</a>
                <ul class="navbar-nav">
                    <li class="nav-item">
                        <a class="nav-link" href="#">Home</a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="#">About</a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link">Services</a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="#">Contact</a>
                    </li>
                </ul>
            <div>
        </nav>
    ```


* the following is th navbar with responsive style
    
     ```
        <nav class="navbar navbar-expand-md navbar-light bg-light"> //expand-md will tigger icon
            <div class="container">
                <a class="navbar-brand" href="#">Navbar</a>
                <button class="navbar-toggler" data-toggle="collapse" data-target="#navbarNav"> // button is added compare to regular one
                    <span class="navbar-toggle-icon"></span>
                </button>
                <div class="collapse navbar-colla[se" id="navbarNav"> // this is extra from regular one
                    <ul class="navbar-nav">
                        <li class="nav-item">
                            <a class="nav-link" href="#">Home</a>
                        </li>
                        <li class="nav-item">
                            <a class="nav-link" href="#">About</a>
                        </li>
                        <li class="nav-item">
                            <a class="nav-link">Services</a>
                        </li>
                        <li class="nav-item">
                            <a class="nav-link" href="#">Contact</a>
                        </li>
                    </ul>
                </div>
            <div>
        </nav>
    ```

* navbar with form
    * ml-auto to make elements go right
        ```
            <form class="form-inline ml-auto">
        ```
    * mr-auto to make elements go left


    ```
        <nav class="navbar navbar-expand-md navbar-light bg-light"> //expand-md will tigger icon
            <div class="container">
                <a class="navbar-brand" href="#">Navbar</a>
                <button class="navbar-toggler" data-toggle="collapse" data-target="#navbarNav"> 
                    <span class="navbar-toggle-icon"></span>
                </button>
                <div class="collapse navbar-colla[se" id="navbarNav"> 
                    <ul class="navbar-nav">
                        <li class="nav-item">
                            <a class="nav-link" href="#">Home</a>
                        </li>
                        <li class="nav-item">
                            <a class="nav-link" href="#">About</a>
                        </li>
                        <li class="nav-item">
                            <a class="nav-link">Services</a>
                        </li>
                        <li class="nav-item">
                            <a class="nav-link" href="#">Contact</a>
                        </li>
                    </ul>
                    <form class="form-inline ml-auto"> // this is added compare to response one
                        <input class="form-control" type="text" placeholder="Search">
                        <button class="btn btn-outline-success">Search</button>
                    </form>
                </div>
            <div>
        </nav>
    ```

* navbar with dropdown
    * similiar to dropdown button, but inside of navbar items

        ```
        <nav class="navbar navbar-expand-sm navbar-light bg-light">
            <div class="container"> // this will make navbar do not go very big
                <a class="navbar-brand" href="#">Navbar</a>
                <ul class="navbar-nav">
                    <li class="nav-item">
                        <a class="nav-link" href="#">Home</a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="#">About</a>
                    </li>
                    <li class="navitem dropdown"> // this is the inside dropdown menu
                        <a class="dropdown-toggle" data-toggle="dropdown">Dropdown</a>
                        <div class="dropdown-menu">
                            <a class="dropdown-item" href="#">Link1</a>
                            <a class="dropdown-item" href="#">Link1</a>
                            <a class="dropdown-item" href="#">Link1</a>
                        </div>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link">Services</a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="#">Contact</a>
                    </li>
                </ul>
            <div>
        </nav>
    ```
    