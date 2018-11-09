# this file is for collapse & accordion

#### button with collapse
```
<button class="btn btn-primary d-block mb-4" data-toggle="collapse" data-target="#collapse-btn-1">Read More</button>

<div class="collapse mb-5" id="collapse-btn-1">
    <div class="card">
        <div class="card-body">
            asdhfaiughbaskdjlbngsldfiugbksjdbgaiulbgfksjldbfgsjldbfgklsdbfgklsdbfgk
        </div>
    </div>
</div>
```


#### accordion

* accordion
    * card
        * card-header
            * #collapse1 data-parent="#accordion" data-toggle="collapse"
            * collapse show

```
<div id="accordion">
      <div class="card">
        <div class="card-header">
          <h5>
            <a href="#collapse1" data-parent="#accordion" data-toggle="collapse">
              Collapse One
            </a>
          </h5>
        </div>

        <div id="collapse1" class="collapse show">
          <div class="card-body">
            Lorem ipsum dolor sit amet, consectetur adipisicing elit. Veritatis ea iste a doloremque, cumque, debitis eum vel ipsum architecto
            aut, recusandae totam ullam aperiam. Nesciunt expedita officiis animi quam corporis optio inventore facilis sint
            et nulla in, repellat debitis dolor at nisi quo, unde temporibus. Quos nisi nostrum officia, illo.
          </div>
        </div>
      </div>

      <div class="card">
        <div class="card-header">
          <h5>
            <a href="#collapse2" data-parent="#accordion" data-toggle="collapse">
              Collapse Two
            </a>
          </h5>
        </div>

        <div id="collapse2" class="collapse">
          <div class="card-body">
            Lorem ipsum dolor sit amet, consectetur adipisicing elit. Veritatis ea iste a doloremque, cumque, debitis eum vel ipsum architecto
            aut, recusandae totam ullam aperiam. Nesciunt expedita officiis animi quam corporis optio inventore facilis sint
            et nulla in, repellat debitis dolor at nisi quo, unde temporibus. Quos nisi nostrum officia, illo.
          </div>
        </div>
      </div>

      <div class="card">
        <div class="card-header">
          <h5>
            <a href="#collapse3" data-parent="#accordion" data-toggle="collapse">
              Collapse Three
            </a>
          </h5>
        </div>

        <div id="collapse3" class="collapse">
          <div class="card-body">
            Lorem ipsum dolor sit amet, consectetur adipisicing elit. Veritatis ea iste a doloremque, cumque, debitis eum vel ipsum architecto
            aut, recusandae totam ullam aperiam. Nesciunt expedita officiis animi quam corporis optio inventore facilis sint
            et nulla in, repellat debitis dolor at nisi quo, unde temporibus. Quos nisi nostrum officia, illo.
          </div>
        </div>
      </div>
    </div>
  </div>
```


* // this one I need to copy the soure file code