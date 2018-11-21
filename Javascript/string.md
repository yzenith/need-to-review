# The following tips is very important

### String method

#### str.split() method

1. get words into an array from str

```
// split by 'space'
str.split(' ')
```

2. get chars from str

```
// split by ''
str.split('')
```

3. copy the whole string to the array

```
// split empty
str.split()
```

### string run as array
1. return the value charatar

```
var text = 'asdfasdfasd';
text.charAt('a');
```

2. find the index of a charatar

```
var text = 'asdfasdf';
text.indexOf('a'); //this will return the first index
text.lastIndexOf('a'); // this will return the last index, first and last can work together to find duplicate
```

3. condition if a charatat exsit

```
var text = 'asddfgrfghfghfg';
return text.includes('a'); // this will return true or false
```