React Basics
============

Declarative programming paradigm

Follow Functional programming best practices

* Keep data immutable
* Keep functions pure
* Use recursion over loops

How React works

* React library creates the views
* ReactDOM library renders the UI in the browser
* React uses a Virtual DOM which is made up of React elements / JS objects.
* React elements are instructions for how the browser's DOM should be created
* Components take props (properties) as input and output a rendered UI of the component
* Components should be seperated into their own files so they can be reused

JSX

* Provides a syntax for creating DOM trees with attributes
* Values can be sent to Components as properties thru JS expressions (curly braces)
* The expressions can be functions, arrays or objects
* Everything inside of the curly braces will get evaulated
* JSX Allows for nested components

Babel

* Transpiles JSX, ES6 and ES7 into code the browser can understand
* Requires specific presets to do transformations
* Converts ES6 imports statements into require('')

WebPack

* Module bundler that takes static files and makes single file (bundle.js)
* Performance is enhanged by needing to load only one dependency
* Performs chunking (rollups, layers) and minification
* Hot Module Replacement watches for code changes on the fly
* [List of loaders](https://webpack.js.org/concepts/loaders/)

data-react-root

* will always appear as an attribute of the root element when rendered
* All other react elements are children of the root
* React renders children elements using `props.children` array

ReactDOM

* containers render, renderToString and renderToStaticMarkup methods
* erasing and rebuilding DOM is most costly of operations
* ReactDOM.render leaves current DOM alone updates only elements needed to update


className

* defines a class attribute of an HTML element, since class is a reserved word

Properties

* Pass data to React components

Factories

* React has built in factories for all common HTML elements
* `React.DOM.li(null, "Cat")` is a built in factory for `li`
* React.createFactory allows you to create your own factories
* Commonly used when not using JSX, otherwise not. 

PropTypes

* Built in property variable validation

state

* Data structure that holds the model which is mutable
* A change in state is the only thing that can change a rendered view
* Whenever state changes it triggers a rerender of the component and view.
* State should never be modified directly

setState()

* Lets React know when state has changed
* Takes in an object, top level props are merged into the existing state
* Props are accessible in the component using `this.state`
* State is initialized in the constructor

componentDidMount()

* Lifecycle method that indicates that React is ready to accept setState() calls
* Called after the Component is mounted into the DOM

One way data flow

* Sibling components cannot communicate with each other, information has to go up the tree and back down
* Communication between children and parents is acheived thru callback functions

Stateless components

* Most components should be stateless functions of their properties

Asynchronous API calls

* Use Axios or Fetch