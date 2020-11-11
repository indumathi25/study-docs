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

Reducers are pure functions that take (previousState, action) as input and return newState. Reducers instead of upating the previousState should return a newState.



 



