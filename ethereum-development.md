# Solidity + Ethereum

## Data types

`uint` - non-zero number (eg.. `uint(8)` to `uint(256)` in steps of `8`)

`string` - string of characters

`struct` - essentially functions. allows you to create more complicated data types

## Arrays

Two types of arrays, `fixed` and `dynamic`

*examples....*

```
// An array with 2 elements
uint[2] myFirstFixedArray;

// A string array with 5 elemnents
string[5] myCoolStringArray;

// A dynamic number array
uint[] myFirstDynamicArray;
```

You can also extend arrays to use other `struct` properties

## Working with structs and arrays

`arrays` and `structs` have methods like `.push()` and 

```
function createZombie(string memory _name, uint _dna) public {
        zombies.push(Zombie(_name, _dna));
    }
```

## Functions

Functions are declared with this syntax - `function name (type _paramName)` 

`memory` - required for all reference types including strings, structs, mappings, and arrays.

`public` - creates an automattic getter method for it so that other contracts can utilize the function/arrays.

`private` - creates a private function that is only accessible by your smart contract

```
function myFirstFunction (string memory _name, uint _dna) public {
    // start here
}

function _myPrivateFunctio (string memory _name, uint _dna) private {

}
```

#### Function return values


```
string greeting = "What's up partner?";

function sayHello() public returns (string memory) {
  return greeting;
}
```

#### Function modifiers

Function modifiers are functions that do something with a value instead of just `return` 

`view` - designates the function as read-only, not changing any data/values.

```
function sayHello() public view returns (string memory) {

}
```

`pure` - pure functions doesn't read from any state of the app. 

```
function _multiply(uint a, uint b) private pure returns (uint) {
  return a * b;
}


```

## Keccak256 and Typecasting

`keccak265()` - built in function that generates a random hash. 

Sometimes you need to convert data types. Typecasting allows you to 

```
uint8 a = 5;
uint b = 6;
// throws an error because a * b returns a uint, not uint8:
uint8 c = a * b;
// we have to typecast b as a uint8 to make it work:
uint8 c = a * uint8(b);
```
