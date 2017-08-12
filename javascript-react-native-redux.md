# React Native & Redux

Notes on React Native and Redux that were taken while completing the "Complete React Native and Redux" course by Stephen Grider (@ste_grider).

## Introduction

These notes assume you have already installed NodeJS and are using a text editor such as Atom, Sublime, or Notepad++.

## Environment Setup

Setup for React Native has been made very simple by the team at @facebook. Detailed instructions can be found -- https://facebook.github.io/react-native/releases/0.21/docs/getting-started.html

These notes assume you already have npm/yarn installed. 

Install xCode

Insatll Android Studio

`react-native init projectname`

### Babel


### WebPack


### eslint

Add eslint to the project

`yarn add eslint`

Add `.eslintrc` file


## Application Setup

3 Steps to creating components

1. Import libraries
2. Make Component
3. Make Component available to other parts of app

```Javascript
// Import Libraries
import { React } from 'react';
import { AppRegistry, Text } from 'react-native';

// Creates the main component
const App = () => {
  return (
      <Text>Hello World!</Text>
  )
};

// Render to the device
AppRegistry.registerComponent('projectname', () => App);
```

## Components

Functional vs. Class-Based

Functional -- garden hose/pipe (one way). Data in, JSX out. Basically just used to display information. Presentational component.

```JavaScript
const Header = () => {
	return <Text>Hi There!</Text>
}
```

Class-Based -- Used for fetching data and used for fetching large components. Gives you the ability to add helper methods.

When writing a class based component, you must define exactly 1 method -- `render()`, that returns some amount of JSX.

```JavaScript
class Header extends Component {
	render () {
		return <Text>Hi There!</Text>
	}
}
```

Components have ***LIFECYCLE METHODS***

When something is getting ready to render to a screen, use a method call -- `componentWillMount()` {}

```JavaScript
class Header extends Component {
	
	componentWillMount() {

  }

	render () {
		return <Text>Hi There!</Text>
	}
}
```

## Props

When we want to pass variables from parent component to child component we use `props`

Passing props to the interface is a core component of React and React Native. Props make component resuability possible.

Prop names are completely arbitrary. They can be called whatever you want.



## State

`state` - a plain javascript object used to record, and respond to user-triggered events. `state` is typically found within a lifecycle method eg.. `componentDidMount(){}` or within a helper method eg.. `onButtonPressed () {}`

Whenever you're using state, a default property must be set. `state = { stateName: 'value' }` It needs to be set in the 

````JavaScript

onButtonPress () {
  const { email,password } = this.state;

  this.setState({ error: '' });
  
  firebase.auth().signInWithEmailAndPassword(email, password)
  .catch(() => { 
    firebase.auth().createUserWithEmailAndPassword(email, password)
    .catch(()=> { 
      this.setState({ error: 'Invalid email and/or password.' }); 
      console.log(this.state.error);
    });
  }); 
}
````

When we need to change what a component shows, call `this.setState()`.

`this.setState()` is automatically implemented via the `Component` class. The purpose of `this.setState()` is to update our component state and say "Hey, here's some new data, we need to re-render the component with the new data".

```JavaScript
this.setState({ albums : data.response }); // Good - Update the albums object with the data from the request

this.state = {}; // Good - only use this.state = {} when setting initial state.

this.state = { albums : data.response }; // BAD - don't do. 
```

DIFFERENCE BETWEEN `state` and `props`

- When you want to communicate from Parent > Child component and pass things through the tree, use `props`.
- When you want to store a piece of information about the component (ie.. record keeping), use `state`.

## Fetching data

The tutorial on Udemy showed most of the `fetch` code in the `componentWillMount()` method. There are some that believe (myself included) that it's better to fetch the data once the component actually renders in the `componentDidMount()` method. This reminds you to always setup an initial state to avoid errors. 


Copied from https://daveceddia.com/where-fetch-data-componentwillmount-vs-componentdidmount/
> In practice, `componentDidMount` is the best place to put calls to fetch data, for two reasons:

> Using DidMount makes it clear that data won’t be loaded until after the initial render. This reminds you to set up initial state properly, so you don’t end up with undefined state that causes errors.

> If you ever need to render your app on the server (SSR/isomorphic/other buzzwords), componentWillMount will actually be called twice – once on the server, and again on the client – which is probably not what you want. Putting the data loading code in componentDidMount will ensure that data is only fetched from the client.

## Redux

Redux notes. Redux has alot of fancy terminology that obscures straightforward concepts. The key is to mastering the terminology to make it easy.

***ONE OF THE BEST LIBRARIES IN EXISTNECE FOR SCALING AN APPLICATION TO BE VERY LARGE WITH THE LEAST AMOUNT OF CODE COMPLEXITY***
This is due to the `action` system. This allows us to make predicatable changes. We never have to access the `state` (store) directly. We use an `action`. 
Actions modify the `state` in a very particular way. We can only modify the `state` in a very finite number of ways.

Reducer - a function that returns some amount of state.

Action - an object that tells the reducer how to change it's data. ***MUST HAVE TYPE property***

State - data for our app to use. everything from value of input fields to whether or not auth user, to list of data, to series of picture, etc..

Store - an object that holds the applications data. holds the reducers and application state


Example.......
````
      Action         ->           Reducer               ->       State

turn 'asdf' into an  ->  if the actions type is 'split' ->  ['a','s','d','f']
array of characters      i will take a string of chars
                         and turn it into an array

Action - contains 2 things, a string of characters, and a direction/command that syas I want this to be split up into characters

Reducer - looks at action and says AHHA, this action is commanding me to split up these characters into single characters. It will split it into a list of characters and return it

State - Because the reducer returned those characters, the state will now contain that array.
````

````JavaScript
// reducer is a fat arrow function that returns an array. produces some amount of state.
const reducer = (state = [], action) => {
  if (action.type === 'split_string') {
    return action.payload.split('');
  }
  
  return state;
};

// sets up the Redux store
const store = Redux.createStore(reducer);

// plain javascript object that will always include a 'type' property with a string as it's value (REQUIREMENT).
// this tells the reducer what operation to perform. the 'payload' property tells what the action will be performed on.
const action = {
  type: 'split_string',
  payload: 'asdf',
};

// returns an empty state array
store.getState();

// sends the action to the reducer
store.dispatch(action);

store.getState();

const action2 = {
  type: 'add_character';
  payload: 'a',
};

store.dispatch(action2);
````
At any time you can call `store.getState();` to get an array of the entire contents of the store.

Nothing happens when you create an `action`. It has to be passed to the `dispatch()` method to update the `store`.

## Images

When we use an image in React Native, it WILL NOT expand to fill the container (like HTML). You must specify a height and width.


## Authentication 

This section is setup for various examples of authentication.

### Firebase Authentication

After creating a Firebase account, there are options for iOS, Android, and WebApp. 

Example for logging in with `signInWithEmailAndPassword()`
````JavaScript
onButtonPress() {
  firebase.auth().signInWithEmailAndPassword(email, password)
    //Beacuse this is a function we are passing off to a promise, that is going to be invoked at some time in the future,  
    // and we don't know the context, we have to bind the method to this.
    .then(this.onLoginSuccess.bind(this))
    .catch(() => { 
      firebase.auth().createUserWithEmailAndPassword(email, password)
      .then(this.onLoginSuccess.bind(this))
      .catch(this.onLoginFailed.bind(this));
  }); 
}
````

```JavaScript
firebase.auth().onAuthStateChanged(function(user) {
  if (user) {
    // User is signed in.
  }
});
````

## Input

`<TextInput/>` does not have a standard width and height. If there is none supplied, the component won't render.



## Debbuging

(mac) command + d  > Debug JS Remotely

Browser page opens, right-click > Open DevTools > console tab

