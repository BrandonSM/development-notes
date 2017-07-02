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


## Components

3 Steps to creating components

1.) Import libraries
2.) Make Component
3.) Make Component available to other parts of app


```Javascript
// Creates the main component
const App = () => {
  return(
      <Header />
    )
};
```