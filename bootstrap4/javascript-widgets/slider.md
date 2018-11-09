# This file is for Bootstrap 4 Javascript section

### Carousel Slider

#### simple slider
```
<div class="carousel slide mb-5" data-ride="carousel" id="slider1">
    <div class="carousel-inner">
        <div class="carousel-item active"> //active for first image
            <img class="d-block img-fluid" src="https://source.unsplash.com/random/300x200" alt="first Slider">  // img-fluid to keep the size when it on different size screens
        </div>
        <div class="carousel-item">
            <img src="https://source.unsplash.com/random/300x200" alt="first Slider">
        </div>
        <div class="carousel-item">
            <img src="https://source.unsplash.com/random/300x200" alt="first Slider">
        </div>
    </div>
</div>
```


#### slider with control
```
<div class="carousel slide mb-5" data-ride="carousel" id="slider2">
    <div class="carousel-inner">
        <div class="carousel-item active"> //active for first image
            <img class="d-block img-fluid" src="https://source.unsplash.com/random/300x200" alt="first Slider">  // img-fluid to keep the size when it on different size screens
        </div>
        <div class="carousel-item">
            <img src="https://source.unsplash.com/random/300x200" alt="first Slider">
        </div>
        <div class="carousel-item">
            <img src="https://source.unsplash.com/random/300x200" alt="first Slider">
        </div>
    </div>
    <!--control--->
    <a href="#slider2" class="carousel-control-pre" data-slider="prev">
        <span class="carousel-control-prev-icon"></span>
    </a>

    <a href="#slider2" class="carousel-control-next" data-slider="next">
        <span class="carousel-control-next-icon"></span>
    </a>
</div>
```


#### slider with indicators   //the button down the image

```
<div class="carousel slide mb-5" data-ride="carousel" id="slider3">
    // here to add indicator
    <ol class="carousel-indicators">
        <li class="active" data-target="#slider3" data-slide-to="0"></li>
        <li data-target="#slider3" data-slide-to="1"></li>
        <li data-target="#slider3" data-slide-to="2"></li>
    </ol>

    <div class="carousel-inner">
        <div class="carousel-item active"> //active for first image
            <img class="d-block img-fluid" src="https://source.unsplash.com/random/300x200" alt="first Slider">  // img-fluid to keep the size when it on different size screens
        </div>
        <div class="carousel-item">
            <img src="https://source.unsplash.com/random/300x200" alt="first Slider">
        </div>
        <div class="carousel-item">
            <img src="https://source.unsplash.com/random/300x200" alt="first Slider">
        </div>
    </div>
    <!--control--->
    <a href="#slider3" class="carousel-control-pre" data-slider="prev">
        <span class="carousel-control-prev-icon"></span>
    </a>

    <a href="#slider3" class="carousel-control-next" data-slider="next">
        <span class="carousel-control-next-icon"></span>
    </a>
</div>
```

#### slider with captions

```
<div class="carousel slide mb-5" data-ride="carousel" id="slider4">
    // here to add indicator
    <ol class="carousel-indicators">
        <li class="active" data-target="#slider3" data-slide-to="0"></li>
        <li data-target="#slider3" data-slide-to="1"></li>
        <li data-target="#slider3" data-slide-to="2"></li>
    </ol>

    <div class="carousel-inner">
        <div class="carousel-item active"> //active for first image
            <img class="d-block img-fluid" src="https://source.unsplash.com/random/300x200" alt="first Slider">  // img-fluid to keep the size when it on different size screens
            // here is the caption
            <div class="carousel-caption d-none d-md-block">
                <h3>Slider one</h3>
                <p>xxdfasfrgdsgdgfasdgfsdfgsdf</p>
            </div>
        </div>
        <div class="carousel-item">
            <img src="https://source.unsplash.com/random/300x200" alt="first Slider">
            // here is the caption
            <div class="carousel-caption d-none d-md-block">
                <h3>Slider two</h3>
                <p>xxdfasfrgdsgdgfasdgfsdfgsdf</p>
            </div>
        </div>
        <div class="carousel-item">
            <img src="https://source.unsplash.com/random/300x200" alt="first Slider">
            // here is the caption
            <div class="carousel-caption d-none d-md-block"> // this will only show md screen
                <h3>Slider three</h3>
                <p>xxdfasfrgdsgdgfasdgfsdfgsdf</p>
            </div>
        </div>
    </div>

    <!--control--->
    <a href="#slider4" class="carousel-control-pre" data-slider="prev">
        <span class="carousel-control-prev-icon"></span>
    </a>

    <a href="#slider4" class="carousel-control-next" data-slider="next">
        <span class="carousel-control-next-icon"></span>
    </a>
</div>
```


#### how to change the slider interval time // slider change time
```
in the bottom of script tag, add following scripts
This should be use jQuery
<script>
    $('.carousel').carousel({
        interval: 1000,
        keyboard: true,
        pause: 'hover',
        wrap: true   // when reach end go back to first slider
    });

    $('#slider4').on('slide.bs.carousel', function(){
        console.log('Slider!!')  // this will happened when slider run each time on console
    });

    $('#slider4').on('slid.bs.carousel', function(){
        console.log('Slid!!')  // this will happened when slider finish run
    });

</script>
```