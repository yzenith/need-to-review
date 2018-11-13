# This file is for tooltips

###### Tooltips

* data-toggle="tooltip" data-placement="top" title="Tooltip on top"
    > the title is the content of tooltip

###### you need script to load tooltips as following
```
<script>
    $('[data-toggle="tooltip"]').tooltip();
</script>
```



###### Tooltips with HTML

* id="hello" data-toggle="tooltip" data-placement="top" data-html="true" title="<h3>hello World</h3>"
    > there is the data-html="true" tag for html
    > data-html="false" will return the <h3>hello World</h3>


###### Trigger with JS (click effect)

```
<button class="btn btn-secondary" onclick="showTooltip()"> // this will show code above with id="hello" 
    show tooltip
</button>

// the onclick can use hideTooltip() and toggleTooltip()

<script>
    $('[data-toggle="tooltip"]').tooltip();

    function showTooltip() {
        $('#hello').tooltip('show');
    }
    function hideTooltip() {
        $('#hello').tooltip('hide');
    }
    function toggleTooltip() {
        $('#hello').tooltip('toggle');
    }
    
    // tooltip event
    $('#hello').on('show.bs.tooltip', function() {
        console.log('Tooltip Show');
    });
     $('#hello').on('shown.bs.tooltip', function() {
        console.log('Tooltip Shown');
    });
     $('#hello').on('hide.bs.tooltip', function() {
        console.log('Tooltip hide');
    });
     $('#hello').on('hidden.bs.tooltip', function() {
        console.log('Tooltip hidden');
    });
<script>
```

#######  tooltip events look up above

