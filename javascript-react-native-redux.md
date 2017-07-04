# React Native & Redux

Notes on React Native and Redux

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

Add eslint config "rallycoding" to the project

`yarn add eslint-config-rallycoding`

Add `.eslintrc` file


## Application Setup

3 Steps to creating components

1. Import libraries
2. Make Component
3. Make Component available to other parts of app

```Javascript
// Import Libraries
import { React } from 'react';
import { AppRegistry } from 'react-native';

// Creates the main component
const App = () => {
  return (
      <Text>Hello World!</Text>
  )
};

// Render to the device
AppRegistry.registerComponent('projectname', () => App);
```

## Props

When we want to pass variables from parent component to child component we use `props`

Passing props to the interface is a core component of React and React Native. Props make component resuability possible.

## Components

Functional vs. Class-Based

Functional -- garden hose/pipe (one way). Data in, JSX out.

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

### State

`state` - a plane javascript object used to record, and respond to user-triggered events.

When we need to change what a component shows, call `this.setState()`

`this.setState()` is automatically implemented via the `Component` class. The purpose of `this.setState()` is to update our component state and say "Hey, here's some new data, we need to re-render the component with the new data".

```JavaScript
this.setState({ albums : data.response }); // Good - Update the albums object with the data from the request

this.state = {}; // Good - only use this.state = {} when setting initial state.

this.state = { albums : data.response }; // BAD - don't do. 
```

DIFFERENCE BETWEEN `state` and `props`

- Want to communicate from Parent > Child component, use PROPS.
- State is for a components internal record keeping.

### Fetching data

//Copied from https://daveceddia.com/where-fetch-data-componentwillmount-vs-componentdidmount/
In practice, `componentDidMount` is the best place to put calls to fetch data, for two reasons:

Using DidMount makes it clear that data won’t be loaded until after the initial render. This reminds you to set up initial state properly, so you don’t end up with undefined state that causes errors.

If you ever need to render your app on the server (SSR/isomorphic/other buzzwords), componentWillMount will actually be called twice – once on the server, and again on the client – which is probably not what you want. Putting the data loading code in componentDidMount will ensure that data is only fetched from the client.

## Debbuging

(mac) command + d  > Debug JS Remotely

Browser page opens, right-click > Open DevTools > console tab

