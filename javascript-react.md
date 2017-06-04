# REACT NOTES

This is a collection of notes I'm keeping on the Javascript React framework as I learn it. I will try and include sources as I use them for the notes. It's inteded to be used as a cheatsheet to get a React app up and running quickly. It serves to remind me what certain things do, what the concepts/ideas of each section are, and maybe some example code usage.

If you find it useful, star it and enjoy it.


## Table of Contents
1. APP SETUP
2. Components
3. Render / Export
4. Props
5. State
6. Navigation / Routing
7. Utils / Helpers
8. Database
9. Redux
10. Immutable 
TERMINOLOGY


## 1. APP SETUP

FOLDER STRUCTURE -- You can use the "create-react-app" package as a boilerplate. The great mind of Dan Abramov (facebook) decided to give us a pre-built "app" template to cut down on development time. (https://github.com/facebookincubator/create-react-app)

"node_modules" - where npm modules are installed on the project (if not global)

"src" - folder where application source code goes. 

"public" - folder where the public facing part of the site goes. Like your HTML and image files.

"package.json" - holds the npm dependencies and specifies app properties. This includes app information, build scripts, and npm packages.

"README.md" - standard markdown file that is included with every project. the "create-react-app" specific readme has links to various resources and documentation.

"yarn.lock" - yarn lock file.



```Javascript
USAGE: npm install create-react-app
```

## 2. Components

Components need to be imported into the App.js file to be utilized (lazy loading?)

`<View>` - A view component is good to use as a container for other components to help control style and layout.

Each Component has it's own `state` object

## 3. Render / return / Export

The render() function is the only "requirement" of the react component. Scope happens within the render() function. The return() function allows rendering of JSX.

```Javascript
class ClassName extends Component {
  render() {
    return (
      <Text>Hello, World!</Text>
    );
  }
}

The `constructor(props)` section of a Component is essentially the initial `state`. 

The `super(props)` line passes the `props` to the constructor and allows them to be used in the `state`.

```Javascript
class ClassName extends Component {
  
  constructor(props) {
    super(props);
    this.state = {date: new Date()};
  }

  render() {
    return (
      <Text>Hello, World!</Text>
    );
  }
}
```
constructor 

## 4. Props

Props are equivalent to arguments (args). They are considered properties that are assigned values by the parent, and and are fixed throughout the lifetime of the component.

eg.

```Javascript
const HelloWorld = (props) => { } 
```

eg. within a Component
```Javascript
<Text prop={args}></Text>
```

## 5. State

State is usually initialized in the constructor() and then changed by calling setState(). It is set just before the `render(){}` method.

```Javascript
// Sets initial State
constructor(props) {
  super(props);
  this.state = {
    searchString: 'london'
  };
}

render () { 
	return (
	
	);
}
```

After the state has been initiated, you need to do something with it. 

The first step is to create a method that acts as an event handler.

```Javascript
// Creates the onSearchTextChanged method on event
onSearchTextChanged(event) {
  console.log('onSearchTextChanged');
  this.setState({ searchString: event.nativeEvent.text });
  console.log(this.state.searchString);
}
```

The next step is to bind the method to a javascript method (eg.. onChange) that will be listening for an event.

```Javascript
<TextInput
  style={styles.searchInput}
  value={this.state.searchString}
  onChange={this.onSearchTextChanged.bind(this)}
  placeholder='Search via name or postcode'/>
```

State is changed as a separate step of a method. When a method is called, you also place a line for changing the state.

```Javascript
// this.setState is added to the method to change the state when the query isLoading.
_executeQuery(query) {
  console.log(query);
  this.setState({ isLoading: true });
}
 
onSearchPressed() {
  var query = urlForQueryAndPage('place_name', this.state.searchString, 1);
  this._executeQuery(query);
}
```

## 6. Navigation / Routing



## 7. UTILS / HELPERS



## 8. Database Solutions



## 9. Redux



## 10. ImmutableJS



## RESOURCES

"Aha Moments" by Tyler McGinnis (@TylerMcGinnis) -- https://tylermcginnis.com/react-aha-moments/ 

"Learning React with 'create-react-app' npm package" by Brandon Richey -- https://medium.com/@diamondgfx/learning-react-with-create-react-app-part-1-a12e1833fdc

"React Native Tutorial" by Ray Wenderlich -- https://www.raywenderlich.com/126063/react-native-tutorial

## TERMINOLOGY

Abstractions - 

