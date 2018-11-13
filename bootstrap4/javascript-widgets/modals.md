# This file is for modals

#### modals trigger // so what is modals? you can trade it as popup, you can put any content inside it

```
<button class="btn btn-primary" data-toggle="modal" data-target="#myModal">
    Lanch modal
</button>


// Modal
<div class="modal" id="myModal">
    <div class="modal-dialog">
        <div class="modal-content">
            <div class="modal-header">
                <h5 class="modal-title">Modal Title</h5>
                <button class="close" data-dismiss="modal">&times;</button>
            </div>
            <div class="modal-body">
                asdjkfghlkasjfhgkjlsdfhglkjsdhfglkjhsdkjfghskdjl
            </div>
            <div class="modal-footer">
                <button class="btn btn-secondary" data-dismiss="modal">
                    Close
                </button>
            </div>
        </div>
    </div>
</div>

```


#### Login Modal trigger

```
<button class="btn btn-dark" data-toggle="modal" data-target="#loginModal">
    Login
</button>


// Modal
<div class="modal" id="loginModal">
    <div class="modal-dialog">
        <div class="modal-content">
            <div class="modal-header">
                <h5 class="modal-title">Modal Title</h5>
                <button class="close" data-dismiss="modal">&times;</button>
            </div>
            <div class="modal-body">
                <form>
                    <div class="form-group">
                        <label for="username">Username</label>
                        <input type="text" class="form-control" placehoder="Username">
                    </div>
                    <div class="form-group">
                        <label for="password">Password</label>
                        <input type="password" class="form-control" placehoder="password">
                    </div>
                </form>
            </div>
            <div class="modal-footer">
                <!-- <button class="btn btn-secondary" data-dismiss="modal">
                    Close
                </button> -->
                 <button class="btn btn-primary" data-dismiss="modal">
                    login
                </button>
            </div>
        </div>
    </div>
</div>

```