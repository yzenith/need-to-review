### This file is talking about using Mocha and Chai to unit and API testing

##### Mocha is the test framework for test, and chai is Libiary

```
// in terminal under project folder, paste below script and ready for testing

mkdir mocha-chai-demo && cd mocha-chai-demo && npm init -y
npm install mocha --save-dev
echo "module.exports = function(a, b) {return a === b}" >> isEqual.js
mkdir test
touch test/test-is-equal.js

```

##### First creat mocha and get ready for chai

```
// so mocha's purpose is that, it will enable 'describe' and 'it' functions
const isEqual = require('../isEqual');  // module.exports = function(a,b){return a === b};
const expect = require('chai').expect; // expect for unit test

describe('isEqual', function(){  // note that "isEqual" used as string
    it('it should use valid input', function(){
        // for equalInputs
        const equalInputs = [
            [1,1],
            ['a','a'],
            [true,true]
        ];
        equalInputs.forEach(function(input){
            const answer = isEqual(input[0],input[1]);
            expect(answer).to.be.true; // but how to log the one return false
        });

        // for unEqualInputs
        const unEqualInputs = [
            [1,'a'],
            [2,true],
            [true,false],
            [1,2],
            ['a','b']
        ];
        unEqualInputs.forEach(function(input){
            const answer = isEqual(input[0],input[1]);
            expect(answer).to.be.false;
        });
    });
});

// then run "npm test" in terminal under mocha-chai-demo folder
```

### stradegy on testing
##### after you test all normal inputs, think of any edge inputs which could break the expection.


### another example:
##### from this example we know, if you want to throw an Error in testing, you have to expect(function(){isEqual}).to.throw(Error)

```
// import chai, declare expect variable
const expect = require('chai').expect;

// import adder
const adder = require('../adder');

// unit tests for our `adder` function
describe('adder', function() {

  // test the normal case
  it('should add two numbers', function() {
    // range of normal inputs, including
    // notable cases like negative answers
    const normalCases = [ // here is new way to make a test, input as an object
      {a: 2, b: 3, expected: 5},
      {a: 200, b: 2000, expected: 2200},
      {a: 2, b: -5, expected: -3}
    ];
    // for each set of inputs (a, b), `adder` should
    // produce the expected value
    normalCases.forEach(function(input) {
      const answer = adder(input.a, input.b);
      expect(answer).to.equal(input.expected); // here used to.equal(value)
    });
  });

it('should raise error if args not numbers', function() {
    // range of bad inputs where not both are numbers
    const badInputs = [
      ['a', 1],
      ['1', 2],
      [2, false]
    ];
    // prove that an error is raised for bad inputs
    badInputs.forEach(function(input) {
      expect(function() {
        adder(input[0], input[1]); // why here use function and not just adder()?
      }).to.throw(Error); // here used to.throw(Error), so where is the Error come from
    });
  });
});

```

##### trade each it statement as a condition when you do unit testing

```
const fizzBuzzer = require('../fizzBuzzer');
const expect = require('chai').expect;

describe('fizzBuzzer', function(){ // trade each condition as it statement
    // input % 15 == 0 will return 'fizz'
    it('it should return fizz-buzz when num % 15 == 0', function(){
        const rightInputs = [15,30,45,60];
        rightInputs.forEach(function(input){
            const answer = fizzBuzzer(input);
            expect(answer).to.equal('fizz-buzz');
        });
    });
    // input % 5 == 0 will return 'buzz'
    it('it will return "buzz" when input % 5 == 0', function(){
        const rightInputs = [5,10,20,25];
        rightInputs.forEach(function(input){
            const answer = fizzBuzzer(input);
            expect(answer).to.equal('buzz')
        });
    });
    // input % 3 == 0 will return 'fizz'
    it('it will return "fizz" when input % 3 == 0', function(){
        const rightInputs = [3,6,9,12,18];
        rightInputs.forEach(function(input){
            const answer = fizzBuzzer(input);
            expect(answer).to.equal('fizz');
        });
    });
    // input % 3 or 5 !=0 will return input
    it('it will return the input if input % 3 or 5 != 0', function(){
        const rightInputs = [2,4,7,8,11,13];
        rightInputs.forEach(function(input){
            const answer = fizzBuzzer(input);
            expect(answer).to.equal(input);
        });
    });
    // input is not num will throw error
    it('it will throw error if input is not a number', function(){
        const wrongInput = ['a',true,false,[1,2,3],{}];
        wrongInput.forEach(function(input){
            expect(function(){fizzBuzzer(input)}).to.throw(Error);
        });
    })
});
```

### API testing
##### the following is an example of API testing, it come with the runServer and closeServer function, which is a high level concept for promise, need to remember it can stop which situation happened.

```
const chai = require("chai");
const chaiHttp = require("chai-http");

const { app, runServer, closeServer } = require("../server");

// this lets us use *expect* style syntax in our tests
// so we can do things like `expect(1 + 1).to.equal(2);`
// http://chaijs.com/api/bdd/
const expect = chai.expect;

// This let's us make HTTP requests
// in our tests.
// see: https://github.com/chaijs/chai-http
chai.use(chaiHttp);

describe("Shopping List", function() {
  // Before our tests run, we activate the server. Our `runServer`
  // function returns a promise, and we return the that promise by
  // doing `return runServer`. If we didn't return a promise here,
  // there's a possibility of a race condition where our tests start
  // running before our server has started.
  before(function() {
    return runServer();
  });

  // although we only have one test module at the moment, we'll
  // close our server at the end of these tests. Otherwise,
  // if we add another test module that also has a `before` block
  // that starts our server, it will cause an error because the
  // server would still be running from the previous tests.
  after(function() {
    return closeServer();
  });

  // test strategy:
  //   1. make request to `/shopping-list`
  //   2. inspect response object and prove has right code and have
  //   right keys in response object.
  it("should list items on GET", function() {
    // for Mocha tests, when we're dealing with asynchronous operations,
    // we must either return a Promise object or else call a `done` callback
    // at the end of the test. The `chai.request(server).get...` call is asynchronous
    // and returns a Promise, so we just return it.
    return chai
      .request(app)
      .get("/shopping-list")
      .then(function(res) {
        expect(res).to.have.status(200);
        expect(res).to.be.json;
        expect(res.body).to.be.a("array");

        // because we create three items on app load
        expect(res.body.length).to.be.at.least(1);
        // each item should be an object with key/value pairs
        // for `id`, `name` and `checked`.
        const expectedKeys = ["id", "name", "checked"];
        res.body.forEach(function(item) {
          expect(item).to.be.a("object");
          expect(item).to.include.keys(expectedKeys);
        });
      });
  });

  // test strategy:
  //  1. make a POST request with data for a new item
  //  2. inspect response object and prove it has right
  //  status code and that the returned object has an `id`
  it("should add an item on POST", function() {
    const newItem = { name: "coffee", checked: false };
    return chai
      .request(app)
      .post("/shopping-list")
      .send(newItem)
      .then(function(res) {
        expect(res).to.have.status(201);
        expect(res).to.be.json;
        expect(res.body).to.be.a("object");
        expect(res.body).to.include.keys("id", "name", "checked");
        expect(res.body.id).to.not.equal(null);
        // response should be deep equal to `newItem` from above if we assign
        // `id` to it from `res.body.id`
        expect(res.body).to.deep.equal(
          Object.assign(newItem, { id: res.body.id })
        );
      });
  });

  // test strategy:
  //  1. initialize some update data (we won't have an `id` yet)
  //  2. make a GET request so we can get an item to update
  //  3. add the `id` to `updateData`
  //  4. Make a PUT request with `updateData`
  //  5. Inspect the response object to ensure it
  //  has right status code and that we get back an updated
  //  item with the right data in it.
  it("should update items on PUT", function() {
    // we initialize our updateData here and then after the initial
    // request to the app, we update it with an `id` property so
    // we can make a second, PUT call to the app.
    const updateData = {
      name: "foo",
      checked: true
    };

    return (
      chai
        .request(app)
        // first have to get so we have an idea of object to update
        .get("/shopping-list")
        .then(function(res) {
          updateData.id = res.body[0].id;
          // this will return a promise whose value will be the response
          // object, which we can inspect in the next `then` block. Note
          // that we could have used a nested callback here instead of
          // returning a promise and chaining with `then`, but we find
          // this approach cleaner and easier to read and reason about.
          return chai
            .request(app)
            .put(`/shopping-list/${updateData.id}`)
            .send(updateData);
        })
        // prove that the PUT request has right status code
        // and returns updated item
        .then(function(res) {
          expect(res).to.have.status(200);
          expect(res).to.be.json;
          expect(res.body).to.be.a("object");
          expect(res.body).to.deep.equal(updateData);
        })
    );
  });

  // test strategy:
  //  1. GET shopping list items so we can get ID of one
  //  to delete.
  //  2. DELETE an item and ensure we get back a status 204
  it("should delete items on DELETE", function() {
    return (
      chai
        .request(app)
        // first have to get so we have an `id` of item
        // to delete
        .get("/shopping-list")
        .then(function(res) {
          return chai.request(app).delete(`/shopping-list/${res.body[0].id}`);
        })
        .then(function(res) {
          expect(res).to.have.status(204);
        })
    );
  });
});

```