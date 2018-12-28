### This file will contain some basic concept of nodejs, which will be the reference in the future

##### how to visit an endopint and show html file?

```
app.get('/',(req,res)=>{
    res.sendFile(__dirname + '/views/index.html');  // need to figure it out __dirname or _dirname
})

// but this will need to set up another two basic things
app.use(morgan('common'));  // this will help log, so morgan is the logging middleware

app.use(express.static('public'));  // this will load static files first, if the static command not load, what will happened?

```


##### Set router for future use

```
app.use('/', recipeRouter);  // here need to use app.use, since router is a middleware

// in recipeRouter.js
router.get('/', (req,res)=>{
    res.json(Recipes.get()); // here they have Recipe.get(), but what is Recipes? is an object?
})
```


### some tips when you write a project

###### in server.js, load middleware should write in the top and use the middleware need to write to below, the bodyParser is depreciated, need to use app.use(express.json())


```
const express = require('express');
const morgan = require('morgan');
const blogpostsRouter = require('./blogpostsRouter.js');
const app = express();

// below is for middleware
app.use(morgan('common')); // if you do not use common then each request, there will be no log
app.use(express.json()); // missing this step, which should be used for parse the req body

app.use('/blog-posts', blogpostsRouter);


// below is for listening 
const port = 3000 || process.env.PORT;
app.listen(port, (req,res) => {
    console.log(` it's running on port 3000`)
})
```


### about router

###### router file need to use the same name in const, get,post,put,delete, and exports

```
const express = require('express');
// all name should be same
const router = express.Router();

// methods
router.get();
router.post();
router.put();
router.delete();

// exports
module.exports = router
```

###### about put method and delete method in POSTman

```
when put route is '/:id' it will be the same localhost:3000/blog-posts/xxcfsvcxvcxfbcb in url

'/:id'
'localhost:3000/blog-posts/xxcfsvcxvcxfbcb'

```