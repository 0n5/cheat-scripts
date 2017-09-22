Redux Basics
============

Redux is a predictable state container for JS
Redux represents the data, react represents the view


State

* Redux centralizes all of the app data into a single object called state


ActionCreators

* Function that returns an action (object)
* Reducers have access to all of actions and can use them via a switch


Reducers

* function that returns a piece of the application state
* smart components or containers have a direct connection to redux
* containers are the link between react and redux

mapStateToProps

* takes in application state and retuns props for the container
* connect() returns the container from mapStateToProps and the component 

mapDispatchToProps

* anything return by this function will be available as props on the container


bindActionCreators

* makes sure that the action created by action creator flows thru the reducers using dispatch

Controlled Component

* Accepts its current value as props and has a callback that can change the value
* Uses a constructor function in the component 
* Every state mutation will have an associated handler function 

#### App Structure 

    App Folder/
      node modules/
      src/
        actions/
          index.js
        components/
          app.js
        containers/
          some_container.js
          other_container.js
        reducers/
          index.js
          some_reducer.js
          other_reducer.js
        index.js
      .babelrc
      index.html
      package.json
      webpack.config.js
