REDUX:
========

Redux is a predictable state container for Javascript apps

> Redux is not tied to React
> Can be used with React, Angular, Vue or even vanilla javascript.

> Redux is a library for Javascript applications.
> Redux stores the state of your application.

> State of an app is the state represented by all the individual components of the app. This includes the data and UI logic.
```
Ex:
UserListComponent:
state = {
    users: [];
}
```
> Redux will store and manage this application state.

> Redux is a state container. The state of the application can change. In redux, all state transactions are explicit and it is possible to keep track of them. 
> Changes to your application's state become predictable.

> Manage the state of your application in a predictable way, redux can help you.

> In Redux state is contained outside the components -> Redux state container

React context - prevents props drilling.
useContext + useReducer -> can do same as Redux

Redux 1.0 - August 2015 when these above 2 are not available. But there is no 100% replacement for Redux.

React Redux:
-----------
React -> UI library
Redux -> State management library

To use Redux with React we make use of React-Redux library
> React-Redux is the official Redux UI binding library for React.


Getting started with Redux:
---------------------------
```
> mkdir redux-demo

> npm init --yes
Initialize the package with pacakage.json

>npm install redux

> create index.js
> node index -> to run the js file.
```
3 Core concepts in Redux:
=========================

3 principles descibes the Redux pattren.

```
Cake shop Scenario	    Redux	  Purpose
Shop	                    Store	  Holds the state of your application
Intention to BUY_CAKE	    Action	  Describes what happened? I.e Describes the changes in the state of the application.
Shopkeeper	            Reducer       Ties the store and action together.

```
> Reducer which actually carries out the state transition depending on the action.


First principle:
The state of your whole application is stored in an object tree within a single store.
Maintain our application state in a single object which would be managed by the Redux store.

Second principle:
Only way to change the state is to emit an action, an object describing what happened. 
To update the state of your application, you need to let Redux know about that with an action. You are not allowed to directly update the state object. ex: BUY_CAKE

Third principle:
To specify how the state is trnasformed by actions, you write pure reducers.

    Reducer - (previousState, action) => newState

Reducers are pure functions that take (previousState, action) as input and return newState. Reducers instead of upating the previousState should return a newState. ex: Shopkeeper is a reducer.

```
const cakeReducer = (state = initialCakeState, action) => {
   switch(action.type){
       case 'BUY_CAKE' : return {
         ...state,
         numOfCakes: state.numOfCakes - 1
       }
       default: return state;
   }
}
```

ACTION:
------
The only way your application can interact with the store.

Carry some information from your app to Redux store.

Action is a plain javascript objects with a 'type' property that indicates the type of action being performed.

Action creator is a function that returns an action.

```
const BUY_CAKE = 'BUY_CAKE'

function buyCake(){
    return {
        type: BUY_CAKE,
        info: 'First redux action'
    }
}
```
REDUCERS:
——————
Function that accepts the state and action as arguments and return the next state of the application.
```
const initialCakeState = {
    numOfCakes: 10
}

const cakeReducer = (state = initialCakeState, action) => {
   switch(action.type){
       case 'BUY_CAKE' : return {
         ...state,
         numOfCakes: state.numOfCakes - 1
       }
       default: return state;
   }
}
```
> First make a copy of the state object and then only update the 'numOfCakes'. If there where other properties they remain unchange.


REDUX STORE:
------------
One store for the entire appliation.
Responsibilities:
1.Holds application state.
2.Allows access to state via getState()
3.Allows state to be updated via dispatch(action)
4.Registers listeners via subscribe(listeners)
5.Handles unregistering of listeners via the function returned by subscibe(listerners)

Subscribe method accepts a function as a parameter which is executed any time the state and the redux store changes.
```
const redux = require('redux')
const createStore = redux.createStore

const store = createStore(cakeReducer)
console.log('Initial State : ', store.getState());

const unsubscribe =  store.subscribe(() => { console.log(store.getState()) })
store.dispatch(buyCake())

unsubscribe()
```
Middleware:
-----------

Is the suggested way to extend Redux with custom functionality. 
Provides a third-party extension point between dispatching an action, and the moment it reaches the reducer.
Use middleware for logging, crash reporting, performing asynchronous tasks etc.
```
npm install redux-logger

const reduxLogger = require('redux-logger')

const logger = reduxLogger.createLogger()

const store = createStore(rootReducer, applyMiddleware(logger))
```
Example of cake and icecream with combined reducers:
-----------------------------------------------------
```
const redux = require('redux')
const reduxLogger = require('redux-logger')

const createStore = redux.createStore
const logger = reduxLogger.createLogger()
const combineReducers = redux.combineReducers
const applyMiddleware = redux.applyMiddleware

const BUY_CAKE = 'BUY_CAKE'
const BUY_ICE_CREAM = 'BUY_ICE_CREAM'

function buyCake(){
    return {
        type: BUY_CAKE,
        info: 'First redux action'
    }
}

function buyIceCream(){
    return {
        type: BUY_ICE_CREAM,
        info: 'Second redux action'
    }
}

const initialCakeState = {
    numOfCakes: 10
}

const initialIceCreamsState = {
    numOfIceCreams: 20
}

const cakeReducer = (state = initialCakeState, action) => {
   switch(action.type){
       case 'BUY_CAKE' : return {
         ...state,
         numOfCakes: state.numOfCakes - 1
       }
       default: return state;
   }
}

const iceCreamReducer = (state = initialIceCreamsState, action) => {
    switch(action.type){
        case 'BUY_ICE_CREAM' : return {
         ...state,
         numOfIceCreams: state.numOfIceCreams - 1
       }
        default: return state;
    }
}

const rootReducer = combineReducers({
    cake: cakeReducer,
    iceCream: iceCreamReducer
})
const store = createStore(rootReducer, applyMiddleware(logger))
console.log('Initial state', store.getState())

const unsubscribe = store.subscribe(() => { })
store.dispatch(buyCake())
store.dispatch(buyCake())
store.dispatch(buyCake())

store.dispatch(buyIceCream())
store.dispatch(buyIceCream())

unsubscribe()

```

Actions:
========
Synchronous Actions: As soon as an action was dispatched, the state will be updated immediately.

Async Actions: Asynchronous API calls to fetch data from an end point and use that data in your application.

Async Action creators: 

axios: Requests to an API end point.

redux-thunk: Define async action creators. Is a middleware applying to the Redux store.
```
npm install axios redux-thunk

const thunkMiddleware = require('redux-thunk').default
const axios = require('axios')

const applyMiddleware = redux.applyMiddleware

const store = createStore(reducer, applyMiddleware(thunkMiddleware))
```

> thunkMiddleware -> allows the action creator to return a function instead of an action. 
>Function now performs side effects such as async tasks. 
>Function can also dispatch regular actions which will be handled by reducer.

Example for Async:
-----------------
```
const redux = require('redux')
const thunkMiddleware = require('redux-thunk').default
const axios = require('axios')

const createStore = redux.createStore
const applyMiddleware = redux.applyMiddleware

const initialStae = {
    loading: false,
    users: [],
    error: ''
}

const FETCH_USERS_REQUEST = 'FETCH_USERS_REQUEST'
const FETCH_USERS_SUCCESS = 'FETCH_USERS_SUCCESS'
const FETCH_USERS_FAILURE = 'FETCH_USERS_FAILURE'

const fetchUsersRequest = () => {
    return {
        type: FETCH_USERS_REQUEST
    }
}

const fetchUsersSuccess = users => {
    return {
        type: FETCH_USERS_SUCCESS,
        payload: users
    }
}

const fetchUsersFailure = error => {
    return {
        type: FETCH_USERS_FAILURE,
        payload: error
    }
}

const reducer = (state = initialStae, action) => {
    switch(action.type){
        case FETCH_USERS_REQUEST:
            return{
                ...state,
                loading: true,
            }
        case FETCH_USERS_SUCCESS:
            return{
                ...state,
                loading: false,
                users: action.payload,
                error: ''
            }
        case FETCH_USERS_FAILURE:
            return{
                ...state,
                loading: false,
                users: [],
                error: action.payload
            }

    }
}

const fetchUsers = () => {
    return function(dispatch) {
        dispatch(fetchUsersRequest())
        axios.get('https://jsonplaceholder.typicode.com/users')
        .then(response => {
            const users = response.data.map(user => user.id);
            dispatch(fetchUsersSuccess(users))
        }).catch(error => {
            dispatch(fetchUsersFailure(error.message))
        })
    }
}
const store = createStore(reducer, applyMiddleware(thunkMiddleware))
store.subscribe(() => { console.log(store.getState()) })
store.dispatch(fetchUsers())

```


 



