# Javascript ES6 (Cheatsheets)


## variables

Scoped

* let
* cont 

Global (Avoid !)

* var 



```javascript
let name = 'Luke';

if (true) {  
  let name = 'Phil';
  console.log(name); // 'Phil'
}

console.log(name); // 'Luke'  
```

## types

primitives 

* Numbers - Integers, floats
* Strings - Any data under single quote, double quote or backtick quote
* Booleans - true or false value
* Null - empty value or no value
* Undefined - a declared variable without a value

non primitives

* objects
* functions
* arrays


## Template literals

```javascript
const message = `Hello ${name}`

```


## arrays

## destructuration / spreading


### destructuring

Arrays

```javascript
const [first, last] = ['Nikola', 'Tesla']
``` 


Objects

```javascript
let {title, author} = {
  title: 'The Silkworm',
  author: 'R. Galbraith'
}

```

```javascript
for (let {title, artist} of songs) {
  ···
}

```

### Spread


Override/add key visible with true value

```javascript
const options = {
  ...defaults,
  visible: true
}


```

## Functions

* arrow syntax
* default param
* rest parameter

```javascript
function greet({ name = 'Rauno' } = {}) {
  console.log(`Hi ${name}!`);
}

greet() // Hi Rauno!
greet({ name: 'Larry' }) // Hi Larry!
```


## classes

```javascript
class Circle extends Shape {

  // Constructor
  constructor (radius) {
    this.radius = radius
  }

  // Methods
  getArea () {
    return Math.PI * 2 * this.radius
  }
 

  // Calling superclass methods
  expand (n) {
    return super.expand(n) * Math.PI
  }
 

  // Static methods
  static createFromDiameter(diameter) {
    return new Circle(diameter / 2)
  }
}
```
 



## promise 

* callback
* promise : then / catch
* async / await

// async /  await service.getAll()


## module

* es2015 syntax


```javascript
//utils.js
export const myFunction = () => 'whatever'
export const myOtherFunc = () => 'myOther'
export default myMainFunc = () => 'IamDefault'
```

Named import 

```javascript
//caller app file
import {myFunction, myOtherFunc} from './utils'

console.log(myFunction())
console.log(myOtherFunc())
```

Default import 

```javascript
import myFunc from './utils';
myFunc();
```


## Some addition to standard lib

* Map

```javascript
var myMap = new Map(),
    keyObj = {},
    keyFunc = function () {};

myMap.set(keyObj, "value for keyObj");
myMap.set(keyFunc, "value for keyFunc");

myMap.get(keyObj);  // "value for keyObj"
myMap.get(keyFunc); // "value for keyFunc"

```

* Set

```javascript
var mySet = new Set();

mySet.add(5);
mySet.add("something");

mySet.has(5);                // true
mySet.has("some" + "thing"); // true
mySet.has(32);               // false
```