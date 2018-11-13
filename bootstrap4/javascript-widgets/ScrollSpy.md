# This file is for ScrollSpy

#### ScrollSpy will be like anchor text, when you click on the anchor you, the browser will show that part

```
<div class="container">
    <nav class="navbar fixed-top navbar-expand-sm navbar-light bg-light mb-3" id="main-nav">
        <div class="container">
            <a class="navbar-brand" href="#">Navbar</a>
            <ul class="navbar-nav">
                <li class="nav-item">
                    <a class="nav-link" href="#welcome">Welcome</a>
                </li>
                <li class="nav-item">
                    <a class="nav-link" href="#about">About</a>
                </li>
                <li class="nav-item">
                    <a class="nav-link" href="#services">Services</a>
                </li>
            </ul>
        </div>
    </nav>
</div>

<section id="welcome">
    <h3>Welcome</h3>
    <p>sdfjaskjhfrueifhkjsdhfkahsdklfhakjf</p>
</section>

<section id="about">
    <h3>Welcome</h3>
    <p>sdfjaskjhfrueifhkjsdhfkahsdklfhakjf</p>
</section>

<section id="services">
    <h3>Welcome</h3>
    <p>sdfjaskjhfrueifhkjsdhfkahsdklfhakjf</p>
</section>


// here is the part to make the auto-scroll smooth animation 
<script>
    $('body').scrollspy({target: '#main-nav'}); // this will make active and highlighted link

    // add smooth scrolling, you can reuse it in the future
    $('#main-nav a').on('click', function(e){
        //check for a hash value
        if(this.hash != '') {
            // prevent default behavior
            e.preventDefault();

            // Store hash
            const hash = this.hash

            // Animate smooth scroll
            $('html, body').animate({
                scrollTop: $(hash).offset().top
            }, 900, function() {
                // add hash to url after scroll
                window.location.hash = hash;
            })
        }
    })
</script>
```