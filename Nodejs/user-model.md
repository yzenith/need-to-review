# this file is API Routes & JWT Authentication
	#### user-model
	* create a folder call models inside routes folder

	```
		const mongoose = require('mongoose');
		const Schema = mongoose.Schema; 

		//create Schema
		const UserSchema = new Schema({
			name: {
				type: String, // String need to be capital
				required: true
			},
			email: {
				type: String,
				required: true
			},
			password: {
				type: String,
				required: true
			},
			avatar: {
				type: String,
				required: true
			},
			date: {
				type: Date, // now type need to capital
				default: date.now  // default to set the value
			}
		});

		module.exports = User = mongoose.model('users',UserSchema);
		// why here need mongoose.model
		// why it need to pass users and UserSchema
	```