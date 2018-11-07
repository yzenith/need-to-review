# this markdown file is for nodejs basic file

* const port = process.env.PORT || port
	* "app.listen(port, (req,res) => console.log(`listen on ${port}`))"
	> this syntax is for whatever port enviorment use or you defined
* const express = require('express');
	* const app = express();
	> this step is to make express available
* app.get("/", (req,res) => {});
	#### this is the home route from express
* npm script
	#### this will make "node run dev" or "node run" worked with certain command
	* in the package.json file, there is proeprty call "script" which can help make that
	> here is an example: "start": "node server"; "dev": "nodemon server"
	> there is one thing you need to know, running nodemon, you need to use _**"npm run server" **_ 
* mongoose to connect server
	* "const mongoose = require('mongoose');"
	> this snippet will be show up in server.js
	* "const db = require('./path/key.js').mongoURL"
	> this will help get the string and ready to connect
	* "mongoose.connect(db).then(()=>{console.log('mongodb connected')}).catch(err => console.log(err))"
	> this is the last step to connect mongodb
	#### the following is the steps again
	1. step one: create mlab connection string object
	2. pass the connection string to **mongoose.connect()**
	3. use .then().catch() to finish the proccess