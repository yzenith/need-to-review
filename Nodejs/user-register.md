# This file is for step of user-register with mogoose

###### load user model

```
const User = require('../../models/User');
const gravatar = require('gravatar');
const bcrypt = require('bcryptjs');

```
```
// need to install gravatar for grap avatar by email address
npm i gravatar --save
```


###### user-register API

```
@ route    user-register
@ des      This API is for user registration
@ access   public // which means there is no require to login
router.post('/user-registrer', (req,res) => {
	
	// verify if the email address had been used
	User.findOne({ email: req.body.email })
		.then(user => {
			if(user){ // this means the email does exsit
				return res.status(400).json({email: "Email Already Exsit"})
			} else {
				const avatar = gravatar.url(req.body.email, {
					s: '200' // Size
					r: 'pg' // Rating
					d: 'mm' // Default
				})

				const newUser = new User({
					name: req.body.name,
					email: req.body.email,
					<!-- avatar: avatar, -->
					avatar, // in ES6, this can be used as avatar,
					password: req.body.password
				});
				
				// this step is for hash the password
				bcrypt.genSalt(10, (err, salt) => {
					bcrypt.hash(newUser.password, salt, (err, hash) => {
						newUser.password = hash;
						newUser.save()
							.then(user => res.json(user))
							.catch(err => console.log(err))

					});

				});
			}
		})

	})

```



###### in server.js, we need to call bodyParser, otherWise the req.body.email will not be return right data

```
const bodyParser = require('body-parser'); // this is a build in module

// Body Parser middleware
app.use(bodyParser.urlencoded({extented:false})); 
	// This object will contain key-value pairs, where the value can be a string or array (when extended is false), or any type (when extended is true)
app.use(bodyParser.json()); // this is for only parsing json
```

#### in server.js the terminal will return warning about URL string parser
```
mongoose
    .connect(db,{ useNewUrlParser: true }) // adding option here
    .then(()=>{console.log('server connected')})
    .catch(err => console.log(err));
```


###### then use the postman visit localhost:5000/api/users/register with POST method

* you should also get data from mlab
