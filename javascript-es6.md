# JavaScript - ES6 notes

## Arrow Functions
Arrow Functions are a better way to write functions.
```JavaScript
// in a regular function `this` doesn't always refer to what you think it does
function myFunction(name) {
 console.log(name);
}

myFunction('Brandon');
```

```JavaScript
// in an arrow function, `this` always refers to what's within the arrow function
const myFunction = (name) => {
  console.log(name);
}

myFunction('Brandon');
```


## Import/Export (modules)
If you're exporting one thing in a file, you can make it the default then import `'./person'`. Also called "named" exports.

No curly brace means you an name the `import` whatever you want.
```Javascript
// person.js
const person = {
  name: 'Brandon'
};

export default person
```

You can export more than 1 item by omitting `default` from the `export` statement.  `import {person, BaseData} from ./utility.js`

Curly braces specifically target exports
```Javascript
// utility.js
export const person = {
  name: 'Brandon'
}

export const BaseData = 10;
```

## Classes
Blueprints for objects.

Classes can contain properties, objects, or functions
```JavaScript
class Person {
  name: 'Brandon',
  shoes: ['Air Max 95', 'Yeezy Boosts', 'Chuck Taylors'],
  myFunction = () = > {...},
}
```

Classes can also inherit from one another.
```JavaScript
class Human {
  // A constructor() is a function that gets called the first time a class is invoked (called).
  constructor() {
    this.gender = 'male';
  }
}

class Person extends Human {
  // super(); ensures that the Parent class (Human) attributes are added to the Child class (Person) when the Child class is invoked.
  super();
  constructor() {
    this.name = 'Brandon';
    this.age = 31;
  }
}

const person1 = New Person();
```

## Classes, Properties, and Methods

Differences in Classes ES6 v ES7
```JavaScript
// ES6 syntax
constructor () {
  this.myProperty = 'Brandon';
}


// ES7 Syntax
myProperty = 'Brandon'; 
```


Difference in Methods ES6 v ES7
```JavaScript

```

## Spread and Rest operators

These are 3 dots. It's a Spread or a Rest depending on where it's being used.
`...` 

Spread - Used to split up array elements or object properties
```JavaScript
const newArray = [..oldArray,'1','2'];
const newObject = {...oldObject, newProp: 5 };
```

Rest - Used to merge a list of function arguments in an array
```JavaScript
function sortArgs(...args) {
  return args.sort();
}
```