### This file is for test section

##### Test will help maintain the new code if the mew code works, ie. if the code will return right result

##### there will be two part of testing, unit testing and API testing

##### CI or continue itegration is a good method developing sofeware

##### local => Github & TravisCI => Heroku



### Promise

##### why need promise, since callback function is hard to track when they nesting, ie. 

```
console.log('Inside first setTimeout'); // show after 1 sec
  setTimeout(function() {
    console.log('Inside second setTimeout'); // show after 2 sec
    setTimeout(function() {
      console.log('Inside third setTimeout'); // show after 3 sec
    }, 1000);
  }, 1000);
}, 1000);

console.log('After calling setTimeout');


// so promise will be like below:
const timeoutPromise = new Promise((resolve, reject) => {
  setTimeout(function () {
    resolve('Success!'); // this is the msg will return 1 sec later
  }, 1000);
});

timeoutPromise
  .then(msg => {
    console.log(msg);
  });


const timeOutPromise = new Promise((resolve,reject) => { // Promise P has to be Capital
    setTimeout(function(){ // Timeout is the keyword
        resolve('I have to write few times') // resolve should be right writing
    },1000);
});

timeOutPromise
    .then(msg => {
        console.log(msg)
    })
    .then(()=>{
        console.log(this is the second msg);
    })
```

###### how to pass the value from first then to following then?

```
const timeoutPromise = new Promise((resolve, reject) => {
  setTimeout(function () {
    resolve('Success!');
  }, 1000);
});

timeoutPromise
  .then(msg => {
    console.log(msg);
    return 'Value from first .then()';
  })
  .then(result => {
    console.log(result);
  });

  // this will return 
  // Success!
  // Value from first .then()
```


##### the reject Promise will stop the subsequent .then(), and pass the value to .catch()

```
const timeoutPromise = new Promise((resolve, reject) => {
  setTimeout(function () {
    reject('only turn reject!');
  }, 1000);
});

timeoutPromise
  .then(msg => { // not excute
    console.log(msg);
    return 'Value from first .then()';
  })
  .then(result => { // not excute
    console.log(result);
  })
  .catch(err => { // the err will be the value from reject()
    console.log(err);
  });

```


###### if there are two Promise, you want to pass the second Promise, then you need to return the second Promise in previous .then()

```
const timeoutPromise = new Promise((resolve, reject) => {
  setTimeout(function () {
    resolve('Success!');
  }, 1000);
});

const anotherPromise = new Promise((resolve, reject) => {
  setTimeout(function () {
    resolve('Another success!');
  }, 1000);
});

timeoutPromise
  .then(msg => {
    console.log(msg);
    return anotherPromise; // here to pass the anotherPromise to next .then()
  })
  .then(promise => {
    console.log(promise);
  })
  .catch(err => {
    console.log(err);
  });

```