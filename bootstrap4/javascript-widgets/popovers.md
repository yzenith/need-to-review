# This file is for bootstrap4 popovers

#### popover

```
<button class="btn btn-danger" data-toggle="popover" data-placement="top" data-content="sdfjsdnvkjdfngkjsnkjvndksjfngjksdf">
    Toggle popover
</button>

<button class="btn btn-primary" data-toggle="popover" data-placement="right" data-content="sdfjsdnvkjdfngkjsnkjvndksjfngjksdf">
    Toggle popover
</button>

<button class="btn btn-warning" data-toggle="popover" data-placement="bottom" data-content="sdfjsdnvkjdfngkjsnkjvndksjfngjksdf">
    Toggle popover
</button>

<button class="btn btn-info" data-toggle="popover" data-placement="left" data-content="sdfjsdnvkjdfngkjsnkjvndksjfngjksdf">
    Toggle popover
</button>



<script>
    // init popover
    $('[data-toggle="popover"]').popover();
</script>
```


#### Dismissible popover // which will disappeared when you click somewhere else

```
<button class="btn btn-primary" data-toggle="popover" data-placement="left" data-content="sdfjsdnvkjdfngkjsnkjvndksjfngjksdf" data-trigger="focus">
    Toggle popover
</button>
```

### control with JS

```
<button class="btn btn-secondart" onclick="showPopover()">
    Show Popover
</button>

<script>
    $('[data-toggle="popover"]').popover;

    function showPopover() {
        $('#hello').popover('show');
    }
    function hidePopover() {
        $('#hello').popover('hide');
    }
    function togglePopover() {
        $('#hello').popover('toggle');
    }

    // popover events, but what is this for?
    $('#hello').on('show.bs.popover', function(){
        console.log('Popover show')
    })
    // this process will be like tooltip
</script>
```

