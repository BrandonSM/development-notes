# Redux

Redux notes. Redux has alot of fancy terminology that obscures straightforward concepts. The key is to mastering the terminology to make it easy.

***ONE OF THE BEST LIBRARIES IN EXISTENCE FOR SCALING AN APPLICATION TO BE VERY LARGE WITH THE LEAST AMOUNT OF CODE COMPLEXITY***
This is due to the `action` system. This allows us to make predicatable changes. We never have to access the `state` (store) directly. We use an `action`. 
Actions modify the `state` in a very particular way. We can only modify the `state` in a very finite number of ways.

Reducer - a function that returns some amount of state.

Action - an object that tells the reducer how to change it's data. ***MUST HAVE TYPE property***

State - data for our app to use. everything from value of input fields to whether or not auth user, to list of data, to series of picture, etc..

Store - an object that holds the applications data. holds the reducers and application state


Example.......
````
      Action         ->           Reducer               ->     State/Store
s
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

// sets up the Redux store - A store is an object that holds our application's state and reducers
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

`dispatch()` sends to the off to the `reducer`, the reducer re-runs, and whatever it returns becomes the state inside of the store.

***One big rule of reducers***
Whenever you change the state object in the reducers, we MUST return a completely new array (or datastructure). 
WE DO NOT MUTATE THE DATA. We create a completely new one.
GOLDEN RULE - Always return a new array with reducers.

## Setup

To add it to a project, run `yarn add redux react-redux` or `npm install --save redux react-redux`

Below is an example of the minimum of Redux you could use to add to an application.

````JavaScript
// src/reducers/index.js
import { combineReducers } from 'redux'; // makes reducers play nice together

export default combineReducers ({
  libraries: () => [

  ]
});
````

````JavaScript
import React from 'react';
import { View, Text } from 'react-native';
import { Provider } from 'react-redux';
import { createStore } from 'redux'; 
import reducers from './reducers';

const App = () => {
  return (
    <Provider store={createStore(reducers)}>
      <View/>
    </Provider>
  );
};

export default App;
````

## Provider

The `<Provider></Provider>` tag works together with the store. each has a speific job. store holds data state1, state2, state3 ... The provider transforms that data into something that can be used with React.

The `<Provider/>` component can only have 1 child component or you will get an error message mentioning the React component can only have 1 child

The following example results in an error...
````JavaScript
<Provider store={createStore(reducers)}>
  <Header />
  <View/>
  <Footer />
</Provider>
````

The following example is OK
````JavaScript
<Provider store={createStore(reducers)}>
  <View>
    <Header />
    <AnotherComponent />
    <Footer />
  </View>
</Provider>
````

## Reducer

Reducer design - The process of deciding what `reducer`s will exist in the application.

What different variables? What are the different pieces of `state`? The different pieces of data.


## Connect helper

Tool that is used explicitly to `connect()` a component to the redux store.

There is one and only one way to reach into the store (data) and that is with the `connect()` helper.
