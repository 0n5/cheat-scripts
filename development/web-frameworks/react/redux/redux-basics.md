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


React / Redux Workflow

1. Create reducer function to create state
2. Create root reducer that imports reducer functions, combines them and maps state objects
3. Create class based component that uses the state created in the reducer
4. Component will map over the array of props sent in from the 
5. Create mapStateToProps that takes the state and returns as props in the container (this.props)
6. 







