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